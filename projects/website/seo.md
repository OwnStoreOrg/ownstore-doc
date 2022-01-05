---
label: SEO
title: Website SEO
icon: codescan-checkmark
order: 2
---

App is very well optimized with industry-standard SEO practices. There are 2 layers for SEO:
- AppSeo
- Page-level SEO

## App SEO
App SEO is basically the global file for everything related to SEO. Can be found in `app/components/seo/AppSeo.tsx`. This file contains
- global values
- incoming page-level values

## Page-level SEO
Now each page can have few SEO entires that can be dynamic. For eg. title of a page can be dynamic. 

Each page has a method to prepare page-level SEO data. Can be found in `app/utils/seo`. Let's take home page as an example...

If you goto `app/utils/seo/home.ts`, you will find a method returning few entries.

```ts
// http://localhost:3000/
export const prepareHomePageSeo = (): IAppSeoProps => {
  return {
    title: 'Home',
    description: 'Home',
    canonical: `${appConfig.global.baseUrl}${getHomePageUrl()}`,
    keywords: [''],
  }
}
```

Now these entries will be passed on to `AppSeo.tsx`, that component will create a final SEO package and dump at the head of the page. 

What else can a page SEO method return?
```ts
title: string
description: string
canonical: string
keywords: string[]
noIndex?: boolean
noFollow?: boolean
openGraph?: {
  title?: string
  description?: string
}
twitter?: {
  card?: 'summary' | 'summary_large_image'
  title?: string
  description?: string
}
imageUrl?: string
structuredData?: {
  breadcrumbList?: { [key: string]: any }
  FAQs?: { [key: string]: any }
  product?: { [key: string]: any }
}
```

Let's understand what these keys mean

Key | Description
--- | ---
`title` | Title of the page
`description` | Page description
`canonical` | Page's canonical URL. Should be absolute.
`keywords` | A list of keywords for the page.
`noIndex` | Should the page be indexed? If no, set this to true.
`noFollow` | Should the page be followed? If no, set this to true.
`openGraph` | This is to control page's meta information for OpenGraph/Facebook. For eg. you might want page `title` to be different when link is previewed.
`openGraph.title` | Title for OpenGraph.
`openGraph.description` | Description for OpenGraph.
`twitter` | This is to control page's meta information for Twitter. For eg. you might want page `title` to be different when link is previewed.
`twitter.card` | Should the card be of default size or large? Possible values: `'summary' | 'summary_large_image'`
`twitter.title` | Title for Twitter.
`twitter.description` | Description for Twitter.
`imageUrl` | A page can also have a image URL. For eg. on product page. Should be absolute.
`structuredData` | By default, each page will have the following structured data: <ul><li>organization - [Reference](https://schema.org/Organization)</li><li>webSite - [Reference](https://schema.org/WebSite)</li><li>webPage - [Reference](https://schema.org/WebPage)</li></ul>
`structuredData.breadcrumbList` | For eg. on individual catalogue page, you might need to show the catalogue index page. [Reference](https://developers.google.com/search/docs/advanced/structured-data/breadcrumb)
`structuredData.FAQs` | Added on FAQ page. [Reference](https://developers.google.com/search/docs/advanced/structured-data/faqpage)
`structuredData.product` | Added for product pages. [Reference](https://developers.google.com/search/docs/advanced/structured-data/product)

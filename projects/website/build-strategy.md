---
label: Build Strategy
title: Website Build Strategy
icon: container
order: -2
---

Since we use NextJs as a framework, we have used 3 build strategies here depending upon the use-case. Used strategies:
- SSG (Static Generation)
- CSR (Client-side Rendering)
- SSR (Server-side Rendering)

Kindly go through this article to [learn more](https://vercel.com/blog/nextjs-server-side-rendering-vs-static-generation) in detail.

## SSG
This strategy enables us to build a dynamic page initially and update its content after an interval. This is much faster, widely adopted and optimized than other strategies. For eg. for a product page...

There can be 1000+ products, so we will build 50 product pages initially and if user visits a page that is not built, NextJs will build the page on the fly, serve that page and update the build mapping so the next time you visit, you'll see a static page with no server lookup. 

Also we can define when an SSG page should be re-validated.

## CSR
Initially a skeleton is served and once the page has finished loading, you will fetch the data and show a corresponding UI. CSR pages:
- Account pages

## SSR
This will build the page everytime you visit. SSR pages
- Search results page

---
label: FAQs
title: Website FAQs
icon: question
order: -3
---

## Which social icons are supported?
```ts
[
  APPLE,
  ANDROID,
  ALIBABA,
  AMAZON,
  EMAIL,
  APPSTORE,
  BLOGGER,
  DISCORD,
  DRIVE,
  EBAY,
  FACEBOOK,
  GITHUB,
  GITLAB,
  MAIL,
  GOOGLE,
  GOOGLE_PLAY,
  INSTAGRAM,
  ITUNES,
  LINKEDIN,
  MEDIUM,
  PAYPAL,
  PHONE,
  PHOTOS,
  PINTEREST,
  QUORA,
  REDDIT,
  RSS,
  SINA_WEIBO,
  SLACK,
  SNAPCHAT,
  SPOTIFY,
  TELEGRAM,
  TIKTOK,
  TUMBLR,
  TWITCH,
  TWITTER,
  VIMEO,
  WECHAT,
  WHATSAPP,
  WIKIPEDIA,
  YELP,
  YOUTUBE,
  GLOBE,
  PWA,
  FORM,
  REFRESH,
]
```

## Which icon library is used?
[Heroicons](https://heroicons.com/) is used.

## How can we check debug logs?
We have added grouped logging using [debug](https://www.npmjs.com/package/debug) library. Let's take an example...

To check `http` logs
```ts http/httpClient.ts
const log = debug('http')
```

- On CLI:
Use `DEBUG` environment variable. For eg.
```bash
DEBUG='http' npm run start:local
```

- On Browser:
Use `localStorage.debug` to control. For eg.
```js
localStorage.debug = 'http'
```

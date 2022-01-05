---
label: FAQs
title: API FAQs
icon: question
order: -1
---

## Which additional headers are supported?
Apart from the standard HTTP headers, we accept a few more

This mapping can be found in `src/app/constants/index.ts`

```ts
export const VALID_EXTERNAL_HEADERS = {
  ACCESS_TOKEN: 'x-access-token',
  ADMIN_ACCESS_TOKEN: 'x-admin-access-token',
  SENTRY_TRACE: 'sentry-trace',
  RESPONSE_CACHE_TIME: `${appConfig.global.app.key.toLowerCase()}-cache-time`,
}
```

## Which origins are supported?

This list can be found in `src/appConfig.ts`.

```ts
[
  'http://localhost:3000', // website local
  'http://localhost:3002', // cms local
  'https://own-store-demo.vercel.app', // website prod
  'https://own-store-demo-cms.vercel.app', // cms prod
]
```

## What are the supported cache TTLs?

We have caching at 2 layers:
- service
- controller

Service-level cache time should be 80% of controller's

```ts
export const CACHE_MULTIPLIER = 0.8

// Ideally service-level cache time should be 80% of controller's
// in seconds
export const SERVICE_CACHE_TTL = {
  LIVE: 30 * CACHE_MULTIPLIER,
  SHORT: 2 * 60 * CACHE_MULTIPLIER,
  DEFAULT: 5 * 60 * CACHE_MULTIPLIER,
  LONG: 10 * 60 * CACHE_MULTIPLIER,
}

// in seconds
export const CONTROLLER_CACHE_TTL = {
  LIVE: 30,
  SHORT: 2 * 60,
  DEFAULT: 5 * 60,
  LONG: 10 * 60,
}
```

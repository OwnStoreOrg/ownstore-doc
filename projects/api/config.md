---
label: Config
title: API Config and ENVs
icon: note
order: 2
---

Before deep-diving into the app config, let's first through the ENVs.

## ENV
This project has multiple environments and can be found under `/env` directory. These envs help us to develop, test and deploy. Currently, we have only 2:
- `local` - For development
- `production` - For production

An ENV file contains values which you need to be different on different environments. For eg. You need a local DB connection while developing, but a prod connection for online users.

## Config
App config can be found in `src/appConfig.ts` file.

### config.global
Key | Description
--- | ---
`global.app` | Few app related information.
`global.domain` | Domain. For eg. `your-store-api.herokuapp.com` OR `localhost:3000`
`global.baseUrl` | Base URL. For eg. `https://your-store-api.herokuapp.com` or `http://localhost:3000`
`global.clientOrigins` | A list of origins where API will be used. This is for security. Check the supported origins [here](http://localhost:3003/projects/api/faq/#which-origins-are-supported)
`global.pageSectionItemsLimit` | A number to limit the count of items fetched for a section. For eg. If 15, then only 15 products will be returned for the `Products` section.
`global.showDoc` | Control if you want to show swagger API doc.

### config.admin 
Key | Description
--- | ---
`admin.email` | Email of the admin. Used as a support email for swagger doc.
`admin.cacheClearKey` | This key will be used when an admin tries to clear the redis cache. The operation will be validated against this key. **Very private** 
`admin.auth.key` | This key will be used to validate an admin from CMS. **Very private**
`admin.auth.tokenSecret` | To prepare a unique and safe admin token with `admin.auth.key` for the CMS, a secret key is needed. **Very private**
`admin.auth.tokenExpiry` | This controls how long the admin should stay logged in. 

### config.errors 
Key | Description
--- | ---
`errors.report4xxErrors` | Set this to true if you want to report 4xx errors to Sentry.

### config.userAuth
Key | Description
--- | ---
`userAuth.tokenSecret` | To prepare a unique and safe user token for users, a secret key is needed. **Very private**
`userAuth.tokenExpiry.default` | This controls how long the user should stay logged in. 
`userAuth.tokenExpiry.extended` | This controls how long the user should stay logged in if they opt-in to `Remember me`. 

### config.order
Key | Description
--- | ---
`order.status` | There's a dependency in code for 2 order statuses: `RECEIVED` & `CANCELLED`. Map these statuses with correct DB ID here.
`order.cancellationReasons` | This is a list of pre-defined reasons shown to users when they cancel the order.

### config.payment
Key | Description
--- | ---
`payment.refundAmountPercent` | The amount in percentage of order total to refund.
`payment.tax` | Total tax on cart total. First priority is given to `percent`. If null, considers 'flat' key.
`payment.tax.percent` | Tax amount in percentage
`payment.tax.flat` | Tax amount in flat number
`payment.tax.decimalPrecision` | This controls the number of decimals after calculation of tax. For eg. 17.23491 => 17.23
`payment.extraCharges` | Total extra charges on cart total. First priority is given to `percent`. If null, considers 'flat' key.
`payment.extraCharges.percent` | Extra charge amount in percentage
`payment.extraCharges.flat` | Extra charge amount in flat number
`payment.extraCharges.decimalPrecision` | This controls the number of decimals after calculation of tax. For eg. 17.23491 => 17.23
`payment.smallestCurrencyUnit` | Smallest currency unit to form 1 amount. For eg. 1 dollar = 100 cents, 1 rupee = 100 paisa. Used by Stripe to process payments. 
`payment.deliveryPriceMapping` | A mapping of [whenAmountAbove]: [deliveryPrice]. Should be in ascending order of whenAmountAbove.

### config.database
Key | Description
--- | ---
`database.url` | DB connection URL. If provided, other credentials such host, password, etc.. will be ignored.
`database.host` | DB host for connection
`database.post` | DB post for connection
`database.name` | DB name for connection
`database.user` | DB user for connection
`database.password` | DB password for connection
`database.enableLogging` | If set to true, `TypeORM` logging will be enabled.
`database.enableSync` | If set to true, any changes in models will be reflected in DB on save. Also if a table is not present in DB but present as a model, TypeORM will create one table. So DB and its tables are eligible for auto sync.

### config.cache
Key | Description
--- | ---
`cache.redis` | Redis is used to cache data at service method level. This is done offload DB operations.
`cache.redis.enabled` | To disable redis cache, set it to `false`
`cache.redis.mode` | Redis mode (`standalone` / `cluster`). [Redis connection reference](https://github.com/luin/ioredis/blob/HEAD/API.md#Redis)
`cache.redis.url` | Redis connection URL. IF provided, other credentials will be ignored. [Redis connection reference](https://github.com/luin/ioredis/blob/HEAD/API.md#Redis)
`cache.redis.host` | [Redis connection reference](https://github.com/luin/ioredis/blob/HEAD/API.md#Redis) 
`cache.redis.port` | [Redis connection reference](https://github.com/luin/ioredis/blob/HEAD/API.md#Redis)
`cache.redis.dbIndex` | [Redis connection reference](https://github.com/luin/ioredis/blob/HEAD/API.md#Redis)
`cache.redis.password` | [Redis connection reference](https://github.com/luin/ioredis/blob/HEAD/API.md#Redis)
`cache.redis.keyPrefix` | Used as a prefix for all Redis cache keys. 
`cache.redis.maxTtl` | How long the cache should be kept at max.
`cache.httpResponse` | We have caching at HTTP response level too.
`cache.httpResponse.enabled` | To disable HTTP response cache, set it to `false`

### config.allow

There are 2 ways you can disable:
- directly from project ENV files by setting the value as `false`
- or expose these ENV variables separately and keep values here as blank. You can avoid a build with this approach and change will be applied immediately.

Key | Description
--- | ---
`allow.newRegisterations` | Allow new registerations.
`allow.newOrders` | Allow new orders.

### config.integrations
Key | Description
--- | ---
`integrations.stripePayment` | Stripe is used to process payments
`integrations.stripePayment.secretKey` | Get secret key from Stripe dashboard
`integrations.sentryErrorReporting` | Sentry is used to monitor app health
`integrations.sentryErrorReporting.enabled` | To disable this integration
`integrations.sentryErrorReporting.dsn` | Get DSN from Sentry's dashboard

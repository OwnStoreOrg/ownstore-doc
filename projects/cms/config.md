---
label: Config
title: CMS Config and ENVs
icon: note
order: 2
---

## ENV
CMS project currently supports 3 environments:
- `local` - For development
- `localproduction` - For development but with prod API
- `production` - For production

## Config
App config can be found in `config/appConfig.ts` file.

### config.global
Key | Description
--- | ---
`global.app` | Few app related information.
`global.domain` | Domain. For eg. `own-store-demo-cms.vercel.app` OR `localhost:3002`
`global.baseUrl` | Base URL. For eg. `https://own-store-demo-cms.vercel.app` or `http://localhost:3002`
`global.imageBaseUrl` | Cloudinary image base URL. For eg. `https://res.cloudinary.com/your-store/image/upload`. If you have mapped AWS S3 with Cloudinary, put that URL here. `imageBaseUrl + image path (from DB)` will render the image. **Note:** This is not for static images.
`global.apiBaseUrl` | API base URL to connect to. For eg. `http://localhost:3001`.
`global.webBaseUrl` | User-facing website URL. For eg. `http://localhost:3000` or `https://own-store-demo.vercel.app`.
`global.redirectToIndexViewAfterUpdate` | Whenever an entity is successfuly updated, do you want to redirect to its index page? This flag controls exactly that.
`global.redirectToIndexViewAfterDelete` | Whenever an entity is successfuly deleted, do you want to redirect to its index page? This flag controls exactly that.
`global.paginationFetchLimit` | How many items should be shown be fetched and shown per page during pagination.

### config.order
Key | Description
--- | ---
`order.recentOrders` | Config for recent orders page.
`order.autoRefresh` | Enable auto refresh of new orders.
`order.refreshIntervalInSeconds` | Control the refresh interval of recent orders.

### config.search
Key | Description
--- | ---
`search.limit` | How many results should be fetched and shown on search pages?

### config.image
Key | Description
--- | ---
`image.imageUploadDirectory` | While uploading images, a dropdown is shown to pick a directory. This mapping controls exactly the same.

### config.integrations

#### config.integrations.cloudinary
Config for Cloudinary integration.

Key | Description
--- | ---
`integrations.cloudinary.cloudName` | Cloudinary clound name. Get this from dashboard. Eg. `your-store`.
`integrations.cloudinary.uploadPresetName` | We are doing unsigned image upload, so we have to create a preset. Steps: <ul><li>Navigate to Cloudinary console.</li><li>Scroll down to `Upload presets` section.</li><li>Create a preset and make sure it is `unsigned`.</li></ul>

#### config.integrations.googleAnalytics
For Google analytics integration.

Key | Description
--- | ---
`integrations.googleAnalytics.enabled` | Use this flag to disable.
`integrations.googleAnalytics.code` | GA code. Get this from dashboard.

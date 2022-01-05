---
label: Commands
title: Website Commands
icon: gear
order: 4
---

Let's discuss the possible commands this project supports

## sync:contract
This command assumes both CMS and API projects are siblings. Syncs API contracts.
```bash
npm run sync:contract
```

## lint
This command analyze the codebase for any linting or formatting issues.
```bash
npm run lint
```

## lint:fix
Same as `lint` but fixes the issues
```bash
npm run lint:fix
```

## script:generate-manifest
Generates a manifest file for the project. 
```bash
npm run script:generate-manifest
```

## start:local
Starts the server on `3002` port using `local` env. Also syncs the contract.
```bash
npm run start:local
```

## start:localprod
Starts the server on `3002` port using `localproduction` env. Also syncs the contract.
```bash
npm run start:localprod
```

## build
Builds the entire project.
```bash
npm run build
```

## build:analyze
Builds the project and opens a UI to visualize the build size. Note: You will have to pass the ENV to start.
```bash
STORE_WEB_ENV=production npm run build:analyze
```

## start
This command can be used to start with build files. Note: You will have to pass the ENV to start.
```bash
STORE_WEB_ENV=local npm run start
STORE_WEB_ENV=production npm run start
```

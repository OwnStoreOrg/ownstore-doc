---
label: Commands
title: CMS Commands
icon: gear
order: 1
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

## start
This command can be used to start with build files. Note: You will have to pass the ENV to start.
```bash
STORE_CMS_ENV=local npm run start
STORE_CMS_ENV=production npm run start
```

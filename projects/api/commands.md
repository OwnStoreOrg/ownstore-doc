---
label: Commands
title: API Commands
icon: gear
order: 1
---

Let's discuss the possible commands this project supports

## lint:fix
This command will fix the linting issues. And report if not fixed.

```bash
npm run lint:fix
```

## start:local
Starts the server on `3001` port using `local` env.

If both MySQL and Redis connections are successful, then you will see a `running...` message.

```bash
npm run start:local
```

## start:prod
Starts the server using `production` env.

```bash
npm run start:prod
```

## build
To build the project

```bash
npm run build
```

## start
This command can be used to start with build files. Note: You will have to pass the ENV to start.
```bash
STORE_API_ENV=local npm run start
STORE_API_ENV=production npm run start
```

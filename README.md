# nuxt-docker-permission-error

This is a reproduction repository for Nuxt permission issue when running `yarn build` command inside the docker container with a fresh NuxtJS installation. This issue happen in:

```
Operating System: Windows 10 Linux Subsystem
Environment: WSL 2 - Ubuntu 20.04.3 LTS
Nuxt Version: v2.15.8
Node Version: v16.13.2
Docker Version: 20.10.12, build e91ed57
```

## Build Setup

This project uses Docker to build production ready app, the only thing to do is to run this command below. If you don't have Docker configured in your machine, please refer to the docker documentation page to perform the installation.

```bash
docker-compose up
```

## What is Expected?

This project should built successfully and accessible through the browser by accessing `http://localhost:3000`

## What is Actually Happening?

The project build fails with error

```
[+] Running 2/2
 ⠿ Network nuxt-docker-permission-error_default  Created 0.7s
 ⠿ Container nuxt-docker-permission-error        Created 30.3s

Attaching to nuxt-docker-permission-error
nuxt-docker-permission-error  | yarn run v1.22.17
nuxt-docker-permission-error  | $ nuxt start
nuxt-docker-permission-error  |
nuxt-docker-permission-error  |  FATAL  No build files found in /app/.nuxt/dist/server.
nuxt-docker-permission-error  | Use either `nuxt build` or `builder.build()` or start nuxt in development mode.
nuxt-docker-permission-error  |
nuxt-docker-permission-error  |   Use either `nuxt build` or `builder.build()` or start nuxt in development mode.
nuxt-docker-permission-error  |   at VueRenderer._ready (node_modules/@nuxt/vue-renderer/dist/vue-renderer.js:758:13)
nuxt-docker-permission-error  |   at async Server.ready (node_modules/@nuxt/server/dist/server.js:637:5)
nuxt-docker-permission-error  |   at async Nuxt._init (node_modules/@nuxt/core/dist/core.js:482:7)
nuxt-docker-permission-error  |
nuxt-docker-permission-error  |
nuxt-docker-permission-error  | ╭──────────────────────────────────────────────────────────────────────────────╮
│                                                                              │
│   ✖ Nuxt Fatal Error                                                         │
│                                                                              │
│   Error: No build files found in /app/.nuxt/dist/server.                     │
│   Use either `nuxt build` or `builder.build()` or start nuxt in              │
│   development mode.                                                          │
│                                                                              │
╰──────────────────────────────────────────────────────────────────────────────╯
nuxt-docker-permission-error  |
nuxt-docker-permission-error  | error Command failed with exit code 1.
nuxt-docker-permission-error  | info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
nuxt-docker-permission-error exited with code 1
```

## Additional Information

The issue seems to be resolved by performing `yarn build` locally from VS Code terminal that is attached to the project inside WSL before doing `docker-compose up`.

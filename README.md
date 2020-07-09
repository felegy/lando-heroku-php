Lando Heroku PHP
================

Lando Heroku PHP scaffold

- Heroku identical devenv (as far as possible)
  - heroku-18 official docker image
  - heroku official PHP buildpack
- Integrated tooling
  - Composer on appserver
  - Git on appserver
  - Heroku-cli on appserver

TOC
---
- [Lando Heroku PHP](#lando-heroku-php)
  - [TOC](#toc)
  - [Install Prerequisites](#install-prerequisites)
    - [Lando and Docker](#lando-and-docker)
    - [Local domain and cert for development](#local-domain-and-cert-for-development)
  - [First steps](#first-steps)
  - [VSCODE debugger settings](#vscode-debugger-settings)

Install Prerequisites
--------------------------

### Lando and Docker

The main dependency is `Lando` [https://lando.dev](https://lando.dev/) and also `Docker` of course, but Lando is contains Docker Desktop built-in on Windows and Mac.

### Local domain and cert for development

The Lando out of the box contains configuration with `traefic` [https://traefik.io](https://traefik.io) and local dev domain `*.lndo.site` see in [Lando Proxy](https://docs.lando.dev/config/proxy.html#automatic-port-assignment) and [Lando SSL/TLS](https://docs.lando.dev/config/security.html) . In above docs is contains a main settings for local development. When you are using `httpie` [https://httpie.org](https://httpie.org) you can define alias for TLS verification in your `.bashrc` or `.zshrc` like this:

```bash
alias http="http --verify=\"$HOME/.lando/certs/lndo.site.pem\""
```

First steps
-----------

Clone my  repo to local dev:

```bash
$ git clone git://github.com/felegy/lando-heroku-php.git lando-heroku-scaffold
```

Change directory to repo:

```bash
$ cd lando-heroku-scaffold && lando start
```

Create `.lando.yml` like this:

```yaml
# .lando.yml
name: lando-heroku-php

```
and copy `dev.env` to `.env` it contains `PORT` env like this:

```bash
# .env

PORT=3000

```

**Let's get this party started!**

```bash
$ lando start
```

Install `heroku-cli` to `appserver`:

```yaml
# .lando.yml
name: lando-heroku-php

services:
  appserver:
    build_as_root:
      - curl -fsSL https://cli-assets.heroku.com/install-ubuntu.sh | sh

```

Rebuild application:

```bash
$ lando rebuild
```

Change appservers startup command via `heroku cli local` by `Procfile` like on heroku:

```yaml
# .lando.yml
name: lando-heroku-php

services:
  appserver:
    build_as_root:
      - curl -fsSL https://cli-assets.heroku.com/install-ubuntu.sh | sh
    overrides:
      command: bash -l heroku local web
```
Rebuild application:

```bash
$ lando rebuild
```
Set proxy route to `appserver` => `PORT` 3000:

```yaml
# .lando.yml
name: lando-heroku-php

proxy:
  appserver:
    - lando-heroku-php.lndo.site:3000

services:
  appserver:
    build_as_root:
      - curl -fsSL https://cli-assets.heroku.com/install-ubuntu.sh | sh
    overrides:
      command: bash -l heroku local web
```

Rebuild application:

```bash
$ lando rebuild
```

[![asciicast](https://asciinema.org/a/279120.svg)](https://asciinema.org/a/279120)

## VSCODE debugger settings

[https://docs.lando.dev/guides/lando-with-vscode.html](https://docs.lando.dev/guides/lando-with-vscode.html)

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Listen for XDebug",
      "type": "php",
      "request": "launch",
      "port": 9000,
      "log": true,
      "pathMappings": {
        "/app/": "${workspaceFolder}/",
      }
    }
  ]
}
```

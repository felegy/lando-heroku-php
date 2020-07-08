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

[TOC]

Installation Prerequisites
--------------------------

### Lando and Docker

The main dependency is `Lando` [https://lando.dev](https://lando.dev/) and also `Docker` of course, but Lando is contains Docker builtin in on Windows and Mac.

### Local domain and cert for development

The Lando out of the box contains configuration with `traefic` [https://traefik.io](https://traefik.io) and local dev domain `*.lndo.site` see in [Lando Proxy](https://docs.lando.dev/config/proxy.html#automatic-port-assignment) and [Lando SSL/TLS](https://docs.lando.dev/config/security.html) . In above docs is contains a main settings for local development. When you are using `httpie` [https://httpie.org](https://httpie.org) you can define alias for TLS verification in your `.bashrc` or `.zshrc` like this:

```bash
alias http="http --verify=\"/Users/$USER/.lando/certs/lndo.site.pem\""
```

First steps
-----------

Clone my gists repo to local dev:

```bash
git clone git://github.com/felegy/lando-heroku-php.git php-devenv-scaffold
```

And change dir to repo and run:

```bash
cd php-devenv-scaffold && lando start
```

[![asciicast](https://asciinema.org/a/279120.svg)](https://asciinema.org/a/279120)

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

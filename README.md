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

<<<<<<< HEAD
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
=======
[TOC]

Installation Prerequisites
>>>>>>> + Update / php 7.4 and latest tools
--------------------------

### Lando and Docker

<<<<<<< HEAD
The main dependency is `Lando` [https://lando.dev](https://lando.dev/) and also `Docker` of course, but Lando is contains Docker Desktop builtin on Windows and Mac.
=======
The main dependency is `Lando` [https://lando.dev](https://lando.dev/) and also `Docker` of course, but Lando is contains Docker builtin in on Windows and Mac.
>>>>>>> + Update / php 7.4 and latest tools

### Local domain and cert for development

The Lando out of the box contains configuration with `traefic` [https://traefik.io](https://traefik.io) and local dev domain `*.lndo.site` see in [Lando Proxy](https://docs.lando.dev/config/proxy.html#automatic-port-assignment) and [Lando SSL/TLS](https://docs.lando.dev/config/security.html) . In above docs is contains a main settings for local development. When you are using `httpie` [https://httpie.org](https://httpie.org) you can define alias for TLS verification in your `.bashrc` or `.zshrc` like this:

```bash
<<<<<<< HEAD
alias http="http --verify=\"$HOME/.lando/certs/lndo.site.pem\""
=======
alias http="http --verify=\"/Users/$USER/.lando/certs/lndo.site.pem\""
>>>>>>> + Update / php 7.4 and latest tools
```

First steps
-----------

<<<<<<< HEAD
Clone my  repo to local dev:

```bash
$ git clone git://github.com/felegy/lando-heroku-php.git lando-heroku-scaffold
```

Change directory to repo:

```bash
$ cd lando-heroku-scaffold && lando start
```

Create `.lando.yml lige this:

```yaml
# .lando.yml
name: lando-heroku-php
proxy:
  appserver:
    - lando-heroku-php.lndo.site:3000

```
and copy `dev.env` to `.env` it contains `PORT` env like this:

```bash
# .env

PORT=3000

```

**Let's get this party started!**

```bash
$ lando start
=======
Clone my gists repo to local dev:

```bash
git clone git://github.com/felegy/lando-heroku-php.git php-devenv-scaffold
```

And change dir to repo and run:

```bash
cd php-devenv-scaffold && lando start
>>>>>>> + Update / php 7.4 and latest tools
```

[![asciicast](https://asciinema.org/a/279120.svg)](https://asciinema.org/a/279120)

<<<<<<< HEAD
## VSCODE debugger settings

[https://docs.lando.dev/guides/lando-with-vscode.html](https://docs.lando.dev/guides/lando-with-vscode.html)

=======
>>>>>>> + Update / php 7.4 and latest tools
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

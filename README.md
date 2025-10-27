## Team

### Merkle DACH
- Adrien Sacco - Delivery Lead / Overall Streams Lead - adrien.sacco@merkle.com
- Mathias Hayoz - 	Experience Strategist - mathias.hayoz@merkle.com
- Milovan Krivokapic - Lead Software Engineer - milovan.krivokapic@merkle.com
- Danko Krstic - Senior Software Engineer - danko.krstic@merkle.com
- Ernst Ammann - Senior Frontend Architect - ernst.ammann@merkle.com
## Technology
![Drupal 10](https://img.shields.io/badge/CMS-Drupal%2010-blue)
![Acquia](https://img.shields.io/badge/Platform-Acquia-blue)
[![CGIAR CICD](https://github.com/CG-SO/cgiarorg-web/actions/workflows/workflow.yml/badge.svg?branch=develop)](https://github.com/CG-SO/cgiarorg-web/actions/workflows/workflow.yml)

# Installation

## Install Docker

Follow Docker installation instructions on [Documentation Page](https://docs.docker.com/desktop/install/mac-install/).

## Install Lando

Installation via DMG file is easiest and recommended. Follow these steps:

1. Download the latest .dmg package from [GitHub](https://github.com/lando/lando/releases)
2. Mount the DMG by double-clicking it
3. Double-click on the LandoInstaller.pkg
4. Go through the setup workflow
5. Enter your username and password when prompted

# Project initialization

## First time initialization

When initializing project for the first time, first run Lando instance and run following command from the root of the
project

```bash
lando start
```

Now you can run automated script created to do all necessary installations and configuration

```bash
lando first-init
```

_Note:_ By default, Lando will attempt to bind the proxy to your host machine's port 80 and 443. If it cannot bind to
these addresses, which is usually the case if something else like a local apache service is running, it will fallback to
other commonly used ports such as 8888 and 444.

Following credentials for admin user will be set:
Username: _admin_
Password: _admin_

In addition, please make sure to create `drupal.env` file in .lando folder, to be able to use env file.

## Add SSL certificate and enable HTTPS

To be enabled to use HTTPS protocol on your local machine, add certificate using following command

```bash
sudo security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.keychain ~/.lando/certs/lndo.site.pem
```

## Run Lando instance

To run Lando instance any other time (if it's not running), just run

```bash
lando start
```

in the root of the project.

# Useful commands

_Note:_ All commands must be run from the root of the project.

## Drupal related commands

### Install composer packages

```bash
lando composer install
```

### Import Drupal configuration

```bash
lando drush cim
```

### Apply database updates required

```bash
lando drush updb
```

### Clear Drupal cache

```bash
lando drush cr
```

## Lando related commands

### Restart Lando instance

```bash
lando restart
```

### List information about local server

```bash
lando info
```

## XDEBUG

Note that xDebug is enabled by default.

### Enable xDebug

```bash
lando xdebug-on
```

### Disable xDebug

```bash
lando xdebug-off
```

## Acquia CLI
Acquia CLI (acli) is a tool for interacting with Cloud Platform. [Read more](https://docs.acquia.com/acquia-cloud-platform/add-ons/acquia-cli/docs)


For the first time, you have to authenticate with Access Token created on your Acquia Cloud Platform profile:
```bash
lando acli auth:login
```

There are many useful commands that `acli` provides, please [see here](https://docs.acquia.com/acquia-cloud-platform/add-ons/acquia-cli/commands)

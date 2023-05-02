# LightningJS_and_LUI_instructions

Instructions to install and write LightningJS and Lightning UI apps.

These instructions are written in May 2023 for Mac OS.

## Table of Contents

* [Prerequisites](#prerequisites)
* [Lightning Installation](#installation)
* [Initialize Your Lightning App](#initialize)

## <a name="prerequisites"></a>Prerequisites

### Knowledge required

* JavaScript
* JSON RPC (Remote Procedure Call)

#### What is JSON RPC

It is a remote procedure call specification, allowing remote execution of a function and receiving the result, no matter that server's OS or that function's programming language.

### Pre-installed

* node
* npm

## <a name="installation"></a>Lightning Installation

I will be using npm instead of yarn.

### Install LightningJS and LightningUI (LUI)

1. Create a new project directory:
```bash
mkdir <name of project>
```
2. Navigate into the new directory:
```bash
cd <name of project>
```
3. Initialize npm __inside__ of __the new directory__ with:
```bash
npm init
```
4. Create a local `.npmrc` file in the project folder containing the following content:
```bat
@lightning:registry=https://artifactory.comcast.com/artifactory/api/npm/Lightning-npm-releases
@suite-themes:registry=https://artifactory.comcast.com/artifactory/api/npm/xds-npm
```
5. install lightning UI and lightning JS with:
```bash
npm install -S @lightning/ui @lightningjs/core
```

### Install Lightning CLI

Install Lightning CLI (lightning's command line interface) with:
```bash
npm install -g @lightningjs/cli
```
or with __sudo__ if you don't have the correct permissions:
```bash
sudo npm install -g @lightningjs/cli
```
#### how to use Lightning CLI

CLI commands begin with `lng`.  You will use CLI in terminal like so:
```bash
lng <command> [options]
```

#### test your installation
```bash
lng -V
```

## <a name="initialize"></a>Initialize Your Lightning App

CLI also contains a helpful boilerplate to begin your app from.

(Don't worry about running `npm install` since this will happen automatically with `lng create`.)

1. Create your app with:
```bash
lng create
```
and follow the prompts.   Note the following prompts:

  * name your app without spaces
  * I like to create my app as a new directory (default) so that I can have multiple apps in one project folder.  If you would rather everything stays within your project directory, the necessary boilerplate modules will be added to the project's `node_modules` directory
  * I like to name my app directory with just the app name (rather than `com.domain.app.MyAppName`)
  * I'd rather not set up git in my app directory since I may already be using GitHub for my project folder.
  * I'm not using TypeScript (the default).  I will be using JavaScript instead.

2. Build your app with:
```bash
lng build
```
3. Run your app in your localhost with:
```bash
lng serve
```

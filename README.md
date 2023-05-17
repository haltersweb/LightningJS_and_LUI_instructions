# LightningJS and LUI instructions

Instructions to install and write LightningJS and Lightning UI (LUI) apps.

These instructions are written in May 2023 for Mac OS.

## Table of Contents

* [Prerequisites](#prerequisites)
* [Lightning Installation](#installation)
* [Initialize Your Lightning App](#initialize)
* [Understanding Lightning](#understand)

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

### Prepare the project directory

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

### Install LightningJS

<!-- THE FOLLOWING IS NOT NEEDED
Create a local `.npmrc` file in the project folder containing the following content:
```bat
@lightning:registry=https://artifactory.comcast.com/artifactory/api/npm/Lightning-npm-releases
@suite-themes:registry=https://artifactory.comcast.com/artifactory/api/npm/xds-npm
```
-->

Using the save flag (--save or -S), install LightningJS.

(Save means the installed package is saved to package.json as a dependency. While the default is true in newer versions of npm, this is a good reminder.)

Install LightningJS with:
```bash
npm install -S @lightningjs/core
```

### Install LightningUI (LUI)

Using the save flag (--save or -S), install LUI.

(Save means the installed package is saved to package.json as a dependency. While the default is true in newer versions of npm, this is a good reminder.)

Install LUI with:
```bash
npm install -S @lightning/ui
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
and follow the prompts.   Notes on the prompts:

  * Name your app without spaces.
  * I like to name my app's (relative) folder with just the app name such as `MyAppName` (rather than `com.domain.app.MyAppName`)
  * I'm not using TypeScript (the default).  I will be using JavaScript instead.
  * I like to create my app as a new directory (default) so that I can have multiple apps in one project folder.  If you would rather everything stays within your project directory, the necessary boilerplate modules will be added to the project's `node_modules` directory
  * I'd rather not set up an empty git repository for my app since I may already be using GitHub for my project folder.

2. Build your app with:
```bash
lng build
```
3. Run your app in your localhost with:
```bash
lng serve
```

## <a name="understand"></a>Understanding Lightning

(from [Lightning Documentation](https://lightningjs.io/docs/#/what-is-lightning/index))

### Overview

Lightning is a JavaScript development platform for TV apps.  It uses WebGL rather than the DOM for rendering for high performance and smooth animation.  The only HTML element used is `<canvas>`.

Lightning consists of three parts:

__Lightning Core__ contains the Lightning Library and Render Engine which offers high performance and smooth animation. ([Lightning Core reference](https://lightningjs.io/docs/#/lightning-core-reference/index))

__Lightning SDK__ contains __Lightning Core__ and helpful app development plugins. ([Lightning SDK reference](https://lightningjs.io/docs/#/lightning-sdk-reference/index))

__Lightning CLI__ (command line interface) makes building apps easy with prefab components and app uploading tools.  Use Lightning CLI along with Lightning SDK. ([Lightning CLI Reference](https://lightningjs.io/docs/#/lightning-cli-reference/index))

#### Componentization

Lightning interfaces are built up from __components__ which can also be __collections of components__.  The app itself is a component which contains page components.  The page components each contain components, etc.

### Interaction

#### <a name="focus_management"></a>Focus management

Since there is no DOM Tree to navigate through, __focus__ is handled by tracking an __active component__ via JavaScript.  A __focus path__ is defined as the __active component and its decendants__.

#### Remote control interaction

A remote control sends KeyCodes.  A KeyCode event listener is attached to the canvas element.  KeyCode events are then understood in relation to the active component (see [focus management](#focus_management) above).

#### Routing between URLs

Use the __Router__ plugin to create URL-driven apps.

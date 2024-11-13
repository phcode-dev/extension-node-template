# Extension Template

Quick start and create a new `Phoenix Code node.js extension` by using this template. This template extension works in browser as well as desktop builds. In browser, it
will not use node, and node.js based functionalities are not available. Desktop
builds will use node capabilities.

In desktop builds, there is an additional capability to execute node.js code.
This is helpful if you want to extend the functionality of Phoenix Code using
the vast npm library.

For creating extensions that do not need node, follow this link:
https://github.com/phcode-dev/extension-template

## Setting up node extensions

In package.json, add the following section

```json
{
    "nodeConfig": {
        "nodeIsRequired": false,
        "main": "node/index.js",
        "npmInstall": "node/"
    }
}
```

#### `nodeConfig` Object

The `nodeConfig` object indicates that this is a Node extension.

#### `nodeIsRequired` Field

-   Set this field to `true` if the extension relies on Node and won't function
    without it.
-   If set to `false` or omitted, the extension can still be loaded in browser
    versions of Phoenix code without Node support, But will use node in native
    builds.
-   It will be shown in the extension manager dialog in browser builds as well.

#### `main` Field

-   Specifies the main entry point for the Node.js component of the extension.
-   Should point to the main JavaScript file for the Node part of the extension.
-   Example: `"main": "node/index.js"`

#### `npmInstall` Field (Optional)

-   Specifies the path to run `npm install` when the user installs the extension
    from the extension manager.
-   It's advisable not to package `node_modules` inside the extension. Only the
    package lock file should be distributed.
-   Example: `"npmInstall": "node/"`

## Communicating between node.js and Phoenix Code

### NodeConnector-API

create [NodeConnector-API](https://docs.phcode.dev/api/API-Reference/NodeConnector) to call functions and send events between your node.js and Phoenix Code extension components.

-   This is available as a global object `global.createNodeConnector`. See above
    link for API docs.
-   Another API -
    [EventDispatcher-API](https://docs.phcode.dev/api/API-Reference/utils/EventDispatcher)
    is also available in the global context as `global.EventDispatcher` for
    event trigger/listen within node.

# Using this template

Follow the below 4 steps to start using this template:

Refer this
[link](https://docs.phcode.dev/api/creating-extensions) for detailed extension documentation after following the below steps:

## step 1

Login with GitHub: https://github.com/login

## step 2

Create a new repository using this template.
![New extension from template](https://user-images.githubusercontent.com/5336369/223931565-2708e516-a422-4e7b-9d89-9ac48c919c3d.gif)

## step 3

-   Clone your GitHub Repo created from `step 2`. See
    [this link](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)
    to lean how to clone a repository from GitHub.
-   Edit `package.json` file in template, make sure to update the following fields accordingly:

| Field       | Description                                                            |
|-------------|------------------------------------------------------------------------|
| `title`     | Replace "Name of the extension" with the actual title of your extension. |
| `name`      | Change `github-<owner>-<repo>` to your specific package name, formatted as `github-yourusername-reponame`. |
| `description` | Update to a brief, relevant description of what your extension does.  |
| `version`   | Start with "0.0.1" or update to reflect your current version following semantic versioning. |
| `license`   | Confirm "MIT" is suitable or specify another license if necessary.     |
| `author`    | Replace with your name and a link to your GitHub profile or another URL. |
| `homepage`  | Set to the URL of your project’s homepage or GitHub repository.        |
| `engines`   | Ensure compatibility with the required Brackets version, e.g., ">=3.0.0". |
| `categories`| Update "demo" with relevant categories that fit your extension.         |
| `keywords`  | Update or append additional keywords that describe your extension.    |
| `files`     | Ensure this includes all necessary files and folders for your extension. |



## step 4

-   Go to https://create.phcode.dev .This is a special development centric
    website of phcode.dev which shows non minified js/css files in the browser
    developer tools.
-   Open the cloned folder and select `Debug > Load Project As Extension`

![image](https://user-images.githubusercontent.com/5336369/224746152-0416a862-891a-4fe1-b9dd-09add25a6cc0.png)

-   You can now make code changes to your extension and select
    `Debug> Reload With Extensions` to test the new code changes.
-   When you are done developing the extension/theme, select
    `Debug> Unload Project As Extension` to unload the extension.

![image](https://user-images.githubusercontent.com/5336369/224747590-556dff1d-5b29-41c3-88a0-3ce72ab643d0.png)

# Detailed Documentation

Please go to [https://docs.phcode.dev/api/creating-extensions](https://docs.phcode.dev/api/creating-extensionss) for more documentation/community support links.

# Publishing your extension to the repository

Once you have built your extension/theme, you can publish the extension to
phcode.dev extension repository in a single step directly from this repo. Please
see publish section in this link for more details: [Publishing extension and themes](https://docs.phcode.dev/api/publishing-extensions)

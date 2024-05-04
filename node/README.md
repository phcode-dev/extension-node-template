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

create
[NodeConnector-API](https://github.com/phcode-dev/phoenix/wiki/NodeConnector-API)
to call functions and send events between your node.js and Phoenix Code
extension components.

-   This is available as a global object `global.createNodeConnector`. See above
    link for API docs.
-   Another API -
    [EventDispatcher-API](https://github.com/phcode-dev/phoenix/wiki/EventDispatcher-API)
    is also available in the global context as `global.EventDispatcher` for
    event trigger/listen within node.

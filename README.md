# @mete-work/plugins
[![](https://img.shields.io/npm/dw/@mete-work/plugins.svg)](https://www.npmjs.com/package/@mete-work/plugins) 
[![](https://img.shields.io/npm/v/@mete-work/plugins.svg)](https://www.npmjs.com/package/@mete-work/plugins)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)

A simple registry that stores all plugins in a shared object.
The only requirement for a plugin is to have a `name` and a `type` properties. 
The rest is entirely up to you.

There is nothing spectacular going on under the hood, just a simple 
object for storing references and a few utility functions.

## Install
```
npm install --save @mete-work/plugins
```

Or if you prefer yarn: 
```
yarn add @mete-work/plugins
```

## Usage

### Adding a plugin
```
import { registerPlugins } from "@mete-work/plugins";

// Add a plugin
registerPlugins({
    name: "my-plugin",
    type: "say-hi",
    render: () => "Hi!"
});

registerPlugins({
    name: "my-second-plugin",
    type: "say-hi",
    render: () => "Yo!"
});
```

### Getting plugins by type
```
// anywhere in your app
import { getPlugins } from "@mete-work/plugins";

const plugins = getPlugins("say-hi");
plugins.forEach(plugin => {
    // Call "render" function
    plugin.render();
});
```

### Getting a single plugin by name
```
// anywhere in your app
import { getPlugin } from "@mete-work/plugins";

const plugin = getPlugin("my-plugin");
// Call "render" function
plugin.render();
```

### Removing a plugin
```
// anywhere in your app
import { unregisterPlugin } from "@mete-work/plugins";

unregisterPlugin("my-plugin");
```

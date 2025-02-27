# Vite SVG loader
Vite plugin to load SVG files as Vue components, using SVGO for optimization.

<a href="https://www.npmjs.com/package/vite-svg-loader" target="_blank"><img src="https://img.shields.io/npm/v/vite-svg-loader?style=flat-square" alt="Version"></a>
<a href="https://www.npmjs.com/package/vite-svg-loader" target="_blank"><img src="https://img.shields.io/npm/dw/vite-svg-loader?style=flat-square" alt="Downloads"></a>
<a href="https://github.com/jpkleemans/vite-svg-loader/actions" target="_blank"><img src="https://img.shields.io/github/workflow/status/jpkleemans/vite-svg-loader/End-to-end%20tests?label=tests&style=flat-square" alt="Tests"></a>
<a href="https://www.npmjs.com/package/vite-svg-loader" target="_blank"><img src="https://img.shields.io/npm/l/vite-svg-loader?style=flat-square" alt="License"></a>

```vue
<template>
  <MyIcon />
</template>

<script setup>
import MyIcon from './my-icon.svg'
</script>
```

### Install
```bash
npm install vite-svg-loader --save-dev
```

### Setup

#### `vite.config.js`
```js
import svgLoader from 'vite-svg-loader'

export default defineConfig({
  plugins: [vue(), svgLoader()]
})
```

### Import params
### URL
SVGs can be imported as URLs using the `?url` suffix:
```js
import iconUrl from './my-icon.svg?url'
// '/assets/my-icon.2d8efhg.svg'
```

### Raw
SVGs can be imported as strings using the `?raw` suffix:
```js
import iconRaw from './my-icon.svg?raw'
// '<?xml version="1.0"?>...'
```

### Component
SVGs can be explicitly imported as Vue components using the `?component` suffix:
```js
import IconComponent from './my-icon.svg?component'
// <IconComponent />
```

### Default import config
When no explicit params are provided SVGs will be imported as Vue components by default.
This can be changed using the `defaultImport` config setting,
such that SVGs without params will be imported as URLs (or raw strings) instead.

#### `vite.config.js`
```js
svgLoader({
  defaultImport: 'url' // or 'raw'
})
```

### SVGO Configuration
#### `vite.config.js`
```js
svgLoader({
  svgoConfig: {
    multipass: true
  }
})
```

### Disable SVGO
#### `vite.config.js`
```js
svgLoader({
  svgo: false
})
```

### Use with TypeScript
If you use the loader in a Typescript project, you'll need to import your svg files with the `?component` param: `import MyIcon from './my-icon.svg?component'`.

You'll also need to reference the type definitions:
```ts
/// <reference types="vite-svg-loader" />
```

## Sponsors

<a href="https://www.nexxtmove.nl/" target="_blank">
  <img src="https://raw.githubusercontent.com/jpkleemans/attribute-events/gh-pages/nexxtmove-logo.svg" alt="Nexxtmove Logo" width="200">
</a>

Thanks to <a href="https://www.nexxtmove.nl/" target="_blank">Nexxtmove</a> for sponsoring the development of this project.  
Your logo or name here? [Sponsor this project](https://github.com/sponsors/jpkleemans).

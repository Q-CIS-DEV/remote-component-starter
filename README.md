# Remote Component Starter Kit


Starter Kit for quickly creating a Remote React Component that can be Remotely Loaded by Trood EM Composer

## Getting Started

Clone the repository or download it in zip

## Files

There are a few important files, one set is used for the bundle, another set for local development.

- `src/index.js` - Entrypoint of the Remote Component. The component needs to be the `default` export.
- `src/webpack-dev-server.js` - Entrypoint for `webpack-dev-server`. This is only used for development and will not be included in the final bundle.
- `src/index.html` - HTML for `webpack-dev-server`. This is only used for development and will not be included in the final bundle.

## Building

The bundle will be output to the `dist/main.js`.

```bash
npm run build
```

Create a development build for easier debugging.

```bash
npm run build:dev
```

## Debugging

The component can be debugged locally by first starting `webpack-dev-server`.

```bash
npm run start
```

## Changing the Output

The bundle as a default will be output to the `dist/main.js`. This can be updated by changing the following two files:

1. `entry` in `webpack-main.config.js`. Update the `main` property to a desired output name.

```javascript
module.exports = {
  ...
  entry: {
    main: "./src/index.js"
  },
  ...
};
```

2.  `url` variable in `src/webpac-dev-server.js`

```javascript
// different paths for localhost vs s3
const url =
  global.location.hostname === "localhost" ? "/dist/main.js" : "main.js";
```

## Upload and use

After building step you can upload output file (default `"/dist/main.js"`) to our file service or any server (with CORS support)
For use your custom component in Trood EM Composer paste component `Remote` into fragment and set url address to uploaded js file
In Advanced settings of `Remote` component you can set any props

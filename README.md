# htmlhint-loader-ng2

> A webpack loader for htmlhint-ng2, based off htmlhint-loader.

[![NPM version](https://img.shields.io/npm/v/htmlhint-loader-ng2.svg?style=flat)](https://www.npmjs.com/package/htmlhint-loader-ng2)
[![License](https://img.shields.io/npm/l/htmlhint-loader-ng2.svg?style=flat)](https://www.npmjs.com/package/htmlhint-loader-ng2)
[![NPM count](https://img.shields.io/npm/dm/htmlhint-loader-ng2.svg?style=flat)](https://www.npmjs.com/package/htmlhint-loader-ng2)
[![NPM count](https://img.shields.io/npm/dt/htmlhint-loader-ng2.svg?style=flat)](https://www.npmjs.com/package/htmlhint-loader-ng2)

## Install

```
npm install htmlhint-loader-ng2
```

## Usage

```javascript
module.exports = {
  module: {
    preLoaders: [
      {
        test: /\.html/, 
        loader: 'htmlhint-ng2', 
        exclude: /node_modules/
      }
    ]
  }
}
```

### Options

You can directly pass some [htmlhint rules](https://github.com/yaniswang/HTMLHint/wiki/Rules) by

- Adding a query string to the loader for this loader usage only

```javascript
{
  module: {
    preLoaders: [
      {
        test: /\.html/,
        loader: 'htmlhint-ng2?{tagname-lowercase: true}',
        exclude: /node_modules/
      },
    ]
  }
}
```

- Adding a `htmlhint` entry in your webpack config for global options:

```javascript
module.exports = {
  htmlhint: {
    configFile: 'path/.htmlhintrc'
  }
}
```

#### `configFile`

A path to a json file containing the set of htmlhint rules you would like applied to this project. *By default all rules are turned off and it is up to you to enable them.*

Example file:
```javascript
{
  "tagname-lowercase": true,
  "attr-lowercase": true,
  "attr-value-double-quotes": true
}
```

#### `formatter` (default: a function that pretty prints any warnings and errors)

The function is called with an array of messages direct for htmlhint and must return a string.

#### `emitAs` (default: `null`)

What to emit errors and warnings as. Set to `warning` to always emit errors as warnings and `error` to always emit warnings as errors. By default the plugin will auto detect whether to emit as a warning or an error.

#### `failOnError` (default `false`)

Whether to force webpack to fail the build on a htmlhint error

#### `failOnWarning` (default `false`)

Whether to force webpack to fail the build on a htmlhint warning

#### `customRules`

Any custom rules you would like added to htmlhint. Specify as an array like so:
```javascript
module.exports = {
  htmlhint-ng2: {
    customRules: [{
      id: 'my-rule-name',
      description: 'Example description',
      init: function(parser, reporter) {
        //see htmlhint docs / source for what to put here
      }
    }]
  }
}
```

## Credits

I based a lot of this code off the [eslint-loader](https://github.com/MoOx/eslint-loader) and the [gulp htmlhint plugin](https://github.com/bezoerb/gulp-htmlhint), so a big thanks is due to the authors of those modules.

## Licence

MIT

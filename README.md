[![Build Status](https://travis-ci.org/terpiljenya/import-glob.svg)](https://travis-ci.org/terpiljenya/import-glob)
[![npm version](https://badge.fury.io/js/import-glob.svg)](https://badge.fury.io/js/import-glob)
# import-glob
ES6 import with glob patterns (preloader for Webpack)

Expands globbing patterns for ES6 `import` statements.

---
```js
import modules from "./foo/**/*.js";
```
Expands into
```js
import * as module0 from "./foo/1.js";
import * as module1 from "./foo/bar/2.js";
import * as module2 from "./foo/bar/3.js";

modules = { 'foo/1.js': module0, 'foo/bar/2.js': module1, 'foo/bar/3.js': module2 }
```
---
__For side effects:__

```js
import "./foo/**/*.scss";
```
Expands into
```js
import "./foo/1.scss";
import "./foo/bar/2.scss";
```
---
__For sass:__

```scss
@import "./foo/**/*.scss";
```
Expands into
```scss
@import "./foo/1.scss";
@import "./foo/bar/2.scss";
```

---

## Install
```sh
npm install import-glob --save-dev
```

## Usage
You can use it one of two ways, the recommended way is to use it as a preloader

```js
{
  module: {
    rules: [
      {
        test: /\.js/,
        use: [{ loader: 'import-glob' }],
      },
    ],
  },
}
```

Alternatively you can use it as a chained loader
```js
require('!import-glob!foo/bar.js')
```

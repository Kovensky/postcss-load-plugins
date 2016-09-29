[![npm][npm]][npm-url]
[![deps][deps]][deps-url]
[![tests][travis]][travis-url]
[![coverage][cover]][cover-url]
[![code style][style]][style-url]
[![chat][chat]][chat-url]

<div align="center">
  <img width="108" height="108" title="Load Plugins" src="http://michael-ciniawsky.github.io/postcss-load-plugins/logo.svg">
  <a href="https://github.com/postcss/postcss">
    <img width="108" height="108" title="PostCSS"           src="http://postcss.github.io/postcss/logo.svg" hspace="20">
  </a>
  <h1>Load Plugins</h1>
  <p>Autoload Plugins for PostCSS<p>
</div>

<h2 align="center">Install</h2>

```bash
npm i -D postcss-load-plugins
```

<h2 align="center">Usage</h2>

Install plugin as usual and make sure saving them to your ***package.json*** dependencies and/or devDependencies.

```
npm i -S|-D postcss-plugin
```

After installing your plugins there a two common ways to declare your plugins and options.

- Create **postcss** section in your projects **package.json**.
- Create a **postcss.config.js**  or  **postcssrc.json** file.

<h2 align="center">Options</h2>

Plugin **options** can either take `false`  or an object literal
`{}` as value.

**`false`**: Plugin loads with no options (defaults)

**`[Object]`**: Plugin loads with set options.

### Order

Plugin **order** is determined by declaration in the plugins section.

```js
postcss: {
  plugins: {
    'postcss-plugin1': false,
    'postcss-plugin2': false,
    'postcss-plugin3': {}
  }
}

// Loaded Plugin Setup
[
  require('postcss-plugin1')(),
  require('postcss-plugin2')(),
  require('postcss-plugin3')(options)
]
```

### package.json

```json
{
 "dependencies": {
   "postcss-bem": "^0.2.2",
   "postcss-nested": "^1.0.0",
   "postcss-import": "^8.1.2"
 },
 "postcss": {
   "plugins": {
     "postcss-import": false,
     "postcss-nested": false,
     "postcss-bem": { "style": "bem" }
    }
  }
}
```

### postcss.config.js

```js
module.exports = {
  plugins: {
    'postcss-import': false,
    'postcss-nested': false,
    'postcss-bem': { style: 'bem' }
  }
}
```
### postcssrc.json

```json
{
  "plugins": {
    "postcss-import": false,
    "postcss-nested": false,
    "postcss-bem": { "style": "bem" }
  }
}
```
<h2 align="center">Example</h2>

```js
const { readFileSync } = require('fs')

const postcss = require('postcss')
const pluginsrc = require('postcss-load-plugins')()

const css = readFileSync('./index.css', 'utf8')

pluginsrc.then((plugins) => {
  postcss(plugins)
    .process(css)
    .then(result => console.log(result.css))
}))
```

<h2 align="center">Maintainers</h2>

<table>
  <tbody>
    <tr>
      <td align="center">
        <img width="150 height="150"
        src="https://avatars.githubusercontent.com/u/5419992?v=3&s=150">
        <br />
        <a href="https://github.com/michael-ciniawsky">Michael Ciniawsky</a>
      </td>
      <td align="center">
        <img width="150 height="150"
        src="https://avatars.githubusercontent.com/u/2437969?v=3&s=150">
        <br />
        <a href="https://github.com/ertrzyiks">Mateusz Derks</a>
      </td>
    </tr>
  </tbody>
</table>

<h2 align="center">LICENSE</h2>

> (MIT)

> Copyright (c) 2016 Michael Ciniawsky <michael.ciniawsky@gmail.com>

> Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

> The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[npm]: https://img.shields.io/npm/v/postcss-load-plugins.svg
[npm-url]: https://npmjs.com/package/postcss-load-plugins

[deps]: https://david-dm.org/michael-ciniawsky/postcss-load-plugins.svg
[deps-url]: https://david-dm.org/michael-ciniawsky/postcss-load-plugins

[style]: https://img.shields.io/badge/code%20style-standard-yellow.svg
[style-url]: http://standardjs.com/

[travis]: http://img.shields.io/travis/michael-ciniawsky/postcss-load-plugins.svg
[travis-url]: https://travis-ci.org/michael-ciniawsky/postcss-load-plugins

[cover]: https://coveralls.io/repos/github/michael-ciniawsky/postcss-load-plugins/badge.svg?branch=master
[cover-url]: https://coveralls.io/github/michael-ciniawsky/postcss-load-plugins?branch=master

[chat]: https://img.shields.io/gitter/room/postcss/postcss.svg?maxAge=2592000
[chat-url]: https://gitter.im/postcss/postcss

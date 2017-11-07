# vue-typing

> A simple Vue.js component that simulates typing"

# Usage

## ES6 Modules / CommonJS

```bash
$ npm run build
```

```js
import VueTyping from 'dist/vue-typing';

Vue.component('vue-typing', VueTyping);
```

```html
<vue-typing text="Hello World!"></vue-typing>
```

## UMD

```bash
$ npm run build:umd
```

```html
<vue-typing text="Hello World!"></vue-typing>

<script src="https://unpkg.com/vue" charset="utf-8"></script>
<script src="./dist/vue-typing.min.js" charset="utf-8"></script>

<script type="text/javascript">
  Vue.component('vue-typing', window.VueTyping);
</script>
```

## Installation

### Using yarn

`yarn add vue-typing`

### Using npm

`npm i --save vue-typing`

## Demo and Docs

`npm run serve`

## Tests

This template uses karma with chai by default, you can change test settings in poi.config.js

`npm run test`
`npm run test:watch`
`npm run test:cov`

## License

This project is licensed under [MIT License](http://en.wikipedia.org/wiki/MIT_License)

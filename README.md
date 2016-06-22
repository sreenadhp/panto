# Pantojs
[![NPM version][npm-image]][npm-url] [![Downloads][downloads-image]][npm-url] [![Dependency status][david-dm-image]][david-dm-url] [![Dev Dependency status][david-dm-dev-image]][david-dm-dev-url]


_**Pantojs**_ is an ambitious file-transforming task runner. It supports simultaneous & furcal transforming streams, incremental transforming and stream nodes cache, which make file-transforming much flexible and fast.


```js
const panto = require('panto');

panto.setOptions({
    cwd: 'your_project_dir'
});

// Isomorphic JavaScript
const srcJs = panto.pick('**/*.{js,jsx}').pipe(panto.read());
srcJs.pipe(panto.babel(clientBabelOptions)).pipe(panto.write()).end();
srcJs.pipe(panto.babel(serverBabelOptions)).pipe(panto.write()).end();

// Less
panto.pick('**/*.less').pipe(panto.read()).pipe(panto.less()).pipe(panto.write()).end();

// Others
panto.rest().pipe(panto.read()).pipe(panto.filter()).pipe(panto.write()).end();

panto.build().then(() => {
    panto.watch();
});
```

Make your own _transformer_, just extend [panto-transformer](https://github.com/pantojs/panto-transformer), make sure _\_transform_ function returns a [Promise](https://promisesaplus.com/) object.


[npm-url]: https://npmjs.org/package/panto
[downloads-image]: http://img.shields.io/npm/dm/panto.svg
[npm-image]: http://img.shields.io/npm/v/panto.svg
[david-dm-url]:https://david-dm.org/pantojs/panto
[david-dm-image]:https://david-dm.org/pantojs/panto.svg
[david-dm-dev-url]:https://david-dm.org/pantojs/panto#info=devDependencies
[david-dm-dev-image]:https://david-dm.org/pantojs/panto/dev-status.svg
# nomiseco

Nodejs middleware for serving compressed files

## Getting Started

This package does not compress your files on the fly. You will need to generate static .gz and .br files, for example:

```shell
$ cd /path/to/you/static/files
$ for f in $(find . -type f); do gzip < $f > $f.gz && brotli < $f > $f.br; done
```

### Prerequisites

nodejs
express

### Installing


```
npm install --save nomiseco
```

## Running the tests

```
npm run test
```

## Deployment

### Basic Usage

```js
const app = require('express')()
const path = require('path')
const { compressionMiddleware } = require('nomiseco')

const publicPath = path.join(__dirname, 'public')

console.log(process.env.NODE_ENV) // prints `production`
// by default, the middleware only takes effect if NODE_ENV is set to production

app.use(
  compressionMiddleware,
  express.static(publicPath)
)
```

## License

MIT

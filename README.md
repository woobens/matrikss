# node-matrikss

(generator-matrikss)[https://github.com/woobens/node-generator-matrikss] 

## Install

```bash
$ npm install matrikss --save
```

### Use yeoman generator

```bash
$ npm install generator-matrikss -g
# Express
$ yo matrikss:express
$ yo matrikss:ben-web
```

## How to use

```javascript
'use strict';

const API = require('matrikss').default;

// API info for document
const INFO = {
  title: 'matrikss-demo',
  description: 'Easy to write, easy to test...',
  version: new Date(),
  host: 'http://127.0.0.1:3000',
  basePath: '/api',
};

// API group info
const GROUPS = {
  Index: 'Ben',
};

// Init API
const apiService = new API({
  info: INFO,
  groups: GROUPS,
});

apiService.api.get('/index')
  .group('Index')
  .title('Test api')
  .register((req, res) => {
    res.end('Hello, API Framework Index');
  });

const express = require('express');
const app = express();
const router = new express.Router();
app.use('/api', router);

// bing express router
apiService.bindRouter(router, apiService.checkerExpress);

app.listen(3000, function () {
  console.log('matrikss-demo listening started');
});
```

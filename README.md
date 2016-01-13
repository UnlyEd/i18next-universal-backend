# Introduction

[![Travis](https://img.shields.io/travis/i18next/i18next-xhr-backend/master.svg?style=flat-square)](https://travis-ci.org/i18next/i18next-xhr-backend)
[![Coveralls](https://img.shields.io/coveralls/i18next/i18next-xhr-backend/master.svg?style=flat-square)](https://coveralls.io/github/i18next/i18next-xhr-backend)
[![npm version](https://img.shields.io/npm/v/i18next-xhr-backend.svg?style=flat-square)](https://www.npmjs.com/package/i18next-xhr-backend)
[![Bower](https://img.shields.io/bower/v/i18next-xhr-backend.svg)]()
[![David](https://img.shields.io/david/i18next/i18next-xhr-backend.svg?style=flat-square)](https://david-dm.org/i18next/i18next-xhr-backend)

This is a simple i18next backend to be used in the browser. It will load resources from a backend server using xhr.

# Getting started

Source can be loaded via [npm](https://www.npmjs.com/package/i18next-xhr-backend), bower or [downloaded](https://github.com/i18next/i18next-xhr-backend/blob/master/i18nextXHRBackend.min.js) from this repo.

```
# npm package
$ npm install i18next-xhr-backend

# bower
$ bower install i18next-xhr-backend
```

Wiring up:

```js
import i18next from 'i18next';
import XHR from 'i18next-xhr-backend';

i18next
  .use(XHR)
  .init(i18nextOptions);
```

- As with all modules you can either pass the constructor function (class) to the i18next.use or a concrete instance.
- If you don't use a module loader it will be added to `window.i18nextXHRBackend`

## Backend Options

```js
{
  // path where resources get loaded from
  loadPath: '/locales/{{lng}}/{{ns}}.json',

  // path to post missing resources
  addPath: 'locales/add/{{lng}}/{{ns}}',

  // your backend server supports multiloading
  // /locales/resources.json?lng=de+en&ns=ns1+ns2
  allowMultiLoading: false,

  // parse data after it has been fetched
  // in example use https://www.npmjs.com/package/json5
  // here it removes the letter a from the json (bad idea)
  parse: function(data) { return data.replace(/a/g, ''); },
  
  // allow cross domain requests
  crossDomain: false,

  // define a custom xhr function
  // can be set to support XDomainRequest in IE 8 and 9
  xhr: function(url, callback, data) { }
}
```

Options can be passed in:

**preferred** - by setting options.backend in i18next.init:

```js
import i18next from 'i18next';
import XHR from 'i18next-xhr-backend';

i18next
  .use(XHR)
  .init({
    backend: options
  });
```

on construction:

```js
  import XHR from 'i18next-xhr-backend';
  const xhr = new XHR(null, options);
```

via calling init:

```js
  import XHR from 'i18next-xhr-backend';
  const xhr = new XHR();
  xhr.init(options);
```

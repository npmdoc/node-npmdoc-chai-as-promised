# api documentation for  [chai-as-promised (v6.0.0)](https://github.com/domenic/chai-as-promised#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-chai-as-promised.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-chai-as-promised) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-chai-as-promised.svg)](https://travis-ci.org/npmdoc/node-npmdoc-chai-as-promised)
#### Extends Chai with assertions about promises.

[![NPM](https://nodei.co/npm/chai-as-promised.png?downloads=true)](https://www.npmjs.com/package/chai-as-promised)

[![apidoc](https://npmdoc.github.io/node-npmdoc-chai-as-promised/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-chai-as-promised_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-chai-as-promised/build..beta..travis-ci.org/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-chai-as-promised/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-chai-as-promised/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Domenic Denicola",
        "email": "d@domenic.me",
        "url": "https://domenic.me"
    },
    "bugs": {
        "url": "https://github.com/domenic/chai-as-promised/issues"
    },
    "dependencies": {
        "check-error": "^1.0.2"
    },
    "description": "Extends Chai with assertions about promises.",
    "devDependencies": {
        "chai": "^3.0.0",
        "coffee-script": "1.10.0",
        "ecstatic": "^1.3.1",
        "glob": "^6.0.1",
        "istanbul": "0.4.1",
        "jshint": "^2.8.0",
        "mocha": "^2.3.4",
        "opener": "^1.4.1",
        "q": "^1.4.1",
        "underscore": "1.8.3"
    },
    "directories": {},
    "dist": {
        "shasum": "1a02a433a6f24dafac63b9c96fa1684db1aa8da6",
        "tarball": "https://registry.npmjs.org/chai-as-promised/-/chai-as-promised-6.0.0.tgz"
    },
    "files": [
        "lib"
    ],
    "gitHead": "b2cfbdc71360dad1faaa29f64bcc8ba54819084e",
    "homepage": "https://github.com/domenic/chai-as-promised#readme",
    "keywords": [
        "chai",
        "chai-plugin",
        "browser",
        "async",
        "testing",
        "assertions",
        "promises",
        "promises-aplus"
    ],
    "license": "WTFPL",
    "main": "./lib/chai-as-promised.js",
    "maintainers": [
        {
            "name": "domenic",
            "email": "domenic@domenicdenicola.com"
        }
    ],
    "name": "chai-as-promised",
    "optionalDependencies": {},
    "peerDependencies": {
        "chai": ">= 2.1.2 < 4"
    },
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/domenic/chai-as-promised.git"
    },
    "scripts": {
        "cover": "istanbul cover node_modules/mocha/bin/_mocha && opener ./coverage/lcov-report/lib/chai-as-promised.js.html",
        "lint": "jshint ./lib",
        "test": "npm run test-plugin && npm run test-intercompatibility",
        "test-intercompatibility": "mocha test-intercompatibility --opts test-intercompatibility/mocha.opts",
        "test-plugin": "mocha"
    },
    "version": "6.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module chai-as-promised](#apidoc.module.chai-as-promised)
1.  [function <span class="apidocSignatureSpan">chai-as-promised.</span>transferPromiseness (assertion, promise)](#apidoc.element.chai-as-promised.transferPromiseness)
1.  [function <span class="apidocSignatureSpan">chai-as-promised.</span>transformAsserterArgs (values)](#apidoc.element.chai-as-promised.transformAsserterArgs)



# <a name="apidoc.module.chai-as-promised"></a>[module chai-as-promised](#apidoc.module.chai-as-promised)

#### <a name="apidoc.element.chai-as-promised.transferPromiseness"></a>[function <span class="apidocSignatureSpan">chai-as-promised.</span>transferPromiseness (assertion, promise)](#apidoc.element.chai-as-promised.transferPromiseness)
- description and source-code
```javascript
transferPromiseness = function (assertion, promise) {
    assertion.then = promise.then.bind(promise);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.chai-as-promised.transformAsserterArgs"></a>[function <span class="apidocSignatureSpan">chai-as-promised.</span>transformAsserterArgs (values)](#apidoc.element.chai-as-promised.transformAsserterArgs)
- description and source-code
```javascript
transformAsserterArgs = function (values) {
    return values;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

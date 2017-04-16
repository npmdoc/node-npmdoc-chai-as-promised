# api documentation for  [chai-as-promised (v6.0.0)](https://github.com/domenic/chai-as-promised#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-chai-as-promised.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-chai-as-promised) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-chai-as-promised.svg)](https://travis-ci.org/npmdoc/node-npmdoc-chai-as-promised)
#### Extends Chai with assertions about promises.

[![NPM](https://nodei.co/npm/chai-as-promised.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/chai-as-promised)

[![apidoc](https://npmdoc.github.io/node-npmdoc-chai-as-promised/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-chai-as-promised/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-chai-as-promised/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-chai-as-promised/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Domenic Denicola",
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
            "name": "domenic"
        }
    ],
    "name": "chai-as-promised",
    "optionalDependencies": {},
    "peerDependencies": {
        "chai": ">= 2.1.2 < 4"
    },
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
1.  [function <span class="apidocSignatureSpan"></span>chai-as-promised (chai, utils)](#apidoc.element.chai-as-promised.chai-as-promised)
1.  [function <span class="apidocSignatureSpan">chai-as-promised.</span>chai_as_promised (chai, utils)](#apidoc.element.chai-as-promised.chai_as_promised)
1.  [function <span class="apidocSignatureSpan">chai-as-promised.</span>toString ()](#apidoc.element.chai-as-promised.toString)
1.  [function <span class="apidocSignatureSpan">chai-as-promised.</span>transferPromiseness (assertion, promise)](#apidoc.element.chai-as-promised.transferPromiseness)
1.  [function <span class="apidocSignatureSpan">chai-as-promised.</span>transformAsserterArgs (values)](#apidoc.element.chai-as-promised.transformAsserterArgs)

#### [module chai-as-promised.chai_as_promised](#apidoc.module.chai-as-promised.chai_as_promised)
1.  [function <span class="apidocSignatureSpan">chai-as-promised.</span>chai_as_promised (chai, utils)](#apidoc.element.chai-as-promised.chai_as_promised.chai_as_promised)
1.  [function <span class="apidocSignatureSpan">chai-as-promised.chai_as_promised.</span>transferPromiseness (assertion, promise)](#apidoc.element.chai-as-promised.chai_as_promised.transferPromiseness)
1.  [function <span class="apidocSignatureSpan">chai-as-promised.chai_as_promised.</span>transformAsserterArgs (values)](#apidoc.element.chai-as-promised.chai_as_promised.transformAsserterArgs)



# <a name="apidoc.module.chai-as-promised"></a>[module chai-as-promised](#apidoc.module.chai-as-promised)

#### <a name="apidoc.element.chai-as-promised.chai-as-promised"></a>[function <span class="apidocSignatureSpan"></span>chai-as-promised (chai, utils)](#apidoc.element.chai-as-promised.chai-as-promised)
- description and source-code
```javascript
chai-as-promised = function (chai, utils) {
    var Assertion = chai.Assertion;
    var assert = chai.assert;

    // If we are using a version of Chai that has checkError on it,
    // we want to use that version to be consistent. Otherwise, we use
    // what was passed to the factory.
    if (utils.checkError) {
        checkError = utils.checkError;
    }

    function isLegacyJQueryPromise(thenable) {
        // jQuery promises are Promises/A+-compatible since 3.0.0. jQuery 3.0.0 is also the first version
        // to define the catch method.
        return typeof thenable.catch !== "function" &&
               typeof thenable.always === "function" &&
               typeof thenable.done === "function" &&
               typeof thenable.fail === "function" &&
               typeof thenable.pipe === "function" &&
               typeof thenable.progress === "function" &&
               typeof thenable.state === "function";
    }

    function assertIsAboutPromise(assertion) {
        if (typeof assertion._obj.then !== "function") {
            throw new TypeError(utils.inspect(assertion._obj) + " is not a thenable.");
        }
        if (isLegacyJQueryPromise(assertion._obj)) {
            throw new TypeError("Chai as Promised is incompatible with thenables of jQuery<3.0.0, sorry! Please " +
                                "upgrade jQuery or use another Promises/A+ compatible library (see " +
                                "http://promisesaplus.com/).");
        }
    }

    function method(name, asserter) {
        utils.addMethod(Assertion.prototype, name, function () {
            assertIsAboutPromise(this);
            return asserter.apply(this, arguments);
        });
    }

    function property(name, asserter) {
        utils.addProperty(Assertion.prototype, name, function () {
            assertIsAboutPromise(this);
            return asserter.apply(this, arguments);
        });
    }

    function doNotify(promise, done) {
        promise.then(function () { done(); }, done);
    }

    // These are for clarity and to bypass Chai refusing to allow 'undefined' as actual when used with 'assert'.
    function assertIfNegated(assertion, message, extra) {
        assertion.assert(true, null, message, extra.expected, extra.actual);
    }

    function assertIfNotNegated(assertion, message, extra) {
        assertion.assert(false, message, null, extra.expected, extra.actual);
    }

    function getBasePromise(assertion) {
        // We need to chain subsequent asserters on top of ones in the chain already (consider
        // 'eventually.have.property("foo").that.equals("bar")'), only running them after the existing ones pass.
        // So the first base-promise is 'assertion._obj', but after that we use the assertions themselves, i.e.
        // previously derived promises, to chain off of.
        return typeof assertion.then === "function" ? assertion : assertion._obj;
    }

    function getReasonName(reason) {
        return (reason instanceof Error) ? reason.toString() : checkError.getConstructorName(reason);
    }

    // Grab these first, before we modify 'Assertion.prototype'.

    var propertyNames = Object.getOwnPropertyNames(Assertion.prototype);

    var propertyDescs = {};
    propertyNames.forEach(function (name) {
        propertyDescs[name] = Object.getOwnPropertyDescriptor(Assertion.prototype, name);
    });

    property("fulfilled", function () {
        var that = this;
        var derivedPromise = getBasePromise(that).then(
            function (value) {
                assertIfNegated(that,
                                "expected promise not to be fulfilled but it was fulfilled with #{act}",
                                { actual: value });
                return value;
            },
            function (reason) {
                assertIfNotNegated(that,
                                   "expected promise to be fulfilled but it was rejected with #{act}",
                                   { actual: getReasonName(reason) });
                return reason;
            }
        );

        module.export ...
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.chai-as-promised.chai_as_promised"></a>[function <span class="apidocSignatureSpan">chai-as-promised.</span>chai_as_promised (chai, utils)](#apidoc.element.chai-as-promised.chai_as_promised)
- description and source-code
```javascript
chai_as_promised = function (chai, utils) {
    var Assertion = chai.Assertion;
    var assert = chai.assert;

    // If we are using a version of Chai that has checkError on it,
    // we want to use that version to be consistent. Otherwise, we use
    // what was passed to the factory.
    if (utils.checkError) {
        checkError = utils.checkError;
    }

    function isLegacyJQueryPromise(thenable) {
        // jQuery promises are Promises/A+-compatible since 3.0.0. jQuery 3.0.0 is also the first version
        // to define the catch method.
        return typeof thenable.catch !== "function" &&
               typeof thenable.always === "function" &&
               typeof thenable.done === "function" &&
               typeof thenable.fail === "function" &&
               typeof thenable.pipe === "function" &&
               typeof thenable.progress === "function" &&
               typeof thenable.state === "function";
    }

    function assertIsAboutPromise(assertion) {
        if (typeof assertion._obj.then !== "function") {
            throw new TypeError(utils.inspect(assertion._obj) + " is not a thenable.");
        }
        if (isLegacyJQueryPromise(assertion._obj)) {
            throw new TypeError("Chai as Promised is incompatible with thenables of jQuery<3.0.0, sorry! Please " +
                                "upgrade jQuery or use another Promises/A+ compatible library (see " +
                                "http://promisesaplus.com/).");
        }
    }

    function method(name, asserter) {
        utils.addMethod(Assertion.prototype, name, function () {
            assertIsAboutPromise(this);
            return asserter.apply(this, arguments);
        });
    }

    function property(name, asserter) {
        utils.addProperty(Assertion.prototype, name, function () {
            assertIsAboutPromise(this);
            return asserter.apply(this, arguments);
        });
    }

    function doNotify(promise, done) {
        promise.then(function () { done(); }, done);
    }

    // These are for clarity and to bypass Chai refusing to allow 'undefined' as actual when used with 'assert'.
    function assertIfNegated(assertion, message, extra) {
        assertion.assert(true, null, message, extra.expected, extra.actual);
    }

    function assertIfNotNegated(assertion, message, extra) {
        assertion.assert(false, message, null, extra.expected, extra.actual);
    }

    function getBasePromise(assertion) {
        // We need to chain subsequent asserters on top of ones in the chain already (consider
        // 'eventually.have.property("foo").that.equals("bar")'), only running them after the existing ones pass.
        // So the first base-promise is 'assertion._obj', but after that we use the assertions themselves, i.e.
        // previously derived promises, to chain off of.
        return typeof assertion.then === "function" ? assertion : assertion._obj;
    }

    function getReasonName(reason) {
        return (reason instanceof Error) ? reason.toString() : checkError.getConstructorName(reason);
    }

    // Grab these first, before we modify 'Assertion.prototype'.

    var propertyNames = Object.getOwnPropertyNames(Assertion.prototype);

    var propertyDescs = {};
    propertyNames.forEach(function (name) {
        propertyDescs[name] = Object.getOwnPropertyDescriptor(Assertion.prototype, name);
    });

    property("fulfilled", function () {
        var that = this;
        var derivedPromise = getBasePromise(that).then(
            function (value) {
                assertIfNegated(that,
                                "expected promise not to be fulfilled but it was fulfilled with #{act}",
                                { actual: value });
                return value;
            },
            function (reason) {
                assertIfNotNegated(that,
                                   "expected promise to be fulfilled but it was rejected with #{act}",
                                   { actual: getReasonName(reason) });
                return reason;
            }
        );

        module.export ...
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.chai-as-promised.toString"></a>[function <span class="apidocSignatureSpan">chai-as-promised.</span>toString ()](#apidoc.element.chai-as-promised.toString)
- description and source-code
```javascript
toString = function () {
    return toString;
}
```
- example usage
```shell
n/a
```

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



# <a name="apidoc.module.chai-as-promised.chai_as_promised"></a>[module chai-as-promised.chai_as_promised](#apidoc.module.chai-as-promised.chai_as_promised)

#### <a name="apidoc.element.chai-as-promised.chai_as_promised.chai_as_promised"></a>[function <span class="apidocSignatureSpan">chai-as-promised.</span>chai_as_promised (chai, utils)](#apidoc.element.chai-as-promised.chai_as_promised.chai_as_promised)
- description and source-code
```javascript
chai_as_promised = function (chai, utils) {
    var Assertion = chai.Assertion;
    var assert = chai.assert;

    // If we are using a version of Chai that has checkError on it,
    // we want to use that version to be consistent. Otherwise, we use
    // what was passed to the factory.
    if (utils.checkError) {
        checkError = utils.checkError;
    }

    function isLegacyJQueryPromise(thenable) {
        // jQuery promises are Promises/A+-compatible since 3.0.0. jQuery 3.0.0 is also the first version
        // to define the catch method.
        return typeof thenable.catch !== "function" &&
               typeof thenable.always === "function" &&
               typeof thenable.done === "function" &&
               typeof thenable.fail === "function" &&
               typeof thenable.pipe === "function" &&
               typeof thenable.progress === "function" &&
               typeof thenable.state === "function";
    }

    function assertIsAboutPromise(assertion) {
        if (typeof assertion._obj.then !== "function") {
            throw new TypeError(utils.inspect(assertion._obj) + " is not a thenable.");
        }
        if (isLegacyJQueryPromise(assertion._obj)) {
            throw new TypeError("Chai as Promised is incompatible with thenables of jQuery<3.0.0, sorry! Please " +
                                "upgrade jQuery or use another Promises/A+ compatible library (see " +
                                "http://promisesaplus.com/).");
        }
    }

    function method(name, asserter) {
        utils.addMethod(Assertion.prototype, name, function () {
            assertIsAboutPromise(this);
            return asserter.apply(this, arguments);
        });
    }

    function property(name, asserter) {
        utils.addProperty(Assertion.prototype, name, function () {
            assertIsAboutPromise(this);
            return asserter.apply(this, arguments);
        });
    }

    function doNotify(promise, done) {
        promise.then(function () { done(); }, done);
    }

    // These are for clarity and to bypass Chai refusing to allow 'undefined' as actual when used with 'assert'.
    function assertIfNegated(assertion, message, extra) {
        assertion.assert(true, null, message, extra.expected, extra.actual);
    }

    function assertIfNotNegated(assertion, message, extra) {
        assertion.assert(false, message, null, extra.expected, extra.actual);
    }

    function getBasePromise(assertion) {
        // We need to chain subsequent asserters on top of ones in the chain already (consider
        // 'eventually.have.property("foo").that.equals("bar")'), only running them after the existing ones pass.
        // So the first base-promise is 'assertion._obj', but after that we use the assertions themselves, i.e.
        // previously derived promises, to chain off of.
        return typeof assertion.then === "function" ? assertion : assertion._obj;
    }

    function getReasonName(reason) {
        return (reason instanceof Error) ? reason.toString() : checkError.getConstructorName(reason);
    }

    // Grab these first, before we modify 'Assertion.prototype'.

    var propertyNames = Object.getOwnPropertyNames(Assertion.prototype);

    var propertyDescs = {};
    propertyNames.forEach(function (name) {
        propertyDescs[name] = Object.getOwnPropertyDescriptor(Assertion.prototype, name);
    });

    property("fulfilled", function () {
        var that = this;
        var derivedPromise = getBasePromise(that).then(
            function (value) {
                assertIfNegated(that,
                                "expected promise not to be fulfilled but it was fulfilled with #{act}",
                                { actual: value });
                return value;
            },
            function (reason) {
                assertIfNotNegated(that,
                                   "expected promise to be fulfilled but it was rejected with #{act}",
                                   { actual: getReasonName(reason) });
                return reason;
            }
        );

        module.export ...
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.chai-as-promised.chai_as_promised.transferPromiseness"></a>[function <span class="apidocSignatureSpan">chai-as-promised.chai_as_promised.</span>transferPromiseness (assertion, promise)](#apidoc.element.chai-as-promised.chai_as_promised.transferPromiseness)
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

#### <a name="apidoc.element.chai-as-promised.chai_as_promised.transformAsserterArgs"></a>[function <span class="apidocSignatureSpan">chai-as-promised.chai_as_promised.</span>transformAsserterArgs (values)](#apidoc.element.chai-as-promised.chai_as_promised.transformAsserterArgs)
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

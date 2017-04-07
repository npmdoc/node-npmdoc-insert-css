# api documentation for  [insert-css (v2.0.0)](https://github.com/substack/insert-css)  [![npm package](https://img.shields.io/npm/v/npmdoc-insert-css.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-insert-css) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-insert-css.svg)](https://travis-ci.org/npmdoc/node-npmdoc-insert-css)
#### insert a string of css into the <head>

[![NPM](https://nodei.co/npm/insert-css.png?downloads=true)](https://www.npmjs.com/package/insert-css)

[![apidoc](https://npmdoc.github.io/node-npmdoc-insert-css/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-insert-css_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-insert-css/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-insert-css/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-insert-css/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "James Halliday",
        "email": "mail@substack.net",
        "url": "http://substack.net"
    },
    "bugs": {
        "url": "https://github.com/substack/insert-css/issues"
    },
    "dependencies": {},
    "description": "insert a string of css into the <head>",
    "devDependencies": {
        "browserify": "^13.0.1",
        "budo": "^8.3.0",
        "computed-style": "^0.3.0",
        "dom-event": "^1.0.0",
        "tape": "^4.6.0",
        "tape-run": "^2.1.4"
    },
    "directories": {},
    "dist": {
        "shasum": "eb5d1097b7542f4c79ea3060d3aee07d053880f4",
        "tarball": "https://registry.npmjs.org/insert-css/-/insert-css-2.0.0.tgz"
    },
    "gitHead": "d13317dfd48d0ed7272526d8a58058ad719f3c91",
    "homepage": "https://github.com/substack/insert-css",
    "keywords": [
        "css",
        "insert",
        "dom",
        "browser",
        "browserify",
        "inject",
        "styles",
        "stylesheet",
        "style",
        "html",
        "head",
        "link"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "jonaskello",
            "email": "jonas.kello@gmail.com"
        },
        {
            "name": "substack",
            "email": "substack@gmail.com"
        },
        {
            "name": "vvo",
            "email": "vincent.voyer@gmail.com"
        }
    ],
    "name": "insert-css",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/substack/insert-css.git"
    },
    "scripts": {
        "example": "budo example.js",
        "test": "browserify test.js | tape-run"
    },
    "testling": {
        "files": "test.js",
        "browsers": [
            "ie/6..latest",
            "chrome/20..latest",
            "firefox/10..latest",
            "safari/latest",
            "opera/11.0..latest",
            "iphone/6",
            "ipad/6"
        ]
    },
    "version": "2.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module insert-css](#apidoc.module.insert-css)
1.  [function <span class="apidocSignatureSpan">insert-css.</span>insertCss (css, options)](#apidoc.element.insert-css.insertCss)



# <a name="apidoc.module.insert-css"></a>[module insert-css](#apidoc.module.insert-css)

#### <a name="apidoc.element.insert-css.insertCss"></a>[function <span class="apidocSignatureSpan">insert-css.</span>insertCss (css, options)](#apidoc.element.insert-css.insertCss)
- description and source-code
```javascript
function insertCss(css, options) {
    options = options || {};

    if (css === undefined) {
        throw new Error(usage);
    }

    var position = options.prepend === true ? 'prepend' : 'append';
    var container = options.container !== undefined ? options.container : document.querySelector('head');
    var containerId = containers.indexOf(container);

    // first time we see this container, create the necessary entries
    if (containerId === -1) {
        containerId = containers.push(container) - 1;
        styleElements[containerId] = {};
    }

    // try to get the correponding container + position styleElement, create it otherwise
    var styleElement;

    if (styleElements[containerId] !== undefined && styleElements[containerId][position] !== undefined) {
        styleElement = styleElements[containerId][position];
    } else {
        styleElement = styleElements[containerId][position] = createStyleElement();

        if (position === 'prepend') {
            container.insertBefore(styleElement, container.childNodes[0]);
        } else {
            container.appendChild(styleElement);
        }
    }

    // strip potential UTF-8 BOM if css was read from a file
    if (css.charCodeAt(0) === 0xFEFF) { css = css.substr(1, css.length); }

    // actually add the stylesheet
    if (styleElement.styleSheet) {
        styleElement.styleSheet.cssText += css
    } else {
        styleElement.textContent += css;
    }

    return styleElement;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

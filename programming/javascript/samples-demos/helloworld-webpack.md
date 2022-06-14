---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - WebPack Sample
description: Dynamsoft Barcode Reader SDK for JavaScript using WebPack
keywords: javascript, js, barcode, vanilla, webpack
noTitleIndex: true
breadcrumbText: WebPack
permalink: /programming/javascript/samples-demos/helloworld-webpack.html
---

# JavaScript Hello World Sample - WebPack

[Webpack](https://webpack.js.org/) is a static module bundler for modern JavaScript applications. While webpack is used by almost all the popular JavaScript frameworks as the basis of their build system, it can also be used alone. In this article, we will take a look at how to use the Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") with just webpack as shown in the code:

* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main/1.hello-world/12.read-video-webpack">Read Barcodes from Camera - Webpack - Source Code</a>

## Create a simple application with Webpack

### Create a configuration file

Create a file with the name webpack.config.js and input the following content

```javascript
const path = require('path');

module.exports = {
    mode: 'development',
    entry: './src/index.js',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js',
    },
};
```

The above example code tells webpack to do the following things

1. Find the file index.js in the /src/ directory which is relative to the current running path (absolute path on the disk)
2. Bundle the relative JavaScript files into a single file bundle.js, then output it under the /dist/ directory.

### Create the source file

Create a directory /src/, then create a index.js file under it with the following content

```javascript
import BarcodeScanner from "dynamsoft-javascript-barcode";
BarcodeScanner.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
BarcodeScanner.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.0.2/dist/";

let pScanner = null;
if (document.getElementById('readBarcode')) {
    document.getElementById('readBarcode').onclick = async function() {
        try {
            let scanner = await (pScanner = pScanner || BarcodeScanner.createInstance());
            scanner.onFrameRead = results => {
                console.log("Barcodes on one frame:");
                for (let result of results) {
                    console.log(result.barcodeFormatString + ": " + result.barcodeText);
                }
            };
            scanner.onUniqueRead = (txt, result) => {
                alert(txt);
                console.log("Unique Code Found: " + result);
            }
            await scanner.show();
        } catch (ex) {
            alert(ex.message);
            throw ex;
        }
    };
}
```

The example code above loads the library and creates a BarcodeScanner object to do barcode scanning. Note that the function is registered to a button with the ID "readBarcode" which exists on the page we create in the next step.

### Create the web page

Create a file with the name index.html and put it together with webpack.config.js. The content is as follows:

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
</head>

<body>
    <button id="readBarcode">show scanner</button>
    <script src="./dist/bundle.js"></script>
</body>

</html>
```

Note that the page is looking for the bundle.js file which is the output from webpack.

### Add dependencies and compile scripts

Now we have all the code we need except for the library and the bundler which is webpack. We can add a package.json file with the following content

```json
{
    "name": "helloworld-webpack",
    "version": "1.0.0",
    "description": "Use the Dynamsoft Barcode Reader JavaScript SDK with just webpack",
    "scripts": {
        "build": "webpack --config webpack.config.js",
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "author": "Dynamsoft Team",
    "devDependencies": {
        "webpack": "5.52.1",
        "webpack-cli": "4.8.0"
    },
    "dependencies": {
        "dynamsoft-javascript-barcode": "9.0.2"
    }
}
```

Run the following script to install the dependencies:

```cmd
npm install
```

### Compile and run

The package configuration file in the last step already includes the compile script, we can build the application like this:

```cmd
npm run-script build
```

The output file "bundle.js" will appear under the /dist/ directory.

### Test the sample

Open index.html, click "show scanner" and you will soon get a working page that scans barcodes.

## Extra notes

### Load the library locally

The example code above uses the library via a CDN, you can also use a local copy of the library by using "copy-webpack-plugin":

```cmd
npm install copy-webpack-plugin
```

```javascript
const path = require('path');
const CopyPlugin = require('copy-webpack-plugin'); // For copying local resources

module.exports = {
    mode: 'development',
    entry: './src/index.js',
    plugins: [
        new CopyPlugin({
            patterns: [
                {
                    from: './node_modules/dynamsoft-javascript-barcode/dist',
                    to: path.resolve(__dirname, 'dist'),
                }
            ]
        }),
    ],
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js',
    },
};
```

Don't forget to change `engineResourcePath` in index.js:

```javascript
BarcodeScanner.engineResourcePath = './dist/'
```

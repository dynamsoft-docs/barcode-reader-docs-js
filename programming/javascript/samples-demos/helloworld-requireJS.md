---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - RequireJS Sample
description: Dynamsoft Barcode Reader SDK for JavaScript using RequireJS
keywords: javascript, js, barcode, vanilla, requirejs
noTitleIndex: true
breadcrumbText: RequireJS
permalink: /programming/javascript/samples-demos/helloworld-requireJS.html
---

# JavaScript Hello World Sample - RequireJS

[RequireJS](https://requirejs.org/) is a JavaScript file and module loader. In this article, we will take a look at how to use the Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") with RequireJS as shown in the code:

* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/main/1.hello-world/11.read-video-requirejs.html">Read Barcodes from Camera - RequireJS - Source Code</a>

## Create a simple page for barcode reading with RequireJS

### Include RequireJS on the page

The first step is to load "require.js" on the page:

```html
<script src="https://cdn.jsdelivr.net/npm/requirejs@2.3.6/require.js"></script>
```

### Use RequireJS to load the library

Once RequireJS is enalbed, we can use the API `requirejs` to load the library from a CDN:

```javascript
requirejs(['https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.0.2/dist/dbr.js'],
    function({
        BarcodeScanner
    }) {});
```

As shown above, the `requirejs` method loads the library and imports two key objects to be used in the context. We use `DBR` to set up the library and then use `BarcodeScanner` to read barcodes from a video input.

```javascript
BarcodeScanner.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
BarcodeScanner.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.0.2/dist/";
let pScanner = null;
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
```

You can try the sample code from:

* <a target = "_blank" href="https://demo.dynamsoft.com/samples/dbr/js/1.hello-world/11.read-video-requirejs.html">Read Barcodes from Camera - RequireJS - Demo</a>

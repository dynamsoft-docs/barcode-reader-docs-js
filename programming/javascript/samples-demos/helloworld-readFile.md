---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - Read An Image Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - Read An Image
keywords: javascript, js, barcode, vanilla, image
noTitleIndex: true
breadcrumbText: Read An Image
permalink: /programming/javascript/samples-demos/helloworld-readFile.html
---

# JavaScript Hello World Sample - Read An Image

In most cases, users of Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") reads barcodes from a video input. In this article, we will discuss an uncommon usage of the library: reading barcodes from existing images.

## Official Sample

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/2.read-an-image.html">Read Barcodes from An Existing Image - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/main/1.hello-world/2.read-an-image.html">Read Barcodes from An Existing Image - Source Code</a>

## Preparation

In this article, we'll make use of the library through the `jsDelivr` CDN. Make sure you can access this file "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.0.2/dist/dbr.js".

## Create the sample page

* Create an empty web page and name it "read-an-image.html" with the following code:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>Dynamsoft Barcode Reader Sample - Read an Image</title>
</head>

<body>
    <script></script>
</body>

</html>
```

* Add reference to the library in the page "head".

```html
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.0.2/dist/dbr.js"></script>
```

* In the page "body", add an input for image selecting and a div for displaying the barcode results.

```html
<input id="ipt-file" type="file" accept="image/png,image/jpeg,image/bmp,image/gif">
<div id="results"></div>
```

* Add an event listner for the file input, then add barcode reading code in the callback.

```javascript
let pReader = null;
Dynamsoft.DBR.BarcodeReader.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
document.getElementById('ipt-file').addEventListener('change', async function() {
    try {
        let resDIV = document.getElementById('results');
        let reader = await (pReader = pReader || Dynamsoft.DBR.BarcodeReader.createInstance());
        for (let i = 0; i < this.files.length; ++i) {
            // Actually there will only be one file here (no 'multiple' attribute)
            let file = this.files[i];
            // Decode the file
            let results = await reader.decode(file);
            if (results.length === 0) {
                resDIV.innerHTML = "No Barcode Found!";
                return;
            }
            var info = "";
            for (let result of results) {
                info += "<p>" + result.barcodeFormatString + ": " + result.barcodeText + "</p>";
            }
            resDIV.innerHTML = info;
        }
    } catch (ex) {
        alert(ex.message);
    }
});
```

> NOTE
>  
> * An instance of the library is created when an image is selected for the first time.
> * The method `decode()` takes the file as the input, reads it and returns the results.

In your application, the input may not be a file, the method `decode()` can handle the following types of input: `Blob`, `Buffer`, `ArrayBuffer`, `Uint8Array`, `Uint8ClampedArray`, `HTMLImageElement`, `HTMLCanvasElement`, `HTMLVideoElement`, `string`.



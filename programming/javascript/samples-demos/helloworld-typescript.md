---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - Minimal Code Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - Minimal Code
keywords: javascript, js, barcode, vanilla
noTitleIndex: true
breadcrumbText: Minimal Code
---

# JavaScript Hello World Sample - TypeScript

[TypeScript](https://www.typescriptlang.org/) is JavaScript with syntax for types. In this article, we will take a look at how to use the Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") with TypeScript as show in the code:

* <a target = "_blank" href="https://github.com/Dynamsoft/dbr-browser-samples/blob/master/1.hello-world/">Read Barcodes from Camera - TypeScript - Source Code</a>

## Preparation

Make sure you have [node](https://nodejs.org/) installed. `node 14.16.0` is used in the example below.

## Start to Implement

### Install the dependencies

Create a folder with the name read-video-typescript, inside the folder, create a package.json file with the following content:

```json
{
  "name": "read-video-typescript",
  "version": "1.0.0",
  "dependencies": {
    "dynamsoft-javascript-barcode": "8.6.1",
    "@types/node": "16.9.1",
    "typescript": "4.4.3"
  }
}
```

Then, install the independencies with:

```shell
npm install
```

### Create a simple page for barcode reading with TypeScript

First, create a script.ts file with the following content:

```typescript
/// <reference path="./node_modules/dynamsoft-javascript-barcode/dist/dbr.reference.d.ts" />

Dynamsoft.DBR.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.6.1/dist/";

let pScanner: Promise<BarcodeScanner> = null;

// decode video from camera
(document.getElementById('btn-show-scanner') as HTMLButtonElement).addEventListener('click', async () => {
    try {
        let scanner = await (pScanner = pScanner || Dynamsoft.DBR.BarcodeScanner.createInstance());
        scanner.onFrameRead = results => {
            if (results.length) {
                console.log(results);
            }
        };
        scanner.onUnduplicatedRead = (txt, result) => {
            if (txt.indexOf("Attention(exceptionCode") !== -1) {
                alert((<any>result).exception.message);
            } else
                alert(result.barcodeFormatString + ': ' + txt);
        };
        await scanner.show();
    } catch (ex) {
        alert(ex.message);
        throw ex;
    }
});
```

Next, create an index.html file:

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
</head>

<body>
    <button id="btn-show-scanner">show scanner</button>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.6.1/dist/dbr.js"
        data-productKeys="PRODUCT-KEYS"></script>
    <script src="script.js"></script>
</body>

</html>
```

Notice that the page looks for a script.js file instead of script.ts. Therefore, we must compile the typescript file first:

```shell
npx tsc ./script.ts --lib es2015 --lib dom
```

After script.js is generated, we can open index.html to test it.

## Conclusion

We demonstrated how to use the library with TypeScript in this article. Although the actual script running on the page is still JavaScript, you can choose to use TypeScript which is more reliable and easier to refactor.
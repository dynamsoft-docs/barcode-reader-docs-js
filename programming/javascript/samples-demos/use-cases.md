---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - Use Case Samples
description: Dynamsoft Barcode Reader SDK for JavaScript - Use Cases
keywords: javascript, js, barcode, use-case
noTitleIndex: true
breadcrumbText: Use Cases
permalink: /programming/javascript/samples-demos/use-cases.html
---

# JavaScript UI Use Case Samples

In this article, we'll take a look at the official samples which demonstrates typical use cases of Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library").

## Read Barcodes and Fill Form Fields

It's difficult to type long text on mobile devices, but if that text is encoded in a barcode, we can use the library to read the barcode and automatically enter the text.

The following code shows how to automatically invoke the library to read a barcode and fill an input box.

```html
<input id="input-to-fill" type="text" readonly="true" placeholder="Barcode Result">
```

```javascript
let scanner = null;
Dynamsoft.DBR.BarcodeReader.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
(async function () {
    document.getElementById("input-to-fill").addEventListener('click', async function () {
        try {
            scanner = scanner || await Dynamsoft.DBR.BarcodeScanner.createInstance();
            scanner.onUniqueRead = (txt, result) => {
                this.value = result.barcodeText;
                scanner.hide();
            };
            await scanner.show();
        } catch (ex) {
            alert(ex.message);
            throw ex;
        }
    });
})();
```

The following official sample shows how to use the library to fill multiple fields for a form.

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/4.use-case/1.fill-a-form-with-barcode-reading.html">Read Barcodes and Fill Form Fields - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/main/4.use-case/1.fill-a-form-with-barcode-reading.html">Read Barcodes and Fill Form Fields - Source Code</a>

## Read the PDF417 Barcode on the Driver’s License

The PDF417 barcode on an AAMVA compatible driver's license contains a lot of information which is encoded following the DL/ID Card Design Standard. Together with a simple parse function, we can use the library to read and get the information to be used in our workflow.

The following official sample shows how to use the library to read a driver's license and extract its information.

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/4.use-case/2.read-a-drivers-license.html">Read the PDF417 Barcode on the Driver&apos;s License - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/main/4.use-case/2.read-a-drivers-license.html">Read the PDF417 Barcode on the Driver&apos;s License - Source Code</a>

Also see [Driver's License Scanner SDK for Mobile and Web](https://www.dynamsoft.com/use-cases/driver-license/).

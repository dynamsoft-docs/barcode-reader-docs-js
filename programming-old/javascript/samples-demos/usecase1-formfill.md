---
layout: default-layout
title: Fill a Form - Dynamsoft Barcode Reader JavaScript Edition
description: Fill a Form Use Cases of Dynamsoft Barcode Reader JavaScript Edition
keywords: javascript, js, barcode, use-case
noTitleIndex: true
breadcrumbText: Use Cases
permalink: /programming/javascript/samples-demos/usecase1-formfill.html
---

# Read Barcodes and Fill Form Fields

It's difficult to type long text on mobile devices, but if that text is encoded in a barcode, we can use the sdk to read the barcode and automatically enter the text.

The following code shows how to automatically invoke the sdk to read a barcode and fill an input box.

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

The following official sample shows how to use the sdk to fill multiple fields for a form.

* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/main/4.use-case/1.fill-a-form-with-barcode-reading.html">Read Barcodes and Fill Form Fields - Source Code</a>

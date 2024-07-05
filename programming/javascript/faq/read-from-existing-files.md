---
layout: default-layout
title: Can I read barcodes from existing files?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, existing file
description: Can I read barcodes from existing files?
needAutoGenerateSidebar: false
---

# Can I read barcodes from existing files?

[<< Back to FAQ index](index.md)

Yes, the JavaScript SDK supports reading from a file in local memory. This can be achieved via the `Caputure` class.

```javascript
let router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
let results = await router.capture("blob:https://demo.dynamsoft.com/afb84bd2-e8cb-4b96-92b6-36dc89783692", "ReadSingleBarcode");
let count = results.items.length;
for(let i = 0; i < count; i++) {
    //...
}

```

> [this article](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/single-image-processing.html?product=dbr&lang=javascript) shows how to read barcodes from existing images and a list of supported input types.

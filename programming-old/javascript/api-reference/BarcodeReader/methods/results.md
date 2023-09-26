---
layout: default-layout
title: BarcodeReader Result Methods - Dynamsoft Barcode Reader JavaScript Edition API
description: This page shows BarcodeReader Result methods of Dynamsoft Barcode Reader JavaScript SDK.
keywords: getIntermediateResults, result methods, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: false
permalink: /programming/javascript/api-reference/BarcodeReader/methods/results.html
---
<!--NOTE, This page is used until version 8.2.3-->

> This page is applicable to version 8.2.3

# Javascript API Reference - `BarcodeReader` Result Methods

| Method             | Description |
|----------------------|-------------|
| [`getIntermediateResults()`](#getintermediateresults) | Get intermediate results. |

---

## getIntermediateResults

Get the intermediate results containing the original image, colour clustered image, binarized image, contours, lines, etc.

The method is only supported in the **full feature edition**.

```javascript
getIntermediateResults() returns Promise
```

### Return Value

`Promise<any>`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

---
layout: default-layout
title: interface DecodedBarcodesResult - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface DecodedBarcodesResult in Dynamsoft DBR Module.
keywords: decoded barcode, barcode result, item, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DecodedBarcodesResult

Interface DecodedBarcodesResult represents information of decoded barcodes from an image.

```typescript
interface DecodedBarcodesResult extends CapturedResultBase{
    readonly barcodeResultItems: Array<BarcodeResultItem>;
}
```

## barcodeResultItems

An array of BarcodeResultItem objects, representing the list of decoded barcodes found in the image.

```typescript
readonly barcodeResultItems: Array<BarcodeResultItem>;
```

**See also**

* [BarcodeResultItem]({{ site.js_api }}interfaces/barcode-result-item.html)
* [CapturedResultBase]({{ site.dcvb_js_api }}core/basic-structures/captured-result-base.html)
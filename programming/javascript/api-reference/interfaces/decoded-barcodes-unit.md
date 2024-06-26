---
layout: default-layout
title: interface DecodedBarcodesUnit - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface DecodedBarcodesUnit in Dynamsoft Core Module.
keywords: decoded barcodes, Image unit, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DecodedBarcodesUnit

A unit that contains decoded barcode elements.

```typescript
interface DecodedBarcodesUnit extends Core.IntermediateResultUnit {
    decodedBarcodes: Array<DecodedBarcodeElement>;         
}
```
<!-- 
| Properties                          | Type                            |
| ----------------------------------- | ------------------------------- |
| [decodedBarcodes](#decodedbarcodes) | *Array\<DecodedBarcodeElement>* | -->

## decodedBarcodes

An array of `DecodedBarcodeElement` objects. Each `DecodedBarcodeElement` represents a successfully decoded barcode, including information such as the barcode format, text, and other relevant details.

```typescript
decodedBarcodes: Array<DecodedBarcodeElement>;
```

**See also**

* [DecodedBarcodeElement]({{ site.js_api }}interfaces/decoded-barcode-element.html)
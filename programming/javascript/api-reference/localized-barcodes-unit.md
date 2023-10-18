---
layout: default-layout
title: interface LocalizedBarcodesUnit - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface LocalizedBarcodesUnit in Dynamsoft Core Module.
keywords: localized barcodes, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# LocalizedBarcodesUnit

A unit of data related to localized barcodes within an image. It extends the `IntermediateResultUnit` interface.

## Definition

```typescript
interface LocalizedBarcodesUnit extends Core.IntermediateResultUnit {
    localizedBarcodes: Array<LocalizedBarcodeElement>;       
}
```

| Properties               | Type |
|----------------------|-------------|
| [`localizedBarcodes`](#localizedbarcodes) | *Array\<LocalizedBarcodeElement>* |

### localizedBarcodes

An array of `LocalizedBarcodeElement` objects. Each `LocalizedBarcodeElement` represents a barcode that has been successfully localized within the image.

```typescript
localizedBarcodes: Array<LocalizedBarcodeElement>;    
```

**See also**

* [LocalizedBarcodeElement]({{ site.js_api }}localized-barcode-element.html)
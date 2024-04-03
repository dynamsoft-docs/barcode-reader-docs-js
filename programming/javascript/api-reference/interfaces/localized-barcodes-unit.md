---
layout: default-layout
title: interface LocalizedBarcodesUnit - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface LocalizedBarcodesUnit in Dynamsoft Core Module.
keywords: localized barcodes, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# LocalizedBarcodesUnit

The `LocalizedBarcodesUnit` interface extends the `IntermediateResultUnit` interface and represents a unit that holds the localized barcode elements.

```typescript
interface LocalizedBarcodesUnit extends Core.IntermediateResultUnit {
    localizedBarcodes: Array<LocalizedBarcodeElement>;       
}
```
<!-- 
| Properties                              | Type                              |
| --------------------------------------- | --------------------------------- |
| [localizedBarcodes](#localizedbarcodes) | *Array\<LocalizedBarcodeElement>* | -->

## localizedBarcodes

An array of `LocalizedBarcodeElement` objects, each representing a localized barcode.

```typescript
localizedBarcodes: Array<LocalizedBarcodeElement>;    
```

**See also**

* [LocalizedBarcodeElement]({{ site.js_api }}interfaces/localized-barcode-element.html)
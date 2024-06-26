---
layout: default-layout
title: interface DeformationResistedBarcodeImageUnit - Dynamsoft Barcode Reader Module JS Edition API Reference
description: This page shows the JS edition of the interface DeformationResistedBarcodeImageUnit in Dynamsoft Barcode Reader Module.
keywords: deformation resisted, Image unit, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DeformationResistedBarcodeImageUnit

A unit that holds the deformation-resisted barcode which includes the corresponding image data, its location, and the barcode format.

```typescript
interface DeformationResistedBarcodeImageUnit extends Core.IntermediateResultUnit {
    deformationResistedBarcode: DeformationResistedBarcode;
}
```

## deformationResistedBarcode

The deformation-resisted barcode.

```typescript
deformationResistedBarcode: DeformationResistedBarcode;
```

**See also**

* [DeformationResistedBarcode](./deformation-resisted-barcode.md)
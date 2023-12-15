---
layout: default-layout
title: interface DeformationResistedBarcodeImageUnit - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface DeformationResistedBarcodeImageUnit in Dynamsoft Core Module.
keywords: deformation resisted, Image unit, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DeformationResistedBarcodeImageUnit

A unit of data that contains deformation resisted barcode image. It extends the `IntermediateResultUnit` interface.

## Definition

```typescript
interface DeformationResistedBarcodeImageUnit extends Core.IntermediateResultUnit {
    imageData: Core.DSImageData;
}
```

| Properties               | Type |
|----------------------|-------------|
| [imageData](#imagedata) | *Core.DSImageData* |

### imageData

The image data of the deformation resisted barcode.

```typescript
imageData: Core.DSImageData;
```

**See also**

* [DSImageData]({{ site.dcv_js_api }}core/basic-structures/ds-image-data.html)
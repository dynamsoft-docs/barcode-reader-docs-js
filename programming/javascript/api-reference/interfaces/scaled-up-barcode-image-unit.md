---
layout: default-layout
title: interface ScaledUpBarcodeImageUnit - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface ScaledUpBarcodeImageUnit in Dynamsoft Core Module.
keywords: scaled up, Image unit, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# ScaledUpBarcodeImageUnit

A unit of data that contains scaled up barcode image. It extends the `IntermediateResultUnit` interface.

```typescript
interface ScaledUpBarcodeImageUnit extends Core.IntermediateResultUnit {
    imageData: Core.DSImageData;
}
```

| Properties              | Type               |
| ----------------------- | ------------------ |
| [imageData](#imagedata) | *Core.DSImageData* |

## imageData

The image data of the scaled-up barcode.

```typescript
imageData: Core.DSImageData;   
```

**See also**

* [DSImageData]({{ site.dcv_js_api }}core/basic-structures/ds-image-data.html)
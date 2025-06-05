---
layout: default-layout
title: interface ScaleBarcodeImageUnit - Dynamsoft Barcode Reader Module JS Edition API Reference
description: This page shows the JS edition of the interface ScaleBarcodeImageUnit in Dynamsoft Barcode Reader Module.
keywords: scaled, Image unit, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# ScaleBarcodeImageUnit

A unit of data that contains scaled barcode image. It extends the `IntermediateResultUnit` interface.

```typescript
interface ScaleBarcodeImageUnit extends Core.IntermediateResultUnit {
    imageData: Core.DSImageData;
}
```
<!-- 
| Properties              | Type               |
| ----------------------- | ------------------ |
| [imageData](#imagedata) | *Core.DSImageData* | -->

## imageData

The image data of the scaled barcode.

```typescript
imageData: Core.DSImageData;   
```

**See also**

* [DSImageData]({{ site.dcvb_js_api }}core/basic-structures/ds-image-data.html)
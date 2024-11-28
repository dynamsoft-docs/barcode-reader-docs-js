---
layout: default-layout
title: interface ComplementedBarcodeImageUnit - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface ComplementedBarcodeImageUnit in Dynamsoft Core Module.
keywords: complemented, Image unit, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# ComplementedBarcodeImageUnit

A unit of data that contains complemented barcode image. It extends the `IntermediateResultUnit` interface.

```typescript
interface ComplementedBarcodeImageUnit extends Core.IntermediateResultUnit {
    imageData: Core.DSImageData;
    location: Core.Quadrilateral;
}
```
<!-- 
| Properties              | Type                 |
| ----------------------- | -------------------- |
| [imageData](#imagedata) | *Core.DSImageData*   |
| [location](#location)   | *Core.Quadrilateral* | -->

## imageData

The image data of the complemented barcode.

```typescript
imageData: Core.DSImageData;
```

**See also**

* [DSImageData]({{ site.dcvb_js_api }}core/basic-structures/ds-image-data.html)

## location

The location of the complemented barcode in a quadrilateral.

```typescript
location: Core.Quadrilateral;
```

**See also**

* [Quadrilateral]({{ site.dcvb_js_api }}core/basic-structures/quadrilateral.html)
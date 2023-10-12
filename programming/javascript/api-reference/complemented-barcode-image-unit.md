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

## Definition

```ts
interface ComplementedBarcodeImageUnit extends Core.IntermediateResultUnit {
            imageData: Core.DSImageData;
            location: Core.Quadrilateral;
        }
```

| Properties               | Type |
|----------------------|-------------|
| [`imageData`](#imagedata) | *Core.DSImageData* |
| [`location`](#location) | *Core.Quadrilateral* |

### imageData

The image data of the complemented barcode.

```ts
imageData: Core.DSImageData;
```

### location

The location of the complemented barcode in a quadrilateral.

```ts
location: Core.Quadrilateral;
```
---
layout: default-layout
title: interface DeformationResistedBarcode - Dynamsoft Barcode Reader Module JS Edition API Reference
description: This page shows the JS edition of the interface DeformationResistedBarcode in Dynamsoft Barcode Reader Module.
keywords: deformation resisted barcode, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DeformationResistedBarcode

The `DeformationResistedBarcode` interface represents a deformation resisted barcode.

```typescript
interface DeformationResistedBarcode {
    format: DBR.EnumBarcodeFormat;
    imageData: DSImageData;
    location: Quadrilateral;
}
```

## Formats

Possible formats of the localized barcode.

```typescript
Formats: EnumBarcodeFormat;
```

**See also**

* [EnumBarcodeFormat]({{ site.js_api }}enum-barcode-format.html?lang=js)

## imageData

Image data of the deformation-resisted barcode image.

```typescript
imageData: DSImageData;
```

**See also**

* [DSImageData]({{ site.dcvb_js_api }}core/basic-structures/ds-image-data.html)

## location

Location of the deformation resisted barcode within the image.

```typescript
location: Quadrilateral;
```

**See also**

* [Quadrilateral]({{ site.dcvb_js_api }}core/basic-structures/quadrilateral.html)
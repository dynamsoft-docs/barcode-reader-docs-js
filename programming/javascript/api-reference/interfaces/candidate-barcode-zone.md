---
layout: default-layout
title: interface CandidateBarcodeZone - Dynamsoft Barcode Reader Module JS Edition API Reference
description: This page shows the JS edition of the interface CandidateBarcodeZone in Dynamsoft Barcode Reader Module.
keywords: candidate barcode zone, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# CandidateBarcodeZone

The `CandidateBarcodeZone` interface represents a candidate barcode zone.

```typescript
interface CandidateBarcodeZone {
    location: Quadrilateral;
    possibleFormats: EnumBarcodeFormat;
}
```

## location

Location of the candidate barcode zone within the image.

```typescript
location: Quadrilateral;
```

**See also**

* [Quadrilateral]({{ site.dcvb_js_api }}core/basic-structures/quadrilateral.html)

## possibleFormats

Possible formats of the localized barcode.

```typescript
possibleFormats: EnumBarcodeFormat;
```

**See also**

* [EnumBarcodeFormat]({{ site.dcv_enumerations }}barcode-reader/barcode-format.html?lang=js)
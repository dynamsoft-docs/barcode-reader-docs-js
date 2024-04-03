---
layout: default-layout
title: interface LocalizedBarcodeElement - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface LocalizedBarcodeElement in Dynamsoft Core Module.
keywords: localized barcode, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# LocalizedBarcodeElement

A localized element within a barcode. It extends `RegionObjectElement` and includes additional properties `possibleFormats`, `possibleFormatsString`, `angle`, `moduleSize` and `confidence`.

```typescript
interface LocalizedBarcodeElement extends Core.RegionObjectElement {
    possibleFormats: EnumBarcodeFormat;
    possibleFormatsString: string;
    angle: number;
    moduleSize: number;
    confidence: number;
}
```
<!-- 
| Properties                                      | Type                |
| ----------------------------------------------- | ------------------- |
| [possibleFormats](#possibleformats)             | *EnumBarcodeFormat* |
| [possibleFormatsString](#possibleformatsstring) | *string*            |
| [angle](#angle)                                 | *number*            |
| [moduleSize](#modulesize)                       | *number*            |
| [confidence](#confidence)                       | *number*            | -->

## possibleFormats

The possible formats or barcode types that the localized element could correspond to.

```typescript
possibleFormats: EnumBarcodeFormat;
```

**See also**

* [EnumBarcodeFormat]({{ site.dcv_enumerations }}barcode-reader/barcode-format.html?lang=js)

## possibleFormatsString

A string that provides a human-readable representation of the possible barcode formats.

```typescript
possibleFormatsString: string;
```

## angle

The angle or orientation of the localized barcode element. It indicates how the element is positioned or rotated within the barcode.

```typescript
angle: number;
```

## moduleSize

The size of the individual modules or elements within the localized barcode element.

```typescript
moduleSize: number;
```

## confidence

The confidence score or reliability of the localization of the barcode element.

```typescript
confidence: number;
```
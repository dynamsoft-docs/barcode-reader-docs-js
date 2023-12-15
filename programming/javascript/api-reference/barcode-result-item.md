---
layout: default-layout
title: interface BarcodeResultItem - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface BarcodeResultItem in Dynamsoft DBR Module.
keywords: barcode result, item, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# BarcodeResultItem

Interface BarcodeResultItem extends CapturedResultItem, represents a barcode result item decoded by barcode reader engine.

## Definition

```typescript
interface BarcodeResultItem extends Core.CapturedResultItem {
    format: DBR.EnumBarcodeFormat;
    formatString: string;
    text: string;
    bytes: Array<number>;
    location: Core.Quadrilateral;
    confidence: number;
    angle: number;
    moduleSize: number;
    details: BarcodeDetails;
    isDPM: boolean;
    isMirrored: boolean;
}
```

| Properties               | Type |
|----------------------|-------------|
| [`format`](#format) | *DBR.EnumBarcodeFormat* |
| [`formatString`](#formatstring) | *string* |
| [`text`](#text) | *string* |
| [`bytes`](#bytes) | *Array\<number>* |
| [`location`](#location) | *Core.Quadrilateral* |
| [`confidence`](#confidence) | *number* |
| [`angle`](#angle) | *number* |
| [`moduleSize`](#modulesize) | *number* |
| [`details`](#details) | *BarcodeDetails* |
| [`isDPM`](#isdpm) | *boolean* |
| [`isMirrored`](#ismirrored) | *boolean* |

### format

The format of the barcode. It specifies the type of barcode that was recognized.

```typescript
format: DBR.EnumBarcodeFormat;
```

**See also**

* [EnumBarcodeFormat]({{ site.dcv_enumerations }}barcode-reader/barcode-format.html?lang=js)

### formatString

A string that describes the format of the barcode in human-readable form. It provides a textual representation of the barcode format.

```typescript
formatString: string;
```

### text

The textual data decoded from the barcode. It represents the content of the barcode.

```typescript
text: string;
```

### bytes

Stores the raw binary data of the barcode as an array of numbers.

```typescript
bytes: Array<number>;
```

### location

The location of the barcode in the form of a quadrilateral (a set of coordinates defining the four corners of the detected barcode). It describes where the barcode was found within an image.

```typescript
location: Core.Quadrilateral;
```

**See also**

* [Quadrilateral]({{ site.dcv_js_api }}core/basic-structures/quadrilateral.html)

### confidence

The confidence score or reliability of the barcode detection.

```typescript
confidence: number;
```

### angle

The angle or orientation of the barcode, indicating if the barcode was detected at an angle or rotated.

```typescript
angle: number;
```

### moduleSize

The size of the individual modules or elements within the barcode.

```typescript
moduleSize: number;
```

### details

Represent additional details specific to the barcode, which could vary depending on the barcode format.

```typescript
details: BarcodeDetails;
```

### isDPM

Indicates whether the barcode is a Direct Part Marking (DPM) barcode.

```typescript
isDPM: boolean;
```

### isMirrored

Whether the barcode is mirrored or reversed from its normal orientation.

```typescript
isMirrored: boolean;
```
---
layout: default-layout
title: interface DecodedBarcodeElement - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface DecodedBarcodeElement in Dynamsoft Core Module.
keywords: decoded barcode, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DecodedBarcodeElement

A decoded element within a barcode. It extends `RegionObjectElement` and includes additional properties about the decoded barcode.

## Definition

```typescript
interface DecodedBarcodeElement extends Core.RegionObjectElement {
    format: EnumBarcodeFormat;
    formatString: string;
    text: string;
    bytes: Array<number>;
    details: BarcodeDetails;
    isDPM: boolean;
    isMirrored: boolean;
    angle: number;
    moduleSize: number;
    confidence: number;
    extendedBarcodeResults: Array<ExtendedBarcodeResult>
}
```

| Properties               | Type |
|----------------------|-------------|
| [format](#format) | *DBR.EnumBarcodeFormat* |
| [formatString](#formatstring) | *string* |
| [text](#text) | *string* |
| [bytes](#bytes) | *Array\<number>* |
| [details](#details) | *BarcodeDetails* |
| [isDPM](#isdpm) | *boolean* |
| [isMirrored](#ismirrored) | *boolean* |
| [angle](#angle) | *number* |
| [moduleSize](#modulesize) | *number* |
| [confidence](#confidence) | *number* |
| [extendedBarcodeResults](#extendedbarcoderesults) | *Array\<ExtendedBarcodeResult>* |

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

### confidence

The confidence score or reliability of the barcode detection.

```typescript
confidence: number;
```

### extendedBarcodeResults

An array of ExtendedBarcodeResults.

```typescript
extendedBarcodeResults: Array<ExtendedBarcodeResult>
```

**See also**

* [ExtendedBarcodeResults]({{ site.js_api }}extended-barcode-result.html)
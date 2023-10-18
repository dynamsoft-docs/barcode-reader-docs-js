---
layout: default-layout
title: interface ExtendedBarcodeResult - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface ExtendedBarcodeResult in Dynamsoft Core Module.
keywords: extended barcode, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# ExtendedBarcodeResult

An extended barcode result in a decoded barcode element. It contains information such as the type of extended barcode, deformation, clarity, and a sampling image of the barcode.

## Definition

```typescript
interface ExtendedBarcodeResult extends DecodedBarcodeElement {
    extendedBarcodeResultType: EnumExtendedBarcodeResultType;
    deformation: number;
    clarity: number;
    samplingImage: Core.DSImageData;
}
```

| Properties               | Type |
|----------------------|-------------|
| [`extendedBarcodeResultType`](#extendedbarcoderesulttype) | *EnumExtendedBarcodeResultType* |
| [`deformation`](#deformation) | *number* |
| [`clarity`](#clarity) | *number* |
| [`samplingImage`](#samplingimage) | *Core.DSImageData* |

### extendedBarcodeResultType

The type of extended barcode result.

```typescript
extendedBarcodeResultType: EnumExtendedBarcodeResultType;
```

**See also**

* [EnumExtendedBarcodeResultType]({{ site.dcv_enumerations }}barcode-reader/extended-barcode-result-type.html?lang=js)

### deformation

The degree of deformation or distortion in the decoded barcode.

```typescript
deformation: number;
```

### clarity

The clarity or quality of the decoded barcode.

```typescript
clarity: number;
```

### samplingImage

The sampling image of the decoded barcode.

```typescript
samplingImage: Core.DSImageData;
```

**See also**

* [DSImageData]({{ site.dcv_js_api }}core/basic-structures/ds-image-data.html)
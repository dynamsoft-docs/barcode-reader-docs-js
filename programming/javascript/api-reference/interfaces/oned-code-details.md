---
layout: default-layout
title: interface OneDCodeDetails - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface OneDCodeDetails in Dynamsoft DBR Module.
keywords: oneD details, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# OneDCodeDetails

This interface extends BarcodeDetails interface and adds properties specific to one-dimensional barcodes (1D barcodes).

## Definition

```typescript
interface OneDCodeDetails extends BarcodeDetails {
    startCharsBytes: Array<number>;
    stopCharsBytes: Array<number>;
    checkDigitBytes: Array<number>;
    startPatternRange: number;
    middlePatternRange: number;
    endPatternRange: number;
}
```

| Properties               | Type |
|----------------------|-------------|
| [startCharsBytes](#startcharsbytes) | *Array\<number>* |
| [stopCharsBytes](#stopcharsbytes) | *Array\<number>* |
| [checkDigitBytes](#checkdigitbytes) | *Array\<number>* |
| [startPatternRange](#startpatternrange) | *number* |
| [middlePatternRange](#middlepatternrange) | *number* |
| [endPatternRange](#endpatternrange) | *number* |

### startCharsBytes

An array of numbers representing the start characters in a byte array for the 1D barcode. Start characters are often used to identify the beginning of the barcode.

```typescript
startCharsBytes: Array<number>;
```

### stopCharsBytes

An array of numbers representing the stop characters in a byte array for the 1D barcode. Stop characters are used to indicate the end of the barcode.

```typescript
stopCharsBytes: Array<number>;
```

### checkDigitBytes

An array of numbers representing the check digit characters in a byte array. Check digits are used for error detection and correction in some 1D barcodes.

```typescript
checkDigitBytes: Array<number>;
```

### startPatternRange

Two numbers that represent the position of the start pattern relative to the barcode location.

```typescript
startPatternRange: number;
```

| Index | Type | Description |
|-------|------|-------------|
| 0     | *number* | X coordinate of the start position in percentage value. |
| 1     | *number* | X coordinate of the end position in percentage value. |

### middlePatternRange

Two numbers that represent the position of the middle pattern relative to the barcode location.

```typescript
middlePatternRange: number;
```

| Index | Type | Description |
|-------|------|-------------|
| 0     | *number* | X coordinate of the start position in percentage value. |
| 1     | *number* | X coordinate of the end position in percentage value. |

### endPatternRange

Two numbers that represent the position of the end pattern relative to the barcode location.

```typescript
endPatternRange: number;
```

| Index | Type | Description |
|-------|------|-------------|
| 0     | *number* | X coordinate of the start position in percentage value. |
| 1     | *number* | X coordinate of the end position in percentage value. |
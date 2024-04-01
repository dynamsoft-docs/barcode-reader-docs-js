---
layout: default-layout
title: interface PDF417Details - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface PDF417Details in Dynamsoft DBR Module.
keywords: PDF417 details, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# PDF417Details

This interface extends `BarcodeDetails` interface and adds properties specific to PDF417 barcodes such as `rows`, `columns`, `errorCorrectionLevel`, etc.

```typescript
interface PDF417Details extends BarcodeDetails {
    rows: number;
    columns: number;
    errorCorrectionLevel: number;
    hasLeftRowIndicator: number;
    hasRightRowIndicator: number;
}
```
<!-- 
| Properties                                    | Type     |
| --------------------------------------------- | -------- |
| [rows](#rows)                                 | *number* |
| [columns](#columns)                           | *number* |
| [errorCorrectionLevel](#errorcorrectionlevel) | *number* |
| [hasLeftRowIndicator](#hasleftrowindicator)   | *number* |
| [hasRightRowIndicator](#hasrightrowindicator) | *number* | -->

## rows

The row count of the PDF417 barcode, indicating how many rows of modules it contains.

```typescript
rows: number;
```

## columns

The column count of the PDF417 barcode, indicating how many columns of modules it contains.

```typescript
columns: number;
```

## errorCorrectionLevel

The error correction level of the PDF417 barcode.

```typescript
errorCorrectionLevel: number;
```

## hasLeftRowIndicator

Indicates whether the PDF417 code has a left row indicator (1 means yes, 0 means no). Row indicators are used to denote the start of a new row in the barcode.

```typescript
hasLeftRowIndicator: number;
```

## hasRightRowIndicator

Indicates whether the PDF417 code has a right row indicator (1 means yes, 0 means no). Similar to the left row indicator, the right row indicator is used to denote the end of a row in the barcode.

```typescript
hasRightRowIndicator: number;
```
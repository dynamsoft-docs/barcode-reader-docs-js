---
layout: default-layout
title: interface QR CodeDetails - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface QR CodeDetails in Dynamsoft DBR Module.
keywords: QR Code details, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# QRCodeDetails

This interface extends `BarcodeDetails` interface and adds properties specific to QR barcodes such as `rows`, `columns`, `errorCorrectionLevel`, etc.

```typescript
interface QRCodeDetails extends BarcodeDetails {
    rows: number;
    columns: number;
    errorCorrectionLevel: number;
    version: number;
    model: number;
    mode: number;
    page: number;
    totalPage: number;
    parityData: number;
}
```
<!-- 
| Properties                                    | Type     |
| --------------------------------------------- | -------- |
| [rows](#rows)                                 | *number* |
| [columns](#columns)                           | *number* |
| [errorCorrectionLevel](#errorcorrectionlevel) | *number* |
| [version](#version)                           | *number* |
| [model](#model)                               | *number* |
| [mode](#mode)                                 | *number* |
| [page](#page)                                 | *number* |
| [totalPage](#totalpage)                       | *number* |
| [parityData](#paritydata)                     | *number* | -->


## rows

The row count of the QR Code, indicating how many rows of modules it contains.

```typescript
rows: number;
```

## columns

The column count of the QR Code, indicating how many columns of modules it contains.

```typescript
columns: number;
```

## errorCorrectionLevel

The error correction level of the QR Code.

```typescript
errorCorrectionLevel: number;
```

## version

The version of the QR code. QR codes come in different versions, each with varying data capacities and sizes.

```typescript
version: number;
```

## model

Number of models of the QR Code.

```typescript
model: number;
```

## mode

Identify the first data encoding mode of the QR Code.

```typescript
mode: number;
```

## page

Position of the particular symbol in the Structured Append format of the QR Code.

```typescript
page: number;
```

## totalPage

Identify the total number of symbols to be concatenated in the Structured Append format of the QR Code.

```typescript
totalPage: number;
```

## parityData

A value obtained by XORing byte by byte the ASCII/JIS values of all the original input data before division into symbol blocks. It's used for error checking and correction.

```typescript
parityData: number;
```
---
layout: default-layout
title: interface DataMatrixDetails - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface DataMatrixDetails in Dynamsoft DBR Module.
keywords: DataMatrix details, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DataMatrixDetails

This interface extends `BarcodeDetails` interface and adds properties specific to DataMatrix barcodes such as `rows`, `columns`, `dataRegionRows`, etc.

```typescript
interface DataMatrixDetails extends BarcodeDetails {
    rows: number;
    columns: number;
    dataRegionRows: number;
    dataRegionColumns: number;
    dataRegionNumber: number;
}
```
<!-- 
| Properties                              | Type     |
| --------------------------------------- | -------- |
| [rows](#rows)                           | *number* |
| [columns](#columns)                     | *number* |
| [dataRegionRows](#dataregionrows)       | *number* |
| [dataRegionColumns](#dataregioncolumns) | *number* |
| [dataRegionNumber](#dataregionnumber)   | *number* | -->

## rows

The row count of the DataMatrix barcode, indicating how many rows of data modules it contains.

```typescript
rows: number;
```

## columns

The column count of the DataMatrix barcode, indicating how many columns of data modules it contains.

```typescript
columns: number;
```

## dataRegionRows

The row count of the data region within the DataMatrix barcode. Data regions are subdivisions of the barcode where data is stored.

```typescript
dataRegionRows: number;
```

## dataRegionColumns

The column count of the data region within the DataMatrix barcode.

```typescript
dataRegionColumns: number;
```

## dataRegionNumber

The count of data regions in the DataMatrix barcode. DataMatrix barcodes can have multiple data regions for storing data redundantly or for error correction purposes.

```typescript
dataRegionNumber: number;
```
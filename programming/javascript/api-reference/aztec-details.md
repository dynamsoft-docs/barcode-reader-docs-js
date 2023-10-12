---
layout: default-layout
title: interface AztecDetails - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface AztecDetails in Dynamsoft DBR Module.
keywords: Aztec details, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# AztecDetails

This interface is specific to Aztec barcodes. It is extends BarcodeDetails, and includes properties such as rows, columns, and layerNumber.

## Definition

```ts
interface AztecDetails extends BarcodeDetails {
            rows: number;
            columns: number;
            layerNumber: number;
        }
```

| Properties               | Type |
|----------------------|-------------|
| [`rows`](#rows) | *number* |
| [`columns`](#columns) | *number* |
| [`layerNumber`](#layernumber) | *number* |

### rows

The row count of the Aztec barcode, indicating how many rows of modules it contains.

```typescript
rows: number;
```

### columns

The column count of the Aztec barcode, indicating how many columns of modules it contains.

```typescript
columns: number;
```

### layerNumber

The layer number of the Aztec code. It can be a negative number (-1, -2, -3, -4) to specify a compact Aztec code or a positive number (1, 2, .. 32) to specify a normal (full-range) Aztec code. The layer number determines the complexity and capacity of the Aztec barcode.

```typescript
layerNumber: number;
```
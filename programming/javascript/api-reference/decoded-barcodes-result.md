---
layout: default-layout
title: interface DecodedBarcodesResult - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface DecodedBarcodesResult in Dynamsoft DBR Module.
keywords: decoded barcode, barcode result, item, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DecodedBarcodesResult

Interface DecodedBarcodesResult extends CapturedResultItem, represents result of decoding barcodes from an image.

## Definition

```ts
interface DecodedBarcodesResult {
            readonly originalImageHashId: string;
            readonly originalImageTag: Core.ImageTag;
            readonly barcodesResultItems: Array<BarcodeResultItem>;
            readonly errorCode: number;
            readonly errorString: string;
        }
```

| Properties               | Type |
|----------------------|-------------|
| [`originalImageHashId`](#originalimagehashid) | *string* |
| [`originalImageTag`](#originalimagetag) | *Core.ImageTag* |
| [`barcodesResultItems`](#barcodesresultitems) | *Array\<BarcodeResultItem>* |
| [`errorCode`](#errorcode) | *number* |
| [`errorString`](#errorstring) | *string* |

### originalImageHashId

A unique identifier or hash of the original image from which the barcodes were decoded. It can be used to associate the result with a specific input image.

```typescript
readonly originalImageHashId: string;
```

### originalImageTag

An image tag associated with the original image.

```typescript
readonly originalImageTag: Core.ImageTag;
```

### barcodesResultItems

An array of BarcodeResultItem objects, representing the list of decoded barcodes found in the image.

```typescript
readonly barcodesResultItems: Array<BarcodeResultItem>;
```

### errorCode

The error code of the barcode reading result, if an error occurred.

```typescript
readonly errorCode: number;
```

### errorString

The error message of the barcode reading result, if an error occurred.

```typescript
readonly errorString: string;
```
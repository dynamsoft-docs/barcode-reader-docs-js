---
layout: default-layout
title: interface SimplifiedBarcodeReaderSettings - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface SimplifiedBarcodeReaderSettings in Dynamsoft DBR Module.
keywords: simplified setting, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# SimplifiedBarcodeReaderSettings

This interface defines simplified settings for barcode reading tasks.

## Definition

```ts
interface SimplifiedBarcodeReaderSettings {
            barcodeFormatIds: EnumBarcodeFormat;
            expectedBarcodesCount: number;
            grayscaleTransformationModes: Array<Core.EnumGrayscaleTransformationMode>;
            grayscaleEnhancementModes: Array<Core.EnumGrayscaleEnhancementMode>; 
            localizationModes: Array<number>;
            deblurModes: Array<number>;
            minResultConfidence: number;
            minBarcodeTextLength: number;
            barcodeTextRegExPattern: string;
            maxThreadsInOneTask: number;
            scaleDownThreshold: number;
        }
```

| Properties               | Type |
|----------------------|-------------|
| [`barcodeFormatIds`](#barcodeformatids) | *EnumBarcodeFormat* |
| [`expectedBarcodesCount`](#expectedbarcodescount) | *number* |
| [`grayscaleTransformationModes`](#grayscaletransformationmodes) | *Array\<Core.EnumGrayscaleTransformationMode>* |
| [`grayscaleEnhancementModes`](#grayscaleenhancementmodes) | *Array\<Core.EnumGrayscaleEnhancementMode>* |
| [`localizationModes`](#localizationmodes) | *Array\<number>* |
| [`deblurModes`](#deblurmodes) | *Array\<number>* |
| [`minResultConfidence`](#minresultconfidence) | *number* |
| [`minBarcodeTextLength`](#minbarcodetextlength) | *number* |
| [`barcodeTextRegExPattern`](#barcodetextregexpattern) | *string* |
| [`maxThreadsInOneTask`](#maxthreadsinonetask) | *number* |
| [`scaleDownThreshold`](#scaledownthreshold) | *number* |

### barcodeFormatIds

A combined value of enumeration BarcodeFormat to specify the targeting barcode formats.

```typescript
barcodeFormatIds: EnumBarcodeFormat;
```

### expectedBarcodesCount

Set the expected barcode count. The default value is 0.

```typescript
expectedBarcodesCount: number;
```

**Remarks**

* Set `expectedBarcodesCount` to 0 if the barcode count is unknown. The library will try to find at least 1 barcode.
* Set `expectedBarcodesCount` to 1 to reach the highest speed for processing single barcode.
* Set `expectedBarcodesCount` to "n" if there will be "n" barcodes to process from an image.
* Set `expectedBarcodesCount` to the highest expected value if there exists multiple barcodes but the exact count is not confirmed.

### grayscaleTransformationModes

Set the grayscale transformation modes with an array of enumeration `GrayscaleTransformationMode`. View the reference page of `GrayscaleTransformationModes` for more detail about grayscale transformation modes.

```typescript
grayscaleTransformationModes: Array<Core.EnumGrayscaleTransformationMode>;
```

### grayscaleEnhancementModes

Set the grayscale enhancement modes with an array of enumeration `GrayscaleEnhancementMode`. View the reference page of `GrayscaleEnhancementModes` for more detail about grayscale enhancement modes.

```typescript
grayscaleEnhancementModes: Array<Core.EnumGrayscaleEnhancementMode>; 
```

### localizationModes

Set the location modes with an array of enumeration `LocalizationMode`. View the reference page of `LocalizationModes` for more detail about location modes.

```typescript
localizationModes: Array<number>;
```

### deblurModes

Set the deblur modes with an array of enumeration `DeblurMode`. View the reference page of `DeblurModes` for more detail about deblur modes.

```typescript
deblurModes: Array<number>;
```

### minResultConfidence

Set the minimum result confidence to filter out the low confidence results. The default value is 30.

```typescript
minResultConfidence: number;
```

### minBarcodeTextLength

Set the minimum barcode text length to filter out the unqualified results.

```typescript
minBarcodeTextLength: number;
```

### barcodeTextRegExPattern

Set the RegEx pattern of the barcode text to filter out the unqualified results.

```typescript
barcodeTextRegExPattern: string;
```

### maxThreadsInOneTask

Set the maximum available threads count in one barcode decoding task.

```typescript
maxThreadsInOneTask: number;
```

### scaleDownThreshold

Set the threshold for scaling down the input image during barcode localization. If the shorter edge size of the image is larger than this threshold,the original may be scaled down to reduce processing time. The default value is 2300.

```typescript
scaleDownThreshold: number;
```
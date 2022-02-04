---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - BarcodeReader
description: This page shows the BarcodeReader Class of Dynamsoft Barcode Reader JavaScript SDK.
keywords: FurtherModes, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: FurtherModes
---

# FurtherModes

## Attributes

| Attribute | Type |
|---------- | ---- |
| [`colourConversionModes`](#colourConversionModes) | *number &#124; [`EnumColourConversionMode`](../enum/EnumColourConversionMode.md)* |
| [`grayscaleTransformationModes`](#grayscaleTransformationModes) | *number &#124; [`EnumGrayscaleTransformationMode`](../enum/EnumGrayscaleTransformationMode.md)* |
| [`regionPredetectionModes`](#regionPredetectionModes) | *number &#124; [`EnumRegionPredetectionMode`](../enum/EnumRegionPredetectionMode.md)* |
| [`imagePreprocessingModes`](#imagePreprocessingModes) | *number &#124; [`EnumImagePreprocessingMode`](../enum/EnumImagePreprocessingMode.md)* |
| [`textureDetectionModes`](#textureDetectionModes) | *number &#124; [`EnumTextureDetectionMode`](../enum/EnumTextureDetectionMode.md)* |
| [`dpmCodeReadingModes`](#dpmCodeReadingModes) | *number &#124; [`EnumDPMCodeReadingMode`](../enum/EnumDPMCodeReadingMode.md)* |
| [`deformationResistingModes`](#deformationResistingModes) | *number &#124; [EnumDeformationResistingMode](../enum/EnumDeformationResistingMode.md)*  |
| [`barcodeComplementModes`](#barcodeComplementModes) | *number &#124; [`EnumBarcodeComplementMode`](../enum/EnumBarcodeComplementMode.md)* |
| [`barcodeColourModes`](#barcodeColourModes) | *number &#124; [`EnumBarcodeColourMode`](../enum/EnumBarcodeColourMode.md)* |

<br />

### colourConversionModes
Sets the modes and their correspondent priorities when the SDK is required to convert a colour image to a grayscale one.

**Value Range** Please see the [EnumColourConversionMode](../enum/EnumColourConversionMode.md) items.

**Default Value** `[CICM_GENERAL,CICM_SKIP,CICM_SKIP,CICM_SKIP,CICM_SKIP,CICM_SKIP,CICM_SKIP,CICM_SKIP]`

<br />

### grayscaleTransformationModes
This parameter should be mainly used when trying to read light on dark barcodes. By default, the SDK is configured to read dark on light barcodes.

**Value Range** An array of [EnumGrayscaleTransformationMode](../enum/EnumGrayscaleTransformationMode.md) items.

**Default Value** `[GTM_ORIGINAL,GTM_SKIP,GTM_SKIP,GTM_SKIP,GTM_SKIP,GTM_SKIP,GTM_SKIP,GTM_SKIP]`

**Remarks** If you are primarily scanning dark on light barcodes, it is best to set the highest priority item in the array to `GTM_INVERTED`.

```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.furtherModes.grayscaleTransformationModes[0] = Dynamsoft.DBR.EnumGrayscaleTransformationMode.GTM_INVERTED;
await reader.updateRuntimeSettings(runtimeSettings);
```
<br />

### regionPredetectionModes
This parameters helps speed up the recognition process by detecting regions of interest automatically. Pre-detection is based on the colour/grayscale distribution of each area, and then choosing areas of interest based on the priority of the region predetction modes.

**Value Range** Array of [EnumRegionPredetectionMode](../enum/EnumRegionPredetectionMode.md) items.

**Default Value** `[RPM_GENERAL,RPM_SKIP,RPM_SKIP,RPM_SKIP,RPM_SKIP,RPM_SKIP,RPM_SKIP,RPM_SKIP]`

**Remarks** If the image is large, and the barcode is very small relative to the whole image, then it is recommended to enable region predetction to speed up the localization process and recognition accuracy.

```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.furtherModes.regionPredetectionModes[0] = Dynamsoft.DBR.EnumRegionPredetectionMode.RPM_GENERAL_RGB_CONTRAST;
runtimeSettings.furtherModes.regionPredetectionModes[1] = Dynamsoft.DBR.EnumRegionPredetectionMode.RPM_GENERAL;
await reader.updateRuntimeSettings(runtimeSettings);
```

<br />

### imagePreprocessingModes
This parameter helps enhance or keep the features of barcode zones by processing colour or grayscale images, in turn improving the localization process.

**Value Range** Array of [`EnumImagePreprocessingMode`](../enum/EnumImagePreprocessingMode.md) items.

**Default Value** `[IPM_GENERAL,IPM_SKIP,IPM_SKIP,IPM_SKIP,IPM_SKIP,IPM_SKIP,IPM_SKIP,IPM_SKIP]`

**Remarks** In order for barcodes to be localized, the barcode must have clear barcode zone features that the algorithm uses to find the barcode and in turn recognize it. By enhancing some of the available zone features, the process of finding the barcode can also potentially become more effective.

```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.furtherModes.imagePreprocessingModes[0] = Dynamsoft.DBR.EnumImagePreprocessingMode.IPM_GRAY_SMOOTH;
runtimeSettings.furtherModes.imagePreprocessingModes[1] = Dynamsoft.DBR.EnumImagePreprocessingMode.IPM_SHARPEN_SMOOTH;
await reader.updateRuntimeSettings(runtimeSettings);
```
<br />

### textureDetectionModes
When scanning 1D barcodes, this parameter helps reduce the time cost and error probability caused by textures that can resemble 1D barcodes.

**Value Range** Array of [EnumTextureDetectionMode](../enum/EnumTextureDetectionMode.md) items.

**Default Value** `[TDM_GENERAL_WIDTH_CONCENTRATION,TDM_SKIP,TDM_SKIP,TDM_SKIP,TDM_SKIP,TDM_SKIP,TDM_SKIP,TDM_SKIP]`

**Remarks** Mainly applicable when scanning 1D barcodes.

```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.furtherModes.textureDetectionModes[0] = Dynamsoft.DBR.EnumTextureDetectionMode.TDM_SKIP; // to disable this parameter completely
await reader.updateRuntimeSettings(runtimeSettings);
```

<br />

### dpmCodeReadingModes
This parameter should only be enabled when working with DPM codes. By default, DPM reading is disabled.

**Value Range** Array of [EnumDPMCodeReadingMode](../enum/EnumDPMCodeReadingMode.md) items.

**Default Value** `[DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP]`

```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.furtherModes.dpmCodeReadingModes[0] = Dynamsoft.DBR.EnumDPMCodeReadingMode.DPMCRM_GENERAL; // to enable DPM code reading set the highest priority item to General
await reader.updateRuntimeSettings(runtimeSettings);
```
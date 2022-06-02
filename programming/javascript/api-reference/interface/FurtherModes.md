---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - Interface - FurtherModes
description: This page shows the BarcodeReader Class of Dynamsoft Barcode Reader JavaScript SDK.
keywords: FurtherModes, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: FurtherModes
permalink: /programming/javascript/api-reference/interface/FurtherModes.html
---

# FurtherModes

## Attributes

| Attribute | Type |
|---------- | ---- |
| [`colourConversionModes`](#colourconversionmodes) | *number &#124; [`EnumColourConversionMode`](../enum/EnumColourConversionMode.md)* |
| [`grayscaleTransformationModes`](#grayscaletransformationmodes) | *number &#124; [`EnumGrayscaleTransformationMode`](../enum/EnumGrayscaleTransformationMode.md)* |
| [`regionPredetectionModes`](#regionpredetectionmodes) | *number &#124; [`EnumRegionPredetectionMode`](../enum/EnumRegionPredetectionMode.md)* |
| [`imagePreprocessingModes`](#imagepreprocessingmodes) | *number &#124; [`EnumImagePreprocessingMode`](../enum/EnumImagePreprocessingMode.md)* |
| [`textureDetectionModes`](#texturedetectionmodes) | *number &#124; [`EnumTextureDetectionMode`](../enum/EnumTextureDetectionMode.md)* |
| [`dpmCodeReadingModes`](#dpmcodereadingmodes) | *number &#124; [`EnumDPMCodeReadingMode`](../enum/EnumDPMCodeReadingMode.md)* |
| [`deformationResistingModes`](#deformationresistingmodes) | *number &#124; [`EnumDeformationResistingMode`](../enum/EnumDeformationResistingMode.md)*  |
| [`barcodeComplementModes`](#barcodecolourmodes) | *number &#124; [`EnumBarcodeComplementMode`](../enum/EnumBarcodeComplementMode.md)* |
| [`barcodeColourModes`](#barcodecolourmodes) | *number &#124; [`EnumBarcodeColourMode`](../enum/EnumBarcodeColourMode.md)* |

### colourConversionModes

Sets the modes and their correspondent priorities when the SDK is required to convert a colour image to a grayscale one.

**Value Range** Please see the [EnumColourConversionMode](../enum/EnumColourConversionMode.md) items.

**Default Value** `[CICM_GENERAL,CICM_SKIP,CICM_SKIP,CICM_SKIP,CICM_SKIP,CICM_SKIP,CICM_SKIP,CICM_SKIP]`

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

### dpmCodeReadingModes

This parameter should only be enabled when working with DPM codes. By default, DPM reading is disabled.

**Value Range** Array of [EnumDPMCodeReadingMode](../enum/EnumDPMCodeReadingMode.md) items

**Default Value** `[DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP,DPMCRM_SKIP]`

```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.furtherModes.dpmCodeReadingModes[0] = Dynamsoft.DBR.EnumDPMCodeReadingMode.DPMCRM_GENERAL; // to enable DPM code reading set the highest priority item to General
await reader.updateRuntimeSettings(runtimeSettings);
```

### deformationResistingModes

This parameter should be used when handling distorted or deformed barcodes. Currently, there is only one general mode that deal with the deformation resistance, so if you are looking to enable this feature, then please refer to the code snippet.

**Value Range** Array of [EnumDeformationResistingMode](../enum/EnumDeformationResistingMode.md) items

**Default Value** `[DRM_SKIP,DRM_SKIP,DRM_SKIP,DRM_SKIP,DRM_SKIP,DRM_SKIP,DRM_SKIP,DRM_SKIP]`

```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.furtherModes.deformationResistingModes[0] = Dynamsoft.DBR.EnumDeformationResistingMode.DRM_GENERAL; // to enable deformation resistance set the highest priority item to General
await reader.updateRuntimeSettings(runtimeSettings);
```

### barcodeComplementModes

When dealing with a barcode that has 'missing' parts, this parameter controls how to complement the missing parts of said barcode.

**Value Range** Array of [EnumBarcodeComplementMode](../enum/EnumBarcodeComplementMode.md) items

**Default Value** `[BCM_SKIP,BCM_SKIP,BCM_SKIP,BCM_SKIP,BCM_SKIP,BCM_SKIP,BCM_SKIP,BCM_SKIP]`

```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.furtherModes.barcodeComplementModes[0] = Dynamsoft.DBR.EnumBarcodeComplementMode.BCM_GENERAL; // to enable the barcode complement feature set the highest priority item to General
await reader.updateRuntimeSettings(runtimeSettings);
```

### barcodeColourModes

In most cases, barcodes come as a dark image with a light background (e.g. black barcode on a white background). However, that is not always the case as the barcodes can come as a light image with a dark background, or some other variation.

**Value Range** Array of [EnumBarcodeColourMode](../enum/EnumBarcodeColourMode.md) items

**Default Value** `[BICM_DARK_ON_LIGHT,BICM_SKIP,BICM_SKIP,BICM_SKIP,BICM_SKIP,BICM_SKIP,BICM_SKIP,BICM_SKIP]`

**Remarks** To learn about the purpose of each mode, please refer to this [page](https://www.dynamsoft.com/barcode-reader/parameters/reference/barcode-colour-modes.html?ver=latest).

```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.furtherModes.barcodeColourModes[0] = Dynamsoft.DBR.EnumBarcodeColourMode.BICM_DARK_ON_LIGHT; // to support both dark-on-light and light-on-dark barcodes then the array must contain both modes.
runtimeSettings.furtherModes.barcodeColourModes[1] = Dynamsoft.DBR.EnumBarcodeColourMode.BICM_LIGHT_ON_DARK; // to support both dark-on-light and light-on-dark barcodes then the array must contain both modes.
await reader.updateRuntimeSettings(runtimeSettings);
```

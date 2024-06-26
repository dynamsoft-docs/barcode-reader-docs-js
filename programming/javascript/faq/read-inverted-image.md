---
layout: default-layout
title: How to read an inverted barcode?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, inverted barcode
description: How to read an inverted barcode?
needAutoGenerateSidebar: false
---

# How to read an inverted barcode?

[<< Back to FAQ index](index.md)

## Version 10
this can be achieved by setting the value of the `grayscaleTransformationModes` array of `furtherModes` to use `GTM_INVERTED` 

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.barcodeSettings.grayscaleTransformationModes[0] = Dynamsoft.Core.EnumGrayscaleTransformationMode.GTM_INVERTED;
await router.updateSettings("ReadSingleBarcode", settings);

```
## Version 9
Typically, normal barcode images include a dark barcode on a light background. An inverted image in this case would have a light barcode on a dark background instead. In order to read those types of barcodes, the `grayscaleTransformationModes` array of `furtherModes` must prioritize `GTM_INVERTED` like shown in the below example.

```javascript
settings.furtherModes.grayscaleTransformationModes[0] =
  Dynamsoft.DBR.EnumGrayscaleTransformationMode.GTM_INVERTED;
await scanner.updateRuntimeSettings(settings);
```

---
layout: default-layout
title: What are the differences between updateScanSettings/updateVideoSettings/updateRuntimeSettings?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, updateScanSettings, updateVideoSettings, updateRuntimeSettings
description: What are the differences between updateScanSettings/updateVideoSettings/updateRuntimeSettings?
needAutoGenerateSidebar: false
---

# What are the differences between updateScanSettings/updateVideoSettings/updateRuntimeSettings ?

[<< Back to FAQ index](index.md)

## Version 10
`updateVideoSettings` is used to update the [MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints) that define most of the video information such as width, height, and the camera facingMode (i.e. front or rear camera).

`updateSettings` is used to update the [SimplifiedSettings](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/interfaces/simplified-capture-vision-settings.html?product=dbr&lang=javascript) interface. It updates the runtime settings with a given template object. 
```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.barcodeSettings.barcodeFormatIds =
  Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

## Version 9

`updateScanSettings` is used to update the [ScanSettings](https://www.dynamsoft.com/barcode-reader/programming/javascript/api-reference/interface/ScanSettings.html?ver=latest) interface. This can be used to configure settings such as ignoring duplicate reads, setting sound/vibration when a barcode is scanned. 

`updateVideoSettings` is used to update the [MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints) that define most of the video information such as width, height, and the camera facingMode (i.e. front or rear camera).

`updateRuntimeSettings` is used to update the [RuntimeSettings](https://www.dynamsoft.com/barcode-reader/programming/javascript/api-reference/interface/RuntimeSettings.html?ver=latest) interface. It updates the runtime settings with a given object or use the string `speed`, `balance`, or `coverage` to use [our preset settings for BarcodeScanner](https://www.dynamsoft.com/barcode-reader/parameters/structure-and-interfaces-of-parameters.html?ver=latest#using-runtime-settings-templates). The default setting is `speed`.

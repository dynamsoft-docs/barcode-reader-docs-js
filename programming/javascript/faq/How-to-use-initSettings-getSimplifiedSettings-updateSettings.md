---
layout: default-layout
title:  How to use initSettings/getSimplifiedSettings/updateSettings?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, updateScanSettings, updateVideoSettings, updateRuntimeSettings
description: What are the differences between updateScanSettings/updateVideoSettings/updateRuntimeSettings?
needAutoGenerateSidebar: false
---

# How to use initSettings/getSimplifiedSettings/updateSettings?

[<< Back to FAQ index](index.md)

`initSettings` is used to intitiate instance with specified setting. [initSettings](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/settings.html?product=dbr&lang=javascript#initsettings) configures runtime settings using a provided JSON string, an object, or a URL pointing to an object, which contains settings for one or more CaptureVisionTemplates.

`getSimplifiedSettings` is used to get the [SimplifiedCaptureVisionSettings](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/interfaces/simplified-capture-vision-settings.html?product=dbr&lang=javascript) that is interface provides a standardized way to adjust a select set of settings for a given CaptureVisionTemplate.

`updateSettings` is used to update the [SimplifiedCaptureVisionSettings](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/interfaces/simplified-capture-vision-settings.html?product=dbr&lang=javascript) interface. It updates the barcode settings tasks with a given object [SimplifiedBarcodeReaderSettings](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/interfaces/simplified-barcode-reader-settings.html).

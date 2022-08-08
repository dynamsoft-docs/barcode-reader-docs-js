---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - Interface - ScannerPlayCallbackInfo
description: Use this interface syntax to set scanner play callback info for barcodes in your Dynamsoft Barcode Reader project for JavaScript.
keywords: ScannerPlayCallbackInfo, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: ScannerPlayCallbackInfo
permalink: /programming/javascript/api-reference/interface/ScannerPlayCallbackInfo.html
---


# ScannerPlayCallbackInfo

`interface` ScannerPlayCallbackInfo

* deviceId: *string*

* width: *number*

* height: *number*

```js
scanner.onPlayed = rsl=>{ console.log(rsl.width+'x'+rsl.height) };
await scanner.show(); // or open, play, setCurrentCamera, like these.
```

---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - Interface - ScannerPlayCallbackInfo
description: This page shows the BarcodeReader Class of Dynamsoft Barcode Reader JavaScript SDK.
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

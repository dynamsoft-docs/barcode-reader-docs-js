---
layout: default-layout
title: Interface - v8.8.7 ScanSettings - Dynamsoft Barcode Reader JavaScript Edition API
description: This page shows the ScanSettings of the BarcodeReader Class of Dynamsoft Barcode Reader JavaScript SDK.
keywords: ScanSettings, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: ScanSettings
permalink: /programming/javascript/api-reference/interface/ScanSettings-v8.8.7.html
---


# ScanSettings

`interface` ScanSettings

* intervalTime?: *number*

  > Scan interval used to allow the library to release the CPU periodically. Measured in ms.

* duplicateForgetTime?: *number*

  > Ignore duplicated results found in the specified time period. Measured in ms.

```js
let scanSettings = await scanner.getScanSettings();
scanSettings.intervalTime = 100; // 100ms
scanSettings.duplicateForgetTime = 3000; // 3s
await scanner.updateScanSettings(scanSettings);
```

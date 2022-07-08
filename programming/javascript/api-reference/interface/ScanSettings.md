---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - Interface - ScanSettings
description: Use this interface syntax to set scan settings for barcodes in Dynamsoft Barcode Reader for JavaScript.
keywords: ScanSettings, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: ScanSettings
permalink: /programming/javascript/api-reference/interface/ScanSettings.html
---

# ScanSettings

`interface` ScanSettings

* intervalTime?: *number*

  > Scan interval used to allow the library to release the CPU periodically. Measured in ms. The default value is `0`.

* duplicateForgetTime?: *number*

  > Ignore duplicated results found in the specified time period. Measured in ms. The default value is `3000`.

* whenToPlaySoundforSuccessfulRead?: *string*

  > Sets when to play sound on barcode recognition (user input is required on iOS or [Chrome](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#chrome_enterprise_policies) for any sound to play). Allowed values are
  >
  > * `never` : never play sound, the default value;
  > * `frame` : play sound when one or multiple barcodes are found on a frame;
  > * `unduplicated` : play sound when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, play only once).

* soundOnSuccessfullRead?: *string*

  > Specifies the sound to play on barcode recognition. If not specified, the default one is used.

* whenToVibrateforSuccessfulRead?: *string*

  > Sets when to vibrate on barcode recognition (user input is required in [Chrome](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#chrome_enterprise_policies) for the vibration). It only supports Android Devices with a vibrating system. Allowed values are
  >
  > * `never`: never vibrate, the default value;
  > * `frame`: vibrate when one or multiple barcodes are found on a frame;
  > * `unduplicated`: vibrate when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, vibrate only once).

* vibrateDuration?: *number*

  > Returns or sets how long the vibration lasts in milliseconds. It only supports Android Devices with a vibrating system. The default value is `300` .

```js
let scanSettings = await scanner.getScanSettings();
scanSettings.intervalTime = 100; // 100ms
scanSettings.whenToPlaySoundforSuccessfulRead = "never";
scanSettings.whenToVibrateforSuccessfulRead = "never";
scanSettings.duplicateForgetTime = 3000; // 3s
await scanner.updateScanSettings(scanSettings);
```

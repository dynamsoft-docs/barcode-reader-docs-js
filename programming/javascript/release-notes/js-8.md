---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript SDK - Release Notes v8.x
description: Dynamsoft Barcode Reader SDK JavaScript version 8.x. Have a close look at the recent updates with various bugs fixed and new attributes added.
keywords: release notes, javascript
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
permalink: /programming/javascript/release-notes/js-8.html
---

# Release Notes for JavaScript SDK - 8.x

## 8.8.7 (01/26/2022)

* Added the attribute `muted` to the video embed element so that the video can be played without user interaction.
* Fixed a bug with the property `intervalTime` in `ScanSettings` to avoid unnecesary frame fetching actions.

## 8.8.5 (01/26/2022)

* Fixed a bug where the scan indicator (laser) flickers upon initialization when a scan region is set.
* Fixed a bug that the wrong version of WASM is referenced when used in a Node.js application.
* Fixed a bug that some images may cause stack overflow errors when used in a Node.js application.

## 8.8.3 (10/29/2021)

* Fixed a bug where it takes more time than expected when creating a `BarcodeReader` or `BarcodeScanner` instance.
* Fixed a bug which makes the building fail in frameworks such as Angular, React, Vue, etc.

## 8.8.0 (10/28/2021)

<div class="fold-panel-prefix"></div>

### Version Highlights <i class="fa fa-caret-down"></i>

<div class="fold-panel-start"></div>

* Added a new localization mode `ONED_FAST_SCAN`, which significantly improved the localization speed for 1D barcodes.
* Added the ability to specify barcode `width`, `height`,  `angle` to improve the recognition speed if you have advance information about barcodes.
* Optimized the logic of `confidence` scoring for 2D barcodes. The 2D barcode results with confidence greater than 30 are more accurate.

<div class="fold-panel-end"></div>

### Edition Highlights

* Reading speed has significantly increased based on better camera control and optimized memory usage in the core algorithm.
* Misreading of 2D barcodes has been significantly reduced as a result of better result filtering based on the optimized algorithm in reading confidence calculating.
* More samples are added to demonstrate the usage of the library in popular frameworks. For more information, please see [Demo and Samples - JavaScript](https://www.dynamsoft.com/barcode-reader/programming/javascript/samples-demos/index.html?ver=latest).

#### Improved

* Refactored camera related APIs internally for easier maintenance.
* Improved result filtering so that misread 2D barcodes are not returned.

#### Changed

The class names of the built-in UI elements have changed

| Previous versions | v8.8.0+ |
|:-:|:-:|
| `dbrScanner-bg-loading` | `dce-bg-loading` |
| `dbrScanner-bg-camera` | `dce-bg-camera` |
| `dbrScanner-video` | `dce-video` |
| `dbrScanner-sel-camera` | `dce-sel-camera` |
| `dbrScanner-sel-resolutio` | `dce-sel-resolution` |
| `dbrScanner-btn-close` | `dce-btn-close` |

## 8.6.3 (09/30/2021)

Fixed an issue where the scanning page may freeze when debugging in the Developer Tools with Chromium-94 browsers on PCs.

## 8.6.1 (09/01/2021)

Fixed a bug where an error occurs when switching region setting from a JSON object to an array of objects.

## 8.6.0 (08/31/2021)

<div class="fold-panel-prefix"></div>

### Version Highlights <i class="fa fa-caret-down"></i>

<div class="fold-panel-start"></div>

* Improved the confidence calculating algorithm for 1D barcodes. Misreading rate of results with confidence between 30-100 has been significantly reduced.
* Improved the reading speed on clear images by implementing a new deblur mode `DM_BASED_ON_LOC_BIN`.

<div class="fold-panel-end"></div>

### Edition Highlights

* Continuous reading of barcodes from a video input is now significantly faster thanks to optimized frame fetching logic.
* Camera selecting on devices with multiple cameras has been optimized so that the main camera is always used by default. This is especially helpful on high-end Android devices.
* Misreading of 1D barcodes has been significantly reduced as a result of better result filtering based on the optimized algorithm in reading confidence calculating.

### Changelog

#### Improved

* Improved frame fetching so that more frames are read for the same time period.
* Improved camera selecting so that the initial camera used is the main camera.
* Improved result filtering so that misread 1D barcodes are not returned.
* Improved WebGL implementation so that much less time is required for image preprocessing.

#### Added

* Added method isWasmLoaded() to return whether the engine file is loaded.	
* Added method isContextDestroyed() to return whether a BarcodeReader or BarcodeScanner instance has been destroyed.
* Added method getOriginalImageInACanvas() to return the actual image the engine tried to read barcodes from.	
* Added method destroyContext() to destroy the BarcodeReader or BarcodeScanner instance itself.	
* Added property ifSaveOriginalImageInACanvas to control whether the actual image to read is saved for debugging.	
* Added property whenToPlaySoundforSuccessfulRead to control when the beep sound should be played.	
* Added property whenToVibrateforSuccessfulRead to control when the device should vibrate.

#### Changed

* Change the default engine from the compact engine to the full-featured engine.

#### Deprecated

* The method destroy() is deprecated, Use the method destroyContext() instead.	
* The property isLoaded is deprecated. Use the method isWasmLoaded() instead.
* The property bDestroyed is deprecated. Use the method isContextDestroyed() instead.	
* The property oriCanvas is deprecated. Use the method getOriginalImageInACanvas() instead.	
* The property bVibrateOnSuccessfulRead is deprecated. Use whenToVibrateforSuccessfulRead instead.	
* The property bPlaySoundOnSuccessfulRead is deprecated. Use whenToPlaySoundforSuccessfulRead instead.	
* The property bSaveOriCanvas is deprecated. Use ifSaveOriginalImageInACanvas instead.

## 8.4.0 (06/29/2021)

### New

* Added a new argument, `ThresholdCompensation`, to the `BinarizationModes` mode arguments.

### Improved

* Improved the speed of identifying 1D codes from still images.
* Improved the speed of identifying dense QR codes.
* Improved the performance of boundary identification for DataMatrix codes.
* Improved camera selection in some browsers on Android devices.
* Improved the `createInstance()` method to avoid unnecessary download of the file "dbr.scanner.html".

### Changed

* Moved the following APIs from `Dynamsoft.DBR.BarcodeReader` to `Dynamsoft. DBR`
 + `detectEnvironment()`

 + `engineResourcePath`

 + `handshakeCode`

 + `isLoaded()`

 + `licenseServer`

 + `loadWasm()`

 + `organizationID`

 + `productKeys`

 + `sessionPassword`

 + `version`

 + `_bUseFullFeature`

Please note that these APIs still exist under `Dynamsoft.DBR.BarcodeReader` , but they have been deprecated and replaced by APIs in the new namespace.

## 8.2.5 (05/18/2021)

### New

* Added property `organizationID` which can be used to fetch license(s) belonging to the specified organization from the License Tracking Server.
* Added a class name to the powered-by message element on the built-in UI so that it can be manipulated in CSS.

### Improved

* Removed redundant warning messages for duplicate barcodes.

### Fixed

* Fixed a bug with the API `bSaveOriCanvas` where the same canvas is reused resulting in duplicated original image for different barcodes.

## 8.2.3 (04/15/2021)

### New

* Added properties `bVibrateOnSuccessfulRead` and `vibrateDuration` to control the vibration of an Android device when barcodes are found.
* Added methods `showVideo()` and `decodeCurrentFrame()` to make it possible for users to show the video and manually trigger the decoding of a frame.
* Added a sample for [Vue 3](https://v3.vuejs.org/).

### Improved

* Optimized how the WASM files are created to make them smaller (18% smaller).
* When opening a camera takes too long and times out, an exception will be thrown.
* When the webpage in which a `BarcodeScanner` instance is running gets hidden (not visible to the user), the barcode scanning will stop automatically. Later when it becomes visible again, the scanning will resume automatically.

### Changed

* Added a "Powered by Dynamsoft" logo to the default Barcode Scanner UI.

## 8.2.1 (03/29/2021)

### Fixed

* Resolved a bug that returns the error as a Promise object instead of a string when calling the method loadWasm().

## 8.2.0 (03/17/2021)

### New

* Added a new mode argument, `FindAccurateBoundary`, to [`RegionPredetectionModes`](https://www.dynamsoft.com/barcode-reader/parameters/reference/region-predetection-modes.html?ver=latest) that determines if the SDK attempts to find an accurate boundary when RegionPredetectionModes is set to `RPM_GENERAL_HSV_CONTRAST`. 

### Improved

* Improved both the localization and decoding algorithms for Postal Codes. 
* LocalizationMode `LM_STATISTICS_POSTAL_CODE` will not be added automatically when enabling Postal Code in your runtime settings. Instead, users must manually add it to the LocalizationMode array if it is required.

### Fixed

* Resolved a bug that infrequently causes the application to crash when decoding a MicroPDF417 barcode.

## 8.1.3 (03/04/2021)

### New

* Added support for SSR (Server-side Rendering) and 3 related samples for Nextjs, Nuxtjs and gatsby respectively.

### Fixed

* Fixed a bug where if `scanner.destroy()` is called before `scanner.show()` finishes, the camera will not be released.

## 8.1.2 (01/22/2021)

### New

* Added `mode`, `page`,  `totalPage` and `parityData` in the `QRCodeDetails` Class.

### Improved

* Improved the recognition accuracy for GS1 Databar.
* Removed the exception code from `barcodeText` when using a valid trial license.
* Optimized memory usage when using WebGL for mapping color images into grayscale images which made the process faster. 

### Fixed

* Fixed a bug where `barcodeFormatString`, `barcodeFormatString_2`,  `regionName` and `documentName` don't have value in the `IRT_TYPED_BARCODE_ZONE` intermediate result.

## 8.1.0 (01/19/2021)

### New 

 
* Added support for MSI Code (Modified Plessey). 
* Added a new member `BarcodeZoneMinDistanceToImageBorders` in the `PublicRuntimeSettings` struct to set the minimum distance (in pixels) between barcode zone and image borders.
* Added exception error message to `TextResult` when license initialization fails or decoding authorization fails.
 

### Improved

 
* Improved the localization robustness for QR Code.
* Improved the localization for low quality 1D barcodes.
* Improved the deblurring performance and recognition rate for DataMatrix.
* Improved the recognition rate for Aztec.
* Improved runtime setting presets to use `BarcodeZoneMinDistanceToImageBorders`.
 

### Fixed

 
* Fixed a bug where Micro PDF417 may not be localized in multiple-barcode scenarios.
* Fixed a bug where the `ExpectedBarcodesCount` and `BarcodeFormat` parameters do not work in the `Region`.
* Fixed a memory issue in iOS Safari caused by enabling sound.
* Fixed an issue with UTF-8 character encoding.

## 8.0.0 (11/25/2020)

### New

* Added support for decoding barcodes from an existing video stream.
* Introduced new namespace `Dynamsoft. DBR`.
* Implemented a new licensing tracking mechanism, License 2.0, which makes it easier for users to track license usage.
* Added a new format control parameter, BarcodeZoneMinDistanceToImageBorders, to set the minimum distance (in pixels) between the barcode zone and image borders.
* Added a new format control parameter, MinRatioOfBarcodeZoneWidthToHeight, to set the minimum ratio (width/height) of the barcode zone.
* Added a new format control parameter, BarcodeZoneBarCountRangeArray, to set the barcode zone’s range of bar count for barcode search.
* Added a new argument, SpatialIndexBlockSize, for RPM_GENERAL_RGB_CONTRAST, RPM_GENERAL_GRAY_CONTRAST and RPM_GENERAL_HSV_CONTRAST.
* Added a new parameter, DeblurModes, so users can use different deblur algorithms for different scenarios. DeblurModes has the following enum types: DirectBinarization, ThresholdBinarization, GrayEqulization, Smoothing, Morphing, DeepAnalysis and Sharpening.

### Improved

* Changed the default runtime preset setting of `BarcodeScanner` from `speed` to `single`.
* Improved the localization speed for the `ScanDirectly` mode.
* Improved the localization accuracy for DataMatrix codes with a narrow quiet zone.

### Fixed

### Feature Deprecated

* `DeblurLevel` is now deprecated. It still works in this version but could be removed in the near future. We recommend using `DeblurModes` instead.

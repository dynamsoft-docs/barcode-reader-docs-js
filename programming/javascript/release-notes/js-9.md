---
layout: default-layout
title: Release Notes v9.x - Dynamsoft Barcode Reader JavaScript Edition
description: This note features the latest updates in Barcode Reader JavaScript SDK version 9.x. New features were added along with various APIs deprecated, removed, and removed.
keywords: release notes, javascript
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
permalink: /programming/javascript/release-notes/js-9.html
---

# Release Notes for Dynamsoft Barcode Reader JavaScript Edition - 9.x

## 9.6.31 (10/11/2023)

#### Fixed

- Fixed an issue may causing error when using WebGL to fetch images on iOS 16.7 and iOS 17.
- Fixed an issue where incorrect data was retrieved when fetching grayscale images or fetching images by 'context2d'.

#### Improved

- Updated the internal Dynamsoft Camera Enhancer to v3.3.8.

## 9.6.30 (09/13/2023)

#### Fixed

- Fixed a bug that led to incorrect output of start/middle/endPatternRange in `OneDCodeDetails`.
- Fixed a bug where an unnecessary input element appears in Safari on iOS 16 when setting `singleFrameMode` to true.

#### Improved

- Updated the barcode reader algorithm to v9.6.30.
- Updated the internal Dynamsoft Camera Enhancer to v3.3.6.
- Updated the API [`singleFrameMode`](../api-reference/BarcodeScanner.md#singleframemode) to support using the system camera directly without prompting for image source selection on mobile devices.
- Updated the method `close()` so that it automatically clears the highlighting of found barcode symbols.

## 9.6.21 (08/03/2023)

#### Fixed

- Fixed an issue where TypeScript 5 cannot locate the declaration file when importing package.

#### Improved

- Updated the built-in Dynamsoft Camera Enhancer module to version 3.3.5 for improved camera performance.
- Update API annotations.

## 9.6.20 (04/18/2023)

#### Improved

- Update the barcode reader algorithm to v9.6.20.
- Update the internal Dynamsoft Camera Enhancer to v3.3.4.

#### Fixed

- Fixed a bug where setting `runtimeSettings.barcodeFormatIds_2` to `BF2_ALL` doesn't take effect.
- Fixed bug where barcode result coordinates were incorrect when calling `decode()` on large images (2048px or wider on mobile, 4096px or wider on desktop). This also causes the wrong canvas to be returned when calling `getOriginalImageInACanvas()`.

## 9.6.11 (03/13/2023)

### Added

- Added method `getVideoFit` to return the value of the object-fit CSS property of the video element.
- Added method `convertToPageCoordinates` to convert coordinates of a barcode location to the coordinates relative to the top left point of the entire document.
- Added method `convertToClientCoordinates` to convert coordinates of a barcode location to the coordinates within the application's viewport at which the event occurred (as opposed to the coordinate within the page).

## 9.6.10 (02/21/2023)

### Added

- Added method `testCameraAccess` to test whether there is an available camera.
- Added method `enableTapToFocus` to enable manual camera focus when clicking/tapping on the video.
- Added method `disableTapToFocus` to disable manual camera focus when clicking/tapping on the video.  
- Added method `isTapToFocusEnabled` to return whether clicking/tapping on the video invokes the camera to focus.

#### Improved

- Update the barcode reader algorithm to v9.6.10.
- Update the internal Dynamsoft Camera Enhancer to v3.3.1.
- The method [`decodeBuffer`](../api-reference/BarcodeReader.md#decodebuffer) is updated to accept an additional parameter "orientation" to help specify the orientation of the image data.
- The interface [`LocalizationResult`](../api-reference/interface/LocalizationResult.md) is updated to have a new property "transformationMatrix".
- Three missing errorcodes are added: DBR_PANORAMA_LICENSE_INVALID, DBR_PHARMACODE_LICENSE_INVALID, DBR_IMAGE_ORIENTATION_INVALID. Check the full likst at [`EnumErrorCode`](enum/../../api-reference/enum/EnumErrorCode.md).

#### Fixed

- Fixed a bug where the "autoZoom" feature may not work as expected.

## 9.6.2 (01/16/2023)

#### Improved

- Improved the `autoZoom` feature.

## 9.6.1 (12/19/2022)

#### Fixed

- Fixed a bug where the indexedDB could become unresponsive if barcodes were scanned too quickly.

## 9.6.0 (12/13/2022)

<div class="fold-panel-prefix"></div>

### Version Highlights <i class="fa fa-caret-down"></i>

<div class="fold-panel-start"></div>

- **DotCode** decoding is improved by optimizing the localization of DotCodes that are close to one another.
- **EAN8 barcode** decoding is improved by honing the accuracy of localization algorithms.
- **QR code** localizing is improved by reducing the mis-assemble rate of the finder patterns when using the localization mode LM_CONNECTED_BLOCK or LM_SCAN_DIRECTLY, which are designed for speed. The mis-assembling only occurs when there exist dense QR codes on the same image.
- **Mirrored rectangular DataMatrix barcode** is supported by implementing `MirrorMode` when localizing the barcodes.
- Deformed barcode decoding is improved by extending the supported modes and mode arguments of `DeformationResistingModes`.

<div class="fold-panel-end"></div>

### Edition-Specific Highlights

#### Added

- Added 3 new properties in [`ScanSettings`](../api-reference/interface/ScanSettings.md#scansettings)
  1. `autoZoom`, when set to `true`, means the SDK will automatically zoom in on the video if the barcode appears too small in the video feed and fails to be read;
  2. `autoFocus`, when set to `true`, means the SDK will automatically focus on the part of the video where a barcode is found but fails to be read;
  3. `autoSuggestTip`, when set to `true`, means the SDK will automatically suggest Tip messages to help guide the user to acquire better video frames for barcode reading.

> These features are only valid when there is a intermediate_results module license.

#### Changed

- `duplicateForgetTime` can only be set to a maximum of 10 seconds in this version. It was not limitd in previous versions.

#### Fixed

- Fixed a bug where binary intermediate result images had unwanted black borders.

## 9.3.1 (10/10/2022)

### Fixed

* Fixed a bug where calling `setCurrentCamera()` or `setResolution()` before opening the camera would cause an error.
* Fixed a bug where the canvas used internally remains in the DOM and is not removed as expected after a `BarcodeScanner` instances calls `destroyContext()`.

## 9.3.0 (09/27/2022)

### Added

* Added 3 properties to control the highlight style of linear barcodes before validation.
  * `barcodeFillStyleBeforeVerification`
  * `barcodeStrokeStyleBeforeVerification`
  * `barcodeLineWidthBeforeVerification`

### Fixed

* Fixed a bug where linear barcodes found were highlighted with a beep (if sound was enabled) but no results were output.

## 9.2.13 (08/11/2022)

* Fixed bugs with the properties `barcodeFillStyle`,`barcodeStrokeStyle` and `barcodeLineWidth` to make them work properly.
* Fixed a bug with `onFrameRead` so that it fires regardless of whether there is a result on the processed frame (as expected).
* Fixed a bug with `onImageRead` so that it fires only once for the same image (as expected), instead of twice.

## 9.2.12 (08/04/2022)

* Fixed a bug where the scan region mask and/or other shapes drawn on the UI were not updated when the view changed to landscape from portrait or vice versa on mobile devices.
* This version uses [Dynamsoft Camera Enhancer version 3.0.1](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/release-note/release-notes-3.x.html?ver=latest#301-08042022).

## 9.2.11 (07/28/2022)

### Added

* Added option `captureAndDecodeInParallel` to the interface `ScanSettings` to control whether to speed up the decoding by capturing the next frame in advance.
* Added properties `ifSaveLastUsedCamera` and `ifSkipCameraInspection` for better camera control.
* Added two more templates `dense` and `distance` as options for `updateRuntimeSettings()`.

### Changed

* The default resolution to try for cameras on desktop is changed to 1920 x 1080, previously it was 1280 x 720.
* The method `setImageSource()` now takes an additional parameter `options` which helps to pass the information needed by the `BarcodeReader` object, such as the definition (`Dynamsoft.DCE.DrawingItem`) for creating the shapes that highlight barcodes.
* When reading 1D barcodes, the callback `onFrameRead` now verifies a result across multiple frames before outputting it so that it is more reliable. The same logic was always used for the callback `onUniqueRead`.
* The methods `pauseScan()` (for `BarcodeScanner`) and `pauseScanning()` (for `BarcodeReader`) now both accept an optional parameter `options`, which can control the behavior of the pause, such as whether to keep results highlighted (`keepResultsHighlighted`).
* This version uses [Dynamsoft Camera Enhancer version 3.0.0](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/release-note/release-notes-3.x.html#300-07272022) instead of the previous version 2.3.2.

### Fixed

* Fixed a bug where the intermediate result images are redacted even with a valid license.

## 9.0.2 (05/06/2022)

### Added

* Added API `ifShowScanRegionMask` to `BarcodeScanner` to control whether to show the scan region mask.

### Changed

* Moved the following docs from the doc directory to the root directory of the package.
  * `Api Reference.html`
  * `legal.txt`
  * `License Agreement.html`

### Fixed

* Fixed bugs with `regionMaskFillStyle`, `regionMaskStrokeStyle`, `regionMaskLineWidth` of `BarcodeScanner` to avoid invalid value setting.
* Fixed a bug where region will be reset to full image when switching template after region setting of `BarcodeScanner`.
* Fixed a bug where the region setting is invalid when using `updateRuntimeSettings` of `BarcodeReader`.

## 9.0.1 (04/25/2022)

### Added

* Added method `setVideoFit()` to `BarcodeScanner` to allow the video element to either fit or cover the viewer.
* Added method `setImageSource()` to `BarcodeReader` to specify an Image Source which provides images of the type [`DSImage`](../api-reference/interface/dsimage.md) for continuous scanning.
* Added methods `startScanning()`, `pauseScanning()`, `resumeScanning()`, `stopScanning()`, `getScanSettings()` and `updateScanSettings()` as well as events `onUniqueRead` and `onImageRead` to `BarcodeReader` to facilitate continous scanning of images coming from the Image Source.

## 9.0.0 (03/24/2022)

<div class="fold-panel-prefix"></div>

### Version Highlights <i class="fa fa-caret-down"></i>

<div class="fold-panel-start"></div>

* Simplified the license activation steps. Different license activation APIs are integrated into one API.
* Added support for **Pharmacode**.
* Added support for **Code 11**, an 1D format.
* Deformation resisting modes `DRM_BROAD_WARP`, `DRM_LOCAL_REFERENCE` and `DRM_DEWRINKLE` are optimized and detached from `DRM_GENERAL`. Users can specify a more effective deformation resisting mode when processing **QRCode** and **DataMatrix codes**.
* Optimized the confidence scoring system for **PDF417 codes**.

<div class="fold-panel-end"></div>

### Edition-Specific Highlights

#### Added

* Added the property `license` as the main API for setting a license key.
* Added methods `getFocus()` and `setFocus()` to control the camera focus.
* Added method `getFrameRate()` to check the current frame rate of the video input.

#### Changed

* The file **dbr.scanner.html** has been renamed to **dbr.ui.html**.
    * `dbrScanner-cvs-scanarea` class is now renamed to `dce-scanarea`
    * `dce-video` is now replaced by `dce-video-container`
    * `dbrScanner-scanlight` is now replaced by `dce-scanlight`
    * `dbrScanner-cvs-drawarea` has been removed

The following APIs are renamed:

| Old API | New API |
|:-|:-:|
| `onUnduplicatedRead` | `onUniqueRead` |
| `outputSettingsToString()` | `outputRuntimeSettingsToString()` |
| `Dynamsoft.DBR.BarcodeReader.isLoaded()` | `Dynamsoft.DBR.BarcodeReader.isWasmLoaded()` |

The following APIs are moved:

| API Name | Notes |
|:-|:-|
| `whenToPlaySoundforSuccessfulRead` | Moved to [`ScanSettings`](../api-reference/interface/ScanSettings.md). |
| `soundOnSuccessfullRead` | Moved to [`ScanSettings`](../api-reference/interface/ScanSettings.md). |
| `whenToVibrateforSuccessfulRead` | Moved to [`ScanSettings`](../api-reference/interface/ScanSettings.md). |
| `vibrateDuration` | Moved to [`ScanSettings`](../api-reference/interface/ScanSettings.md). |

#### Deprecated

The following APIs are deprecated:

| API Name | Notes |
|:-|:-|
| `Dynamsoft.DBR.BarcodeReader.handshakeCode` | Use `Dynamsoft.DBR.BarcodeReader.license` instead. |
| `Dynamsoft.DBR.BarcodeReader.licenseServer` | Use  `Dynamsoft.DBR.BarcodeReader.license` instead. |
| `Dynamsoft.DBR.BarcodeReader.organizationID` | Use `Dynamsoft.DBR.BarcodeReader.license` instead. |
| `Dynamsoft.DBR.BarcodeReader.sessionPassword` | Use `Dynamsoft.DBR.BarcodeReader.license` instead. |
| `Dynamsoft.DBR.BarcodeReader.productKeys` | Use `Dynamsoft.DBR.BarcodeReader.license` instead. |
| `Dynamsoft.DBR.BarcodeScanner.handshakeCode` | Use `Dynamsoft.DBR.BarcodeScanner.license` instead. |
| `Dynamsoft.DBR.BarcodeScanner.licenseServer` | Use  `Dynamsoft.DBR.BarcodeScanner.license` instead. |
| `Dynamsoft.DBR.BarcodeScanner.organizationID` | Use `Dynamsoft.DBR.BarcodeScanner.license` instead. |
| `Dynamsoft.DBR.BarcodeScanner.sessionPassword` | Use `Dynamsoft.DBR.BarcodeScanner.license` instead. |
| `Dynamsoft.DBR.BarcodeScanner.productKeys` | Use `Dynamsoft.DBR.BarcodeScanner.license` instead. |

#### Removed

The following APIs are removed:

| API Name | Notes |
|:-|:-|
| `Dynamsoft.DBR.browserInfo` | Use `Dynamsoft.DBR.BarcodeReader.browserInfo` instead. |
| `Dynamsoft.DBR.detectEnvironment()` | Use `Dynamsoft.DBR.BarcodeReader.detectEnvironment()` instead. |
| `Dynamsoft.DBR.deviceFriendlyName` | Use `Dynamsoft.DBR.BarcodeReader.deviceFriendlyName` instead. |
| `Dynamsoft.DBR.engineResourcePath` | Use `Dynamsoft.DBR.BarcodeReader.engineResourcePath` instead. |
| `Dynamsoft.DBR.handshakeCode` | Use `Dynamsoft.DBR.BarcodeReader.license` instead. |
| `Dynamsoft.DBR.isLoaded()` | Use `Dynamsoft.DBR.BarcodeReader.isWasmLoaded()` instead. |
| `Dynamsoft.DBR.licenseServer` | Use  `Dynamsoft.DBR.BarcodeReader.license` instead. |
| `Dynamsoft.DBR.loadWasm` | Use `Dynamsoft.DBR.BarcodeReader.isWasmLoaded` instead. |
| `Dynamsoft.DBR.organizationID` | Use `Dynamsoft.DBR.BarcodeReader.license` instead. |
| `Dynamsoft.DBR.productKeys` | Use `Dynamsoft.DBR.BarcodeReader.license` instead. |
| `Dynamsoft.DBR.sessionPassword` | Use `Dynamsoft.DBR.BarcodeReader.license` instead. |
| `Dynamsoft.DBR.version` | Use `Dynamsoft.DBR.BarcodeReader.version` instead. |

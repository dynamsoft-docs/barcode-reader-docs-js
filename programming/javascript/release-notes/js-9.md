---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript SDK - Release Notes v8.x
description: This is the release notes page of Dynamsoft Barcode Reader for JavaScript SDK v8.x.
keywords: release notes, javascript
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# Release Notes for JavaScript SDK - 9.x

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

### Edition Highlights

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

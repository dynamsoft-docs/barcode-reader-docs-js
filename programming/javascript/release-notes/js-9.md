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

## 9.0.0 (03/22/2022)

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

#### Changed

* The following APIs are renamed:

| Old API | New API |
|:-:|:-:|
| `onUnduplicatedRead` | `onUniqueRead` |
| `outputSettingsToString()` | `outputRuntimeSettingsToString()` |
| `Dynamsoft.DBR.BarcodeReader.isLoaded()` | `Dynamsoft.DBR.BarcodeReader.isWasmLoaded()` |

* The following APIs are moved:

| API Name | Notes |
|:-:|:-:|
| `whenToPlaySoundforSuccessfulRead` | Moved to [`ScanSettings`](./api-reference/interface/ScanSettings.md). |
| `soundOnSuccessfullRead` | Moved to [`ScanSettings`](./api-reference/interface/ScanSettings.md). |
| `whenToVibrateforSuccessfulRead` | Moved to [`ScanSettings`](./api-reference/interface/ScanSettings.md). |
| `vibrateDuration` | Moved to [`ScanSettings`](./api-reference/interface/ScanSettings.md). |

#### Deprecated

* The following APIs are deprecated:

| API Name | Notes |
|:-:|:-:|
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

* The following APIs are removed:

| API Name | Notes |
|:-:|:-:|
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
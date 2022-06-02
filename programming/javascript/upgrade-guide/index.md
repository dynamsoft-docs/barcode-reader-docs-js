---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - How to Upgrade
description: This page shows how to upgrade Dynamsoft Barcode Reader JavaScript SDK to the latest version.
keywords: user guide, upgrade, javascript, js
needAutoGenerateSidebar: true
pageStartVer: 8.4
permalink: /programming/javascript/upgrade-guide/
---

# How to Upgrade

## From v8.x to v9.x

1. Update the version number if you are using a **CDN**:

   ```html
   <script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.0.2/dist/dbr.js"></script>
   ```

   > If you have deployed the library files to your own server, [download the latest version](https://www.dynamsoft.com/barcode-reader/downloads/?utm_source=upgradeguide) and replace the old files.

2. Update the API you use for licensing the SDK

Previously, you might have used the APIs `productKeys`, `handshakeCode`, `organizationID` and `sessionPassword`, etc. In v9.0.0+, use the API `license` instead.

* If you used an offline license before, simply pass that license key using the API `license`.
* If you used an online license before, you can log in the [customer portal](https://www.dynamsoft.com/customer/license/fullLicense) and check the according license key to be used with the API `license`.

[Contact Dynamsoft Sales Team](mailto:sales@dynamsoft.com) for more information.

### Breaking changes introduced in v9.0.0

* The following APIs are renamed:

| Old API | New API |
|:-:|:-:|
| `onUnduplicatedRead` | `onUniqueRead` |
| `outputSettingsToString()` | `outputRuntimeSettingsToString()` |
| `Dynamsoft.DBR.BarcodeReader.isLoaded()` | `Dynamsoft.DBR.BarcodeReader.isWasmLoaded()` |

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

* The following APIs are moved:

| API Name | Notes |
|:-:|:-:|
| `whenToPlaySoundforSuccessfulRead` | Moved to [`ScanSettings`](../api-reference/interface/ScanSettings.md). |
| `soundOnSuccessfullRead` | Moved to [`ScanSettings`](../api-reference/interface/ScanSettings.md). |
| `whenToVibrateforSuccessfulRead` | Moved to [`ScanSettings`](../api-reference/interface/ScanSettings.md). |
| `vibrateDuration` | Moved to [`ScanSettings`](../api-reference/interface/ScanSettings.md). |

* The file **dbr.scanner.html** has been renamed to **dbr.ui.html**.

### Breaking changes introduced in v8.8.0

The class names of the built-in UI elements changed in v8.8.0+:

| Previous versions | v8.8.0+ |
|:-:|:-:|
| `dbrScanner-bg-loading` | `dce-bg-loading` |
| `dbrScanner-bg-camera` | `dce-bg-camera` |
| `dbrScanner-video` | `dce-video` |
| `dbrScanner-sel-camera` | `dce-sel-camera` |
| `dbrScanner-sel-resolutio` | `dce-sel-resolution` |
| `dbrScanner-btn-close` | `dce-btn-close` |

---

## From v7.x to v8.x

1. Change your license

   In v8.0, we introduced a new license tracking mechanism, [License 2.0](https://www.dynamsoft.com/license-tracking/docs/about/index.html). If you have a v7.x license and wish to upgrade to v8.x, you must [contact us](https://www.dynamsoft.com/company/contact/) to acquire a new license.

2. Update version and code

   If you are using a **CDN**, simply update the version number denoted after **@** in the URL.

   ```html
   <script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/dbr.js" data-productKeys="PRODUCT-KEYS"></script>
   ```

   If you have deployed the library files to your server, you'll need to replace the old files with the ones in the latest version. Download the latest version [here](https://www.dynamsoft.com/barcode-reader/downloads/).

   Next, replace the value ("PRODUCT-KEYS") of `data-productKeys` with the handshake code or organization ID you receive based on License 2.0 (as mentioned in the section [Change your license](#change-your-license) above).

### API changes

#### :exclamation: *Namespace change*

Use the new namespace `Dynamsoft.DBR` in place of just `Dynamsoft`. The following shows the equivalent changes for `BarcodeScanner` and `BarcodeReader`:

```js
Dynamsoft.BarcodeScanner -> Dynamsoft.DBR.BarcodeScanner
Dynamsoft.BarcodeReader -> Dynamsoft.DBR.BarcodeReader
```

If you are using the library as an ES/CMD module, you don’t need to change your code. Otherwise, you can either make a global change from `Dynamsoft` to `Dynamsoft.DBR` or use the following line to quickly make the namespace change.

```js
Dynamsoft = Dynamsoft.DBR; //This line should be called before you call any other methods/properties of the library.
```

#### Deprecating `deblurLevel`

`deblurLevel` has been deprecated in v8.0 and replaced with `deblurModes`. Athough `deblurLevel` will continue to work in v8.0, we recommend updating your code to use `deblurModes` as soon as possible to avoid any breaking changes in the future.

Check out the code below on how to switch from `deblurLevel` to `deblurModes`.

```js
let settings = await barcodeScanner.getRuntimeSettings();
//settings.deblurLevel = 9;
settings.deblurModes = ["DM_DIRECT_BINARIZATION",   
                        "DM_THRESHOLD_BINARIZATION", 
                        "DM_GRAY_EQUALIZATION",
                        "DM_SMOOTHING",
                        "DM_MORPHING",
                        "DM_DEEP_ANALYSIS",
                        "DM_SHARPENING",
                        "DM_SKIP"] 
await barcodeScanner.updateRuntimeSettings(settings);
```

#### Default runtime setting has changed from `speed` to `single` for `BarcodeScanner`

The `single` runtime setting was introduced in v7.5 as an experimental feature for `BarcodeScanner`. In v8.0, `single` is made the default setting.

Before v8.0, the default setting was `speed`.

> NOTE:
>
> `BarcodeReader` still uses `coverage` as the default setting.

#### Removed some deprecated APIs from `textResult`

* `BarcodeText` is removed, use `barcodeText` instead
* `BarcodeFormat` is removed, use `barcodeFormat` instead
* `BarcodeFormatString` is removed, use `barcodeFormatString` instead
* `LocalizationResult` is removed, use `localizationResult` instead
* `ResultPoints` in `localizationResult` is removed, use `x1,x2,x3,x4,y1,y2,y3,y4` instead
* `accompanyingTextBytes` is removed, if you wish to use the feature or something similar, please [contact us](https://www.dynamsoft.com/company/contact/).

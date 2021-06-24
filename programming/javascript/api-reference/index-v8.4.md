---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - Main Page
description: This is the main page of Dynamsoft Barcode Reader JavaScript SDK API Reference.
keywords: BarcodeScanner, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: API Reference
---

# Dynamsoft Barcode Reader for JavaScript - API Reference

## Global

* [licenseServer](#licenseserver)
* [organizationID](#organizationid)
* [handshakeCode](#handshakecode)
* [sessionPassword](#sessionpassword)
* [deviceFriendlyName](#devicefriendlyname)
* [productKeys](#productkeys)

* [_bUseFullFeature](#_busefullfeature)
* [engineResourcePath](#engineresourcepath)
* [loadWasm](#loadwasm)
* [isLoaded](#isloaded)
* [version](#version)
* [detectEnvironment](#detectenvironment)

## Classes

* [BarcodeReader](BarcodeReader.md)
* [BarcodeScanner](BarcodeScanner.md) 

## Interfaces

* [LocalizationResult](interface/LocalizationResult.md)
* [RegionDefinition](interface/RegionDefinition.md)
* [RuntimeSettings](interface/RuntimeSettings.md)
* [ScannerPlayCallbackInfo](interface/ScannerPlayCallbackInfo.md)
* [ScanSettings](interface/ScanSettings.md)
* [TextResult](interface/TextResult.md)
* [VideoDeviceInfo](interface/VideoDeviceInfo.md)

## Enums

* [EnumBarcodeColourMode](enum/EnumBarcodeColourMode.md)
* [EnumBarcodeComplementMode](enum/EnumBarcodeComplementMode.md)
* [EnumBarcodeFormat](enum/EnumBarcodeFormat.md)
* [EnumBarcodeFormat_2](enum/EnumBarcodeFormat_2.md)
* [EnumBinarizationMode](enum/EnumBinarizationMode.md)
* [EnumClarityCalculationMethod](enum/EnumClarityCalculationMethod.md)
* [EnumClarityFilterMode](enum/EnumClarityFilterMode.md)
* [EnumColourClusteringMode](enum/EnumColourClusteringMode.md)
* [EnumColourConversionMode](enum/EnumColourConversionMode.md)
* [EnumConflictMode](enum/EnumConflictMode.md)
* [EnumDeblurMode](enum/EnumDeblurMode.md)
* [EnumDeformationResistingMode](enum/EnumDeformationResistingMode.md)
* [EnumDPMCodeReadingMode](enum/EnumDPMCodeReadingMode.md)
* [EnumErrorCode](enum/EnumErrorCode.md)
* [EnumGrayscaleTransformationMode](enum/EnumGrayscaleTransformationMode.md)
* [EnumImagePixelFormat](enum/EnumImagePixelFormat.md)
* [EnumImagePreprocessingMode](enum/EnumImagePreprocessingMode.md)
* [EnumIMResultDataType](enum/EnumIMResultDataType.md)
* [EnumIntermediateResultSavingMode](enum/EnumIntermediateResultSavingMode.md)
* [EnumIntermediateResultType](enum/EnumIntermediateResultType.md)
* [EnumLocalizationMode](enum/EnumLocalizationMode.md)
* [EnumPDFReadingMode](enum/EnumPDFReadingMode.md)
* [EnumQRCodeErrorCorrectionLevel](enum/EnumQRCodeErrorCorrectionLevel.md)
* [EnumRegionPredetectionMode](enum/EnumRegionPredetectionMode.md)
* [EnumResultCoordinateType](enum/EnumResultCoordinateType.md)
* [EnumResultType](enum/EnumResultType.md)
* [EnumScaleUpMode](enum/EnumScaleUpMode.md)
* [EnumTerminatePhase](enum/EnumTerminatePhase.md)
* [EnumTextFilterMode](enum/EnumTextFilterMode.md)
* [EnumTextResultOrderMode](enum/EnumTextResultOrderMode.md)
* [EnumTextureDetectionMode](enum/EnumTextureDetectionMode.md)

### licenseServer

* `static` licenseServer: *string&#91;&#93; &#124; string*

  Specifies the URL(s) for the main and stand-by License Tracking Server(s). This is only required when you host the License Tracking Server(s) yourself. If nothing is set, the Server(s) hosted by Dynamsoft will be used.

  ```js
  // You can specify only the main server
  Dynamsoft.DBR.licenseServer = ["YOUR-OWN-MAIN-LTS"];

  //or you can specify both
  Dynamsoft.DBR.licenseServer = ["YOUR-OWN-MAIN-LTS", "YOUR-OWN-STANDBY-LTS"];
  ```

<br />

### organizationID

* `static` organizationID: *string*

  When a license is purchased, it is registered to an Organization. This license is then hosted by a License Tracking Server which authorizes terminal devices and consumes the license. This API specifies which Organization you would like to acquire authorization from.

  ```js
  Dynamsoft.DBR.organizationID = "YOUR-ORGANIZATION-ID";
  ```

<br />

### handshakeCode

* `static` handshakeCode: *string*

  Licenses registered to the same Organization are grouped by Handshake Codes. When an Organization is specified by `organizationID`, the default Handshake Code will be used unless another Code is specified with this API.

  Generally, the first Handshake Code ever created for an organization is the default one. However, you can always make another Code default in the [customer portal](https://www.dynamsoft.com/lts/#/handshakeCodes).
  
  ```js
  Dynamsoft.DBR.handshakeCode = "YOUR-HANDSHAKE-CODE";
  ```

<br />

### sessionPassword

* `static` sessionPassword: *string*

  Specifies a password to protect the [Handshake Code](#handshakeCode). If no Handshake Code is specified with the API `handshakeCode`, this password protects the default Handshake Code.

  The password can be set for each Handshake Code when it was first created and can be changed later by editing the configuration of the Code.

  ```js
  Dynamsoft.DBR.sessionPassword = "YOUR-SESSION-PASSWORD";
  ```
  
<br />

### deviceFriendlyName

* `static` deviceFriendlyName: *string*

  Sets a human-readable name that identifies the device. This name will appear in the device details table when you check the statistics of a Handshake Code or a License Item.

  ```js
  Dynamsoft.DBR.deviceFriendlyName = "Harry-Potter-iPhone";
  ```

<br />

### productKeys

* `static` productKeys: *string*

  A product key is an alphanumeric string used as an offline license. If such a key is specified in your program, you do not need to specify anything else for licensing purposes.
  
  ```js
  Dynamsoft.DBR.productKeys = "YOUR-PRODUCT-KEYS";
  ```

  For convenience, you can even set `productKeys` in the `script` tag.
  
  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/dbr.js" data-productKeys="PRODUCT-KEYS"></script>
  ```

<br />

### _bUseFullFeature

* `static` _bUseFullFeature: *boolean*

  Whether to use the full engine. The property needs to be set before [loadWasm](#loadwasm). The default is 'false'.

   ```js
   Dynamsoft.DBR.BarcodeReader._bUseFullFeature = true;
   await Dynamsoft.DBR.BarcodeReader.loadWasm();
   ```

   Learn more about [differences between compact and full WASM engines](../../user-guide/?ver=latest#specify-which-engine-to-use).

<br />

### engineResourcePath

* `static` engineResourcePath: *string*

  Specifies the path to find the engine(s). The property needs to be set before [loadWasm](#loadwasm). If not specified, the library will try to find the engine in the same location as the main JavaScript file (dbr.js).

  ```js
  Dynamsoft.DBR.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/";
  await Dynamsoft.DBR.BarcodeReader.loadWasm();
  ```

<br />

### loadWasm

* `static` loadWasm&#40;&#41;: *Promise&lt;void&gt;*

  Downloads and compiles the engine to get it loaded/ready for a BarcodeReader or BarcodeScanner instance to be created. You can call this API to silently set the operating environment of the library as soon as the page is loaded, avoiding unnecessary waiting time when using the library later.

  If this API is not called beforehand, it will be called automatically when creating an instance of BarcodeReader or BarcodeScanner.
 
  ```js
  window.addEventListener('DOMContentLoaded', (event) => {
     Dynamsoft.DBR.BarcodeReader.loadWasm();
  });
  ```

<br />

### isLoaded

* `static` isLoaded&#40;&#41;: *boolean*

  Returns whether the engine is loaded/ready.

<br />

### version

* `readonly` `static` version: *string*

  Returns the version of the library including the detailed version numbers of the engine and the main JavaScript code.

  Needs to call after [loadWasm](#loadwasm).

  ```js
  console.log(Dynamsoft.DBR.BarcodeReader.version); // "loading...(JS 8.2.5.20210426)"
  await Dynamsoft.DBR.BarcodeReader.loadWasm();
  console.log(Dynamsoft.DBR.BarcodeReader.version); // "8.4.0.8960(JS 8.2.5.20210426)"
  ```

<br />

### detectEnvironment

* `static` detectEnvironment&#40;&#41;: *Promise&lt;any&gt;*

  Returns a report on the current running environments.

  ```js
  console.log(Dynamsoft.DBR.BarcodeReader.detectEnvironment());
  // {"wasm":true, "worker":true, "getUserMedia":true, "camera":true, "browser":"Chrome", "version":90, "OS":"Windows"}
  ```

<br />
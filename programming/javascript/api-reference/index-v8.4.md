---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - Main Page
description: This is the main page of Dynamsoft Barcode Reader JavaScript SDK API Reference.
keywords: BarcodeScanner, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
---

# Dynamsoft Barcode Reader for JavaScript - API Reference

The library comes with two primary Classes: `BarcodeReader` and `BarcodeScanner`.

## BarcodeReader

A low-level barcode reader that processes still images and return barcode results. The following code snippet shows its basic usage.

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
let results = await reader.decode(imageSource);
for(let result of results){
  console.log(result.barcodeText);
}
```

The APIs for this class include

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ### Create and Destroy Instances
> <hr>
> * [createInstance](BarcodeReader.md#createinstance)
> * [destroy](BarcodeReader.md#destroy)
> * [bDestroyed](BarcodeReader.md#bdestroyed)
> 
> ### Decode Barcodes
> <hr>
> * [decode](BarcodeReader.md#decode)
> * [decodeBase64String](BarcodeReader.md#decodebase64string)
> * [decodeUrl](BarcodeReader.md#decodeurl)
> * [decodeBuffer](BarcodeReader.md#decodebuffer)
> 
> ### Change Settings
> <hr>
> * [getRuntimeSettings](BarcodeReader.md#getruntimesettings)
> * [updateRuntimeSettings](BarcodeReader.md#updateruntimesettings)
> * [resetRuntimeSettings](BarcodeReader.md#resetruntimesettings)
> * [getModeArgument](BarcodeReader.md#getmodeargument)
> * [setModeArgument](BarcodeReader.md#setmodeargument)
> 
> ### Auxiliary
> <hr>
> * [bSaveOriCanvas](BarcodeReader.md#bsaveoricanvas)
> * [oriCanvas](BarcodeReader.md#oricanvas)

## BarcodeScanner

A barcode scanner object gets access to a camera via the [MediaDevices](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices) interface, then uses its built-in UI to show the camera input and perform continuous barcode scanning on the incoming frames.

The default built-in UI of each barcode scanner is defined in the file "dbr.scanner.html". If used directly, the UI will fit the entire page and sit on top. There are a few ways to customize it, read more on how to [Customize the UI](../user-guide/#customize-the-ui).

Although a barcode scanner is designed to scan barcodes from a video input, it also supports a special mode called [singleFrameMode](#singleFrameMode) which allows the user to select a still image or take a shot with the mobile camera for barcode scanning.

The following code snippet shows the basic usage of the `BarcodeScanner` class.

```js
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
scanner.onUnduplicatedRead = txt => console.log(txt);
await scanner.show();
```

The `BarcodeScanner` is a child class of [BarcodeReader](./BarcodeReader.md) and inherits all its methods and properties. APIs not directly inherited include 

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ### Create and Destroy Instances
> <hr>
> * [createInstance](BarcodeScanner.md#createinstance)
> * [destroy](BarcodeScanner.md#destroy)
> * [bDestroyed](BarcodeScanner.md#bdestroyed)
> 
> ### Decode Barcodes
> <hr>
> * [onUnduplicatedRead](BarcodeScanner.md#onunduplicatedread)
> * [onFrameRead](BarcodeScanner.md#onframeread)
> * [decodeCurrentFrame](BarcodeScanner.md#decodecurrentframe)
> 
> ### Basic Interaction
> <hr>
> * [show](BarcodeScanner.md#show)
> * [hide](BarcodeScanner.md#hide)
> * [pauseScan](BarcodeScanner.md#pausescan)
> * [resumeScan](BarcodeScanner.md#resumescan)
> 
> ### Scan Settings
> <hr>
> * [bPlaySoundOnSuccessfulRead](BarcodeScanner.md#bplaysoundonsuccessfulread)
> * [soundOnSuccessfullRead](BarcodeScanner.md#soundonsuccessfullread)
> * [bVibrateOnSuccessfulRead](BarcodeScanner.md#bvibrateonsuccessfulread)
> * [vibrateDuration](BarcodeScanner.md#vibrateduration)
> * [singleFrameMode](BarcodeScanner.md#singleFrameMode)
> * [getScanSettings](BarcodeScanner.md#getscansettings)
> * [updateScanSettings](BarcodeScanner.md#updatescansettings)
> 
> ### UI Control
> <hr>
> * [getUIElement](BarcodeScanner.md#getuielement)
> * [setUIElement](BarcodeScanner.md#setuielement)
> * [defaultUIElementURL](BarcodeScanner.md#defaultuielementurl)
> * [barcodeFillStyle](BarcodeScanner.md#barcodefillstyle)
> * [barcodeLineWidth](BarcodeScanner.md#barcodelinewidth)
> * [barcodeStrokeStyle](BarcodeScanner.md#barcodestrokestyle)
> * [regionMaskFillStyle](BarcodeScanner.md#regionmaskfillstyle)
> * [regionMaskLineWidth](BarcodeScanner.md#regionmasklinewidth)
> * [regionMaskStrokeStyle](BarcodeScanner.md#regionmaskstrokestyle)
> 
> ### Camera Control
> <hr>
> * [getAllCameras](BarcodeScanner.md#getallcameras)
> * [getCurrentCamera](BarcodeScanner.md#getcurrentcamera)
> * [setCurrentCamera](BarcodeScanner.md#setcurrentcamera)
> * [getResolution](BarcodeScanner.md#getresolution)
> * [setResolution](BarcodeScanner.md#setresolution)
> * [getVideoSettings](BarcodeScanner.md#getvideosettings)
> * [updateVideoSettings](BarcodeScanner.md#updatevideosettings)
> * [openVideo](BarcodeScanner.md#openvideo)
> * [showVideo](BarcodeScanner.md#showvideo)
> * [play](BarcodeScanner.md#play)
> * [onPlayed](BarcodeScanner.md#onplayed)
> * [pause](BarcodeScanner.md#pause)
> * [stop](BarcodeScanner.md#stop)
> 
> ### Advanced Camera Control
> <hr>
> * [getCapabilities](BarcodeScanner.md#getcapabilities)
> * [getCameraSettings](BarcodeScanner.md#getcamerasettings)
> * [setFrameRate](BarcodeScanner.md#setframerate)
> * [setColorTemperature](BarcodeScanner.md#setcolortemperature)
> * [setExposureCompensation](BarcodeScanner.md#setexposurecompensation)
> * [setZoom](BarcodeScanner.md#setzoom)
> * [turnOnTorch](BarcodeScanner.md#turnontorch)
> * [turnOffTorch](BarcodeScanner.md#turnofftorch)

## License Control

The library provides flexible licensing options with the support of the following APIs

<div class="doc-card-prefix doc-card-list-prefix"></div>

> * [licenseServer](#licenseserver)
> * [organizationID](#organizationid)
> * [handshakeCode](#handshakecode)
> * [sessionPassword](#sessionpassword)
> * [deviceFriendlyName](#devicefriendlyname)
> * [productKeys](#productkeys)

## Initialization Control

The following static methods and properties help to set up the runtime environment for the library.

<div class="doc-card-prefix doc-card-list-prefix"></div>

> * [_bUseFullFeature](#_busefullfeature)
> * [engineResourcePath](#engineresourcepath)
> * [loadWasm](#loadwasm)
> * [isLoaded](#isloaded)
> * [version](#version)
> * [detectEnvironment](#detectenvironment)

## Interfaces and Enums

In order to make the code more predictable and readable, the library defines a series of supporting interfaces and enumerations.

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ### Interfaces
> <hr>
> * [LocalizationResult](interface/LocalizationResult.md)
> * [RegionDefinition](interface/RegionDefinition.md)
> * [RuntimeSettings](interface/RuntimeSettings.md)
> * [ScannerPlayCallbackInfo](interface/ScannerPlayCallbackInfo.md)
> * [ScanSettings](interface/ScanSettings.md)
> * [TextResult](interface/TextResult.md)
> * [VideoDeviceInfo](interface/VideoDeviceInfo.md)
>
> ### Enums
> <hr>
> * [EnumBarcodeColourMode](enum/EnumBarcodeColourMode.md)
> * [EnumBarcodeComplementMode](enum/EnumBarcodeComplementMode.md)
> * [EnumBarcodeFormat](enum/EnumBarcodeFormat.md)
> * [EnumBarcodeFormat_2](enum/EnumBarcodeFormat_2.md)
> * [EnumBinarizationMode](enum/EnumBinarizationMode.md)
> * [EnumClarityCalculationMethod](enum/EnumClarityCalculationMethod.md)
> * [EnumClarityFilterMode](enum/EnumClarityFilterMode.md)
> * [EnumColourClusteringMode](enum/EnumColourClusteringMode.md)
> * [EnumColourConversionMode](enum/EnumColourConversionMode.md)
> * [EnumConflictMode](enum/EnumConflictMode.md)
> * [EnumDeblurMode](enum/EnumDeblurMode.md)
> * [EnumDeformationResistingMode](enum/EnumDeformationResistingMode.md)
> * [EnumDPMCodeReadingMode](enum/EnumDPMCodeReadingMode.md)
> * [EnumErrorCode](enum/EnumErrorCode.md)
> * [EnumGrayscaleTransformationMode](enum/EnumGrayscaleTransformationMode.md)
> * [EnumImagePixelFormat](enum/EnumImagePixelFormat.md)
> * [EnumImagePreprocessingMode](enum/EnumImagePreprocessingMode.md)
> * [EnumIMResultDataType](enum/EnumIMResultDataType.md)
> * [EnumIntermediateResultSavingMode](enum/EnumIntermediateResultSavingMode.md)
> * [EnumIntermediateResultType](enum/EnumIntermediateResultType.md)
> * [EnumLocalizationMode](enum/EnumLocalizationMode.md)
> * [EnumPDFReadingMode](enum/EnumPDFReadingMode.md)
> * [EnumQRCodeErrorCorrectionLevel](enum/EnumQRCodeErrorCorrectionLevel.md)
> * [EnumRegionPredetectionMode](enum/EnumRegionPredetectionMode.md)
> * [EnumResultCoordinateType](enum/EnumResultCoordinateType.md)
> * [EnumResultType](enum/EnumResultType.md)
> * [EnumScaleUpMode](enum/EnumScaleUpMode.md)
> * [EnumTerminatePhase](enum/EnumTerminatePhase.md)
> * [EnumTextFilterMode](enum/EnumTextFilterMode.md)
> * [EnumTextResultOrderMode](enum/EnumTextResultOrderMode.md)
> * [EnumTextureDetectionMode](enum/EnumTextureDetectionMode.md)

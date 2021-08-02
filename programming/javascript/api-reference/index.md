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

# Dynamsoft Barcode Reader for  - API Reference - JavaScript

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

### Create and Destroy Instances

| API Name | Description |
|---|---|
| [createInstance](BarcodeReader.md#createinstance) | Creates a `BarcodeReader` instance. |
| [destroy](BarcodeReader.md#destroy) | Destroies the BarcodeReader instance. |
| [bDestroyed](BarcodeReader.md#bdestroyed) | Indicates whether the instance has been destroyed. |

### Decode Barcodes

| API Name | Description |
|---|---|
| [decode](BarcodeReader.md#decode) | Decodes barcodes from an image. |
| [decodeBase64String](BarcodeReader.md#decodebase64string) | Decodes barcodes from a base64-encoded image (with or without MIME). |
| [decodeUrl](BarcodeReader.md#decodeurl) | Decodes barcodes from an image specified by its URL. |
| [decodeBuffer](BarcodeReader.md#decodebuffer) | Decodes barcodes from raw image data. |

### Change Settings

| API Name | Description |
|---|---|
| [getRuntimeSettings](BarcodeReader.md#getruntimesettings) | Returns the current runtime settings. |
| [updateRuntimeSettings](BarcodeReader.md#updateruntimesettings) | Updates runtime settings with a given struct or a preset template. |
| [resetRuntimeSettings](BarcodeReader.md#resetruntimesettings) | Resets all parameters to default values. |
| [getModeArgument](BarcodeReader.md#getmodeargument) | Returns the argument value for the specified mode parameter. |
| [setModeArgument](BarcodeReader.md#setmodeargument) | Sets the argument value for the specified mode parameter. |

### Auxiliary

| API Name | Description |
|---|---|
| [bSaveOriCanvas](BarcodeReader.md#bsaveoricanvas) | Whether to save the original image into a &lt;canvas&gt; element. |
| [oriCanvas](BarcodeReader.md#oricanvas) | An `HTMLCanvasElement` that holds the original image. |

<br />

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


### Create and Destroy Instances

| API Name | Description |
|---|---|
| [createInstance](#createinstance) | Creates a `BarcodeScanner` instance. |
| [destroy](#destroy) | Destroys the `BarcodeScanner` instance. |
| [bDestroyed](#bdestroyed) | Indicates whether the instance has been destroyed. |

### Decode Barcodes

| API Name | Description |
|---|---|
| [onUnduplicatedRead](#onunduplicatedread) | This event is triggered when a new, unduplicated barcode is found. |
| [onFrameRead](#onframeread) | This event is triggered after the library finishes scanning a frame. |
| [decodeCurrentFrame](#decodecurrentframe) | Scans the current frame of the video for barcodes. |

### Basic Interaction

| API Name | Description |
|---|---|
| [show](#show) | Binds and shows UI, opens the camera and starts decoding. |
| [hide](#hide) | Stops decoding, releases camera and unbinds UI. |
| [pauseScan](#pausescan) | Pauses the decoding process. |
| [resumeScan](#resumescan) | Resumes the decoding process. |

### Scan Settings

| API Name | Description |
|---|---|
| [bPlaySoundOnSuccessfulRead](#bplaysoundonsuccessfulread) | Whether and when to play sound on barcode recognition. |
| [soundOnSuccessfullRead](#soundonsuccessfullread) | Specifies the sound to play on barcode recognition. |
| [bVibrateOnSuccessfulRead](#bvibrateonsuccessfulread) | Whether and when to vibrate on barcode recognition. |
| [vibrateDuration](#vibrateduration) | Returns or sets how long the vibration lastsin milliseconds.  |
| [singleFrameMode](#singleFrameMode) |  |
| [getScanSettings](#getscansettings) | Returns the current scan settings. |
| [updateScanSettings](#updatescansettings) | Changes scan settings with the object passed in. |

### UI Control

| API Name | Description |
|---|---|
| [getUIElement](#getuielement) | Returns the HTML element that is used by the `BarcodeScanner` instance. |
| [setUIElement](#setuielement) | Specifies an HTML element for the `BarcodeScanner` instance to use as its UI. |
| [defaultUIElementURL](#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [barcodeFillStyle](#barcodefillstyle) | Specifies the color used inside the shape which highlights a found barcode.  |
| [barcodeStrokeStyle](#barcodestrokestyle) | Specifies the color used to paint the outline of the shape which highlights a found barcode. |
| [barcodeLineWidth](#barcodelinewidth) | Specifies the line width of the outline of the shape which highlights a found barcode. |
| [regionMaskFillStyle](#regionmaskfillstyle) | Specifies the color used in the square-loop shape between the actual scanning area and the boundary of the video input. |
| [regionMaskStrokeStyle](#regionmaskstrokestyle) | Specifies the color used to paint the outline of the scanning region. |
| [regionMaskLineWidth](#regionmasklinewidth) | Specifies the width of the outline of the scanning region. |

### Camera Control

| API Name | Description |
|---|---|
| [getAllCameras](#getallcameras) | Returns infomation of all available cameras on the device. |
| [getCurrentCamera](#getcurrentcamera) | Returns information about the current camera. |
| [setCurrentCamera](#setcurrentcamera) | Chooses a camera as the video source. |
| [getResolution](#getresolution) | Returns the resolution of the current video input. |
| [setResolution](#setresolution) | Sets the resolution of the current video input. |
| [getVideoSettings](#getvideosettings) | Returns the current video settings. |
| [updateVideoSettings](#updatevideosettings) | Changes the video input. |
| [openVideo](#openvideo) | Binds UI and opens the camera to show the video stream. |
| [showVideo](#showvideo) | Similar to openVideo but will also show the UI Element if it is hidden. |
| [play](#play) | Play the video if it is already open but paused or stopped. |
| [onPlayed](#onplayed) | This event is triggered when the video stream starts playing. |
| [pause](#pause) | Pauses the video without releasing the camera. |
| [stop](#stop) | Stops the video and releases the camera. |

### Advanced Camera Control

| API Name | Description |
|---|---|
| [getCapabilities](#getcapabilities) | Inspects and returns the capabilities of the current camera. |
| [getCameraSettings](#getcamerasettings) | Returns the current values for each constrainable property of the current camera. |
| [setFrameRate](#setframerate) | Adjusts the frame rate. |
| [setColorTemperature](#setcolortemperature) | Adjusts the color temperature. |
| [setExposureCompensation](#setexposurecompensation) | Sets the exposure compensation index. |
| [setZoom](#setzoom) | Sets the exposure compensation index. |
| [turnOnTorch](#turnontorch) | Turns on the torch/flashlight. |
| [turnOffTorch](#turnofftorch) | Turns off the torch/flashlight. |

## License Control

The library provides flexible licensing options with the support of the following APIs

* [licenseServer](LicenseControl.md#licenseserver)
* [organizationID](LicenseControl.md#organizationid)
* [handshakeCode](LicenseControl.md#handshakecode)
* [sessionPassword](LicenseControl.md#sessionpassword)
* [deviceFriendlyName](LicenseControl.md#devicefriendlyname)
* [productKeys](LicenseControl.md#productkeys)

## Initialization Control

The following static methods and properties help to set up the runtime environment for the library.

* [_bUseFullFeature](InitializationControl.md#_busefullfeature)
* [engineResourcePath](InitializationControl.md#engineresourcepath)
* [loadWasm](InitializationControl.md#loadwasm)
* [isLoaded](InitializationControl.md#isloaded)
* [version](InitializationControl.md#version)
* [detectEnvironment](InitializationControl.md#detectenvironment)

## Interfaces and Enums

In order to make the code more predictable and readable, the library defines a series of supporting interfaces and enumerations.

### Interfaces

* [LocalizationResult](interface/LocalizationResult.md)
* [RegionDefinition](interface/RegionDefinition.md)
* [RuntimeSettings](interface/RuntimeSettings.md)
* [ScannerPlayCallbackInfo](interface/ScannerPlayCallbackInfo.md)
* [ScanSettings](interface/ScanSettings.md)
* [TextResult](interface/TextResult.md)
* [VideoDeviceInfo](interface/VideoDeviceInfo.md)

### Enums

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

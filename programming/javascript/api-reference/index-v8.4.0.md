---
layout: default-layout
title: v8.4.0 Entry Page - Dynamsoft Barcode Reader JavaScript Edition API
description: This is the main page of Dynamsoft Barcode Reader JavaScript SDK API Reference.
keywords: BarcodeScanner, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
permalink: /programming/javascript/api-reference/index-v8.4.0.html
---

# JavaScript API Reference

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
| [createInstance]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#createinstance) | Creates a `BarcodeReader` instance. |
| [destroy]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#destroy) | Destroies the BarcodeReader instance. |
| [bDestroyed]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#bdestroyed) | Indicates whether the instance has been destroyed. |

### Decode Barcodes

| API Name | Description |
|---|---|
| [decode]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#decode) | Decodes barcodes from an image. |
| [decodeBase64String]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#decodebase64string) | Decodes barcodes from a base64-encoded image (with or without MIME). |
| [decodeUrl]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#decodeurl) | Decodes barcodes from an image specified by its URL. |
| [decodeBuffer]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#decodebuffer) | Decodes barcodes from raw image data. |

### Change Settings

| API Name | Description |
|---|---|
| [getRuntimeSettings]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#getruntimesettings) | Returns the current runtime settings. |
| [updateRuntimeSettings]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#updateruntimesettings) | Updates runtime settings with a given struct or a preset template. |
| [resetRuntimeSettings]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#resetruntimesettings) | Resets all parameters to default values. |
| [getModeArgument]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#getmodeargument) | Returns the argument value for the specified mode parameter. |
| [setModeArgument]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#setmodeargument) | Sets the argument value for the specified mode parameter. |

### Auxiliary

| API Name | Description |
|---|---|
| [bSaveOriCanvas]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#bsaveoricanvas) | Whether to save the original image into a &lt;canvas&gt; element. |
| [oriCanvas]({{ site.js }}api-reference/BarcodeReader-v8.4.0.html#oricanvas) | An `HTMLCanvasElement` that holds the original image. |

<br />

## BarcodeScanner

A barcode scanner object gets access to a camera via the [MediaDevices](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices) interface, then uses its built-in UI to show the camera input and perform continuous barcode scanning on the incoming frames.

The default built-in UI of each barcode scanner is defined in the file "dbr.scanner.html". If used directly, the UI will fit the entire page and sit on top. There are a few ways to customize it, read more on how to [Customize the UI](../user-guide/#customize-the-ui).

Although a barcode scanner is designed to scan barcodes from a video input, it also supports a special mode called [singleFrameMode]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#singleframemode) which allows the user to select a still image or take a shot with the mobile camera for barcode scanning.

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
| [createInstance]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#createinstance) | Creates a `BarcodeScanner` instance. |
| [destroy]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#destroy) | Destroys the `BarcodeScanner` instance. |
| [bDestroyed]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#bdestroyed) | Indicates whether the instance has been destroyed. |

### Decode Barcodes

| API Name | Description |
|---|---|
| [onUnduplicatedRead]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#onunduplicatedread) | This event is triggered when a new, unduplicated barcode is found. |
| [onFrameRead]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#onframeread) | This event is triggered after the library finishes scanning a frame. |
| [decodeCurrentFrame]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#decodecurrentframe) | Scans the current frame of the video for barcodes. |

### Basic Interaction

| API Name | Description |
|---|---|
| [show]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#show) | Binds and shows UI, opens the camera and starts decoding. |
| [hide]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#hide) | Stops decoding, releases camera and unbinds UI. |
| [pauseScan]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#pausescan) | Pauses the decoding process. |
| [resumeScan]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#resumescan) | Resumes the decoding process. |

### Scan Settings

| API Name | Description |
|---|---|
| [bPlaySoundOnSuccessfulRead]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#bplaysoundonsuccessfulread) | Whether and when to play sound on barcode recognition. |
| [soundOnSuccessfullRead]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#soundonsuccessfullread) | Specifies the sound to play on barcode recognition. |
| [bVibrateOnSuccessfulRead]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#bvibrateonsuccessfulread) | Whether and when to vibrate on barcode recognition. |
| [vibrateDuration]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#vibrateduration) | Returns or sets how long the vibration lastsin milliseconds.  |
| [singleFrameMode]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#singleframemode) | Returns or sets whether to enable the singe-frame mode. | |
| [getScanSettings]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#getscansettings) | Returns the current scan settings. |
| [updateScanSettings]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#updatescansettings) | Changes scan settings with the object passed in. |

### UI Control

| API Name | Description |
|---|---|
| [getUIElement]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#getuielement) | Returns the HTML element that is used by the `BarcodeScanner` instance. |
| [setUIElement]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#setuielement) | Specifies an HTML element for the `BarcodeScanner` instance to use as its UI. |
| [defaultUIElementURL]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [barcodeFillStyle]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#barcodefillstyle) | Specifies the color used inside the shape which highlights a found barcode.  |
| [barcodeStrokeStyle]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#barcodestrokestyle) | Specifies the color used to paint the outline of the shape which highlights a found barcode. |
| [barcodeLineWidth]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#barcodelinewidth) | Specifies the line width of the outline of the shape which highlights a found barcode. |
| [regionMaskFillStyle]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#regionmaskfillstyle) | Specifies the color used in the square-loop shape between the actual scanning area and the boundary of the video input. |
| [regionMaskStrokeStyle]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#regionmaskstrokestyle) | Specifies the color used to paint the outline of the scanning region. |
| [regionMaskLineWidth]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#regionmasklinewidth) | Specifies the width of the outline of the scanning region. |

### Camera Control

| API Name | Description |
|---|---|
| [getAllCameras]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#getallcameras) | Returns infomation of all available cameras on the device. |
| [getCurrentCamera]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#getcurrentcamera) | Returns information about the current camera. |
| [setCurrentCamera]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#setcurrentcamera) | Chooses a camera as the video source. |
| [getResolution]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#getresolution) | Returns the resolution of the current video input. |
| [setResolution]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#setresolution) | Sets the resolution of the current video input. |
| [getVideoSettings]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#getvideosettings) | Returns the current video settings. |
| [updateVideoSettings]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#updatevideosettings) | Changes the video input. |
| [openVideo]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#openvideo) | Binds UI and opens the camera to show the video stream. |
| [showVideo]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#showvideo) | Similar to openVideo but will also show the UI Element if it is hidden. |
| [play]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#play) | Play the video if it is already open but paused or stopped. |
| [onPlayed]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#onplayed) | This event is triggered when the video stream starts playing. |
| [pause]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#pause) | Pauses the video without releasing the camera. |
| [stop]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#stop) | Stops the video and releases the camera. |

### Advanced Camera Control

| API Name | Description |
|---|---|
| [getCapabilities]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#getcapabilities) | Inspects and returns the capabilities of the current camera. |
| [getCameraSettings]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#getcamerasettings) | Returns the current values for each constrainable property of the current camera. |
| [setFrameRate]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#setframerate) | Adjusts the frame rate. |
| [setColorTemperature]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#setcolortemperature) | Adjusts the color temperature. |
| [setExposureCompensation]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#setexposurecompensation) | Sets the exposure compensation index. |
| [setZoom]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#setzoom) | Sets the exposure compensation index. |
| [turnOnTorch]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#turnontorch) | Turns on the torch/flashlight. |
| [turnOffTorch]({{ site.js }}api-reference/BarcodeScanner-v8.4.0.html#turnofftorch) | Turns off the torch/flashlight. |

## License Control

The library provides flexible licensing options with the support of the following APIs

* [licenseServer]({{ site.js }}api-reference/LicenseControl-v8.4.0.html#licenseserver)
* [organizationID]({{ site.js }}api-reference/LicenseControl-v8.4.0.html#organizationid)
* [handshakeCode]({{ site.js }}api-reference/LicenseControl-v8.4.0.html#handshakecode)
* [sessionPassword]({{ site.js }}api-reference/LicenseControl-v8.4.0.html#sessionpassword)
* [deviceFriendlyName]({{ site.js }}api-reference/LicenseControl-v8.4.0.html#devicefriendlyname)
* [productKeys]({{ site.js }}api-reference/LicenseControl-v8.4.0.html#productkeys)

## Initialization Control

The following static methods and properties help to set up the runtime environment for the library.

* [_bUseFullFeature]({{ site.js }}api-reference/InitializationControl-v8.4.0.html#_busefullfeature)
* [engineResourcePath]({{ site.js }}api-reference/InitializationControl-v8.4.0.html#engineresourcepath)
* [loadWasm]({{ site.js }}api-reference/InitializationControl-v8.4.0.html#loadwasm)
* [isLoaded]({{ site.js }}api-reference/InitializationControl-v8.4.0.html#isloaded)
* [version]({{ site.js }}api-reference/InitializationControl-v8.4.0.html#version)
* [detectEnvironment]({{ site.js }}api-reference/InitializationControl-v8.4.0.html#detectenvironment)

## Interfaces and Enums

In order to make the code more predictable and readable, the library defines a series of supporting interfaces and enumerations.

### Interfaces

* [LocalizationResult](interface/LocalizationResult.md)
* [Region](interface/Region.md)
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

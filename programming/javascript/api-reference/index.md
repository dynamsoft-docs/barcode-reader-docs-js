---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - v9.0.2 Entry Page
description: Introduction to Dynamsoft Barcode Reader for JavaScript & WebAssembly. Simply integrate the library to run it on all major modern browsers.
keywords: BarcodeScanner, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
permalink: /programming/javascript/api-reference/
---

# JavaScript API Reference

The Dynamsoft Barcode Reader JavaScript library comes with two primary classes: `BarcodeReader` and `BarcodeScanner`.

## BarcodeReader

A low-level barcode reader that processes still images and returns barcode results. The following code snippet shows its basic usage:

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
let results = await reader.decode(imageSource);
for(let result of results){
  console.log(result.barcodeText);
}
```

The APIs for this class include:

### Create and Destroy Instances

| API Name | Description |
|---|---|
| [createInstance()](BarcodeReader.md#createinstance) | Creates a `BarcodeReader` instance. |
| [destroyContext()](BarcodeReader.md#destroycontext) | Destroys the `BarcodeReader` instance. |
| [isContextDestroyed()](BarcodeReader.md#iscontextdestroyed) | Returns whether the instance has been destroyed. |

### Decode Barcodes on a Single Image

| API Name | Description |
|---|---|
| [decode()](BarcodeReader.md#decode) | Decodes barcodes from an image. |
| [decodeBase64String()](BarcodeReader.md#decodebase64string) | Decodes barcodes from a base64-encoded image (with or without MIME). |
| [decodeUrl()](BarcodeReader.md#decodeurl) | Decodes barcodes from an image specified by its URL. |
| [decodeBuffer()](BarcodeReader.md#decodebuffer) | Decodes barcodes from raw image data. |

### Decode Barcodes on multiple images from an Image Source

| API Name | Description |
|---|---|
| [setImageSource](BarcodeReader.md#setimagesource) | Sets an image source for continous scanning. |
| [onUniqueRead](BarcodeReader.md#onuniqueread) | This event is triggered when a new, unduplicated barcode is found. |
| [onImageRead](BarcodeReader.md#onimageread) | This event is triggered after the library finishes scanning an image. |
| [startScanning()](BarcodeReader.md#startscanning) | Starts continuous scanning of incoming images. |
| [stopScanning()](BarcodeReader.md#stopscanning) | Stops continuous scanning. |
| [pauseScanning()](BarcodeReader.md#pausescanning) | Pause continuous scanning but keep the video stream. |
| [resumeScanning()](BarcodeReader.md#resumescanning) | Resumes continuous scanning. |
| [getScanSettings()](BarcodeReader.md#getscansettings) | Returns the current scan settings. |
| [updateScanSettings()](BarcodeReader.md#updatescansettings) | Changes scan settings with the object passed in. |

### Change Settings

| API Name | Description |
|---|---|
| [getRuntimeSettings()](BarcodeReader.md#getruntimesettings) | Returns the current runtime settings. |
| [updateRuntimeSettings()](BarcodeReader.md#updateruntimesettings) | Updates runtime settings with a given struct or a preset template. |
| [resetRuntimeSettings()](BarcodeReader.md#resetruntimesettings) | Resets all parameters to default values. |
| [outputRuntimeSettingsToString()](BarcodeReader.md#outputruntimesettingstostring) | Return the current RuntimeSettings in the form of a string. |
| [getModeArgument()](BarcodeReader.md#getmodeargument) | Returns the argument value for the specified mode parameter. |
| [setModeArgument()](BarcodeReader.md#setmodeargument) | Sets the argument value for the specified mode parameter. |

### Auxiliary

| API Name | Description |
|---|---|
| [ifSaveOriginalImageInACanvas](BarcodeReader.md#ifsaveoriginalimageinacanvas) | Whether to save the original image into a &lt;canvas&gt; element. |
| [getOriginalImageInACanvas()](BarcodeReader.md#getoriginalimageinacanvas) | Returns an `HTMLCanvasElement` that holds the original image. |

<br />

## BarcodeScanner

A barcode scanner object gets access to a camera via the [MediaDevices](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices) interface, then uses its built-in UI to show the camera input and performs continuous barcode scanning on the incoming frames.

The default built-in UI of each barcode scanner is defined in the file `dbr.ui.html` and it fits the entire page and sits on top. Read more on how to [Customize the UI](../user-guide/#customize-the-ui).

Although a barcode scanner is designed to scan barcodes from a video input, it also supports a special mode called [singleFrameMode](BarcodeScanner.md#singleframemode) which allows users to select a still image or take a shot with the camera for barcode scanning.

The following code snippet shows the basic usage of the `BarcodeScanner` class.

```js
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
scanner.onUniqueRead = txt => console.log(txt);
await scanner.show();
```

The `BarcodeScanner` is a child class of [BarcodeReader](./BarcodeReader.md) and inherits all its methods and properties. APIs not directly inherited include: 

### Create and Destroy Instances

| API Name | Description |
|---|---|
| [createInstance()](BarcodeScanner.md#createinstance) | Creates a `BarcodeScanner` instance. |
| [destroyContext()](BarcodeScanner.md#destroycontext) | Destroys the `BarcodeScanner` instance. |
| [isContextDestroyed()](BarcodeScanner.md#iscontextdestroyed) | Returns whether the instance has been destroyed. |

### Decode Barcodes

| API Name | Description |
|---|---|
| [onUniqueRead](BarcodeScanner.md#onUniqueRead) | This event is triggered when a new, unduplicated barcode is found. |
| [onFrameRead](BarcodeScanner.md#onframeread) | This event is triggered after the library finishes scanning a frame. |

### Basic Interaction

| API Name | Description |
|---|---|
| [show()](BarcodeScanner.md#show) | Binds and shows UI, opens the camera and starts decoding. |
| [hide()](BarcodeScanner.md#hide) | Stops decoding, releases camera, hides and unbinds UI. |
| [open()](BarcodeScanner.md#open) | Binds UI, opens the camera and starts decoding. Meant for use with frameworks like Angular, Vue, React. |
| [close()](BarcodeScanner.md#close) | Stops decoding, releases camera and unbinds UI. Meant for use with frameworks like Angular, Vue, React. |

### Scan Settings

| API Name | Description |
|---|---|
| [singleFrameMode](BarcodeScanner.md#singleframemode) | Returns or sets whether to enable the singe-frame mode. |
| [getScanSettings()](BarcodeScanner.md#getscansettings) | Returns the current scan settings. |
| [updateScanSettings()](BarcodeScanner.md#updatescansettings) | Changes scan settings with the object passed in. |

### UI Control

| API Name | Description |
|---|---|
| [getUIElement()](BarcodeScanner.md#getuielement) | Returns the HTML element that is used by the `BarcodeScanner` instance. |
| [setUIElement()](BarcodeScanner.md#setuielement) | Specifies an HTML element for the `BarcodeScanner` instance to use as its UI. |
| [defaultUIElementURL](BarcodeScanner.md#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [barcodeFillStyle](BarcodeScanner.md#barcodefillstyle) | Specifies the color used inside the shape which highlights a found barcode.  |
| [barcodeStrokeStyle](BarcodeScanner.md#barcodestrokestyle) | Specifies the color used to paint the outline of the shape which highlights a found barcode. |
| [barcodeLineWidth](BarcodeScanner.md#barcodelinewidth) | Specifies the line width of the outline of the shape which highlights a found barcode. |
| [regionMaskFillStyle](BarcodeScanner.md#regionmaskfillstyle) | Specifies the color used in the square-loop shape between the actual scanning area and the boundary of the video input. |
| [regionMaskStrokeStyle](BarcodeScanner.md#regionmaskstrokestyle) | Specifies the color used to paint the outline of the scanning region. |
| [regionMaskLineWidth](BarcodeScanner.md#regionmasklinewidth) | Specifies the width of the outline of the scanning region. |
| [setVideoFit()](BarcodeScanner.md#setvideofit) | Sets the `object-fit` CSS property of the video element. |
| [ifShowScanRegionMask](BarcodeScanner.md#ifshowscanregionmask) | Whether to show or hide the scan region mask. |

### Camera Control

| API Name | Description |
|---|---|
| [getAllCameras()](BarcodeScanner.md#getallcameras) | Returns infomation of all available cameras on the device. |
| [getCurrentCamera()](BarcodeScanner.md#getcurrentcamera) | Returns information about the current camera. |
| [setCurrentCamera()](BarcodeScanner.md#setcurrentcamera) | Chooses a camera as the video source. |
| [getResolution()](BarcodeScanner.md#getresolution) | Returns the resolution of the current video input. |
| [setResolution()](BarcodeScanner.md#setresolution) | Sets the resolution of the current video input. |
| [getVideoSettings()](BarcodeScanner.md#getvideosettings) | Returns the current video settings. |
| [updateVideoSettings()](BarcodeScanner.md#updatevideosettings) | Changes the video input. |

### Video Decoding Process Control

| API Name | Description |
|---|---|
| [play()](BarcodeScanner.md#play) | Play the video if it is already open but paused or stopped. |
| [onPlayed](BarcodeScanner.md#onplayed) | This event is triggered when the video stream starts playing. |
| [pauseScan()](BarcodeScanner.md#pausescan) | Pauses the decoding process. |
| [resumeScan()](BarcodeScanner.md#resumescan) | Resumes the decoding process. |
| [pause()](BarcodeScanner.md#pause) | Pauses the video without releasing the camera. |
| [stop()](BarcodeScanner.md#stop) | Stops the video and releases the camera. |

### Advanced Camera Control

| API Name | Description |
|---|---|
| [getCapabilities()](BarcodeScanner.md#getcapabilities) | Inspects and returns the capabilities of the current camera. |
| [getCameraSettings()](BarcodeScanner.md#getcamerasettings) | Returns the current values for each constrainable property of the current camera. |
| [getFrameRate()](BarcodeScanner.md#getframerate) | Returns the real-time frame rate. |
| [setFrameRate()](BarcodeScanner.md#setframerate) | Adjusts the frame rate. |
| [setColorTemperature()](BarcodeScanner.md#setcolortemperature) | Adjusts the color temperature. |
| [setExposureCompensation()](BarcodeScanner.md#setexposurecompensation) | Sets the exposure compensation index. |
| [setFocus()](BarcodeScanner.md#setfocus) | Sets the focus mode and focus distance of the camera. |
| [getFocus()](BarcodeScanner.md#getfocus) | Gets the focus mode and focus distance of the camera. |
| [setZoom()](BarcodeScanner.md#setzoom) | Sets the exposure compensation index. |
| [turnOnTorch()](BarcodeScanner.md#turnontorch) | Turns on the torch/flashlight. |
| [turnOffTorch()](BarcodeScanner.md#turnofftorch) | Turns off the torch/flashlight. |

## License Control

* [license](LicenseControl.md#license)
* [deviceFriendlyName](LicenseControl.md#devicefriendlyname)

## Initialization Control

The following static methods and properties help to set up the runtime environment for the library:

* [engineResourcePath](InitializationControl.md#engineresourcepath)
* [loadWasm()](InitializationControl.md#loadwasm)
* [isWasmLoaded()](InitializationControl.md#iswasmloaded)
* [version](InitializationControl.md#version)
* [detectEnvironment()](InitializationControl.md#detectenvironment)

## Interfaces and Enums

In order to make the code more predictable and readable, the library defines a series of supporting interfaces and enumerations:

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

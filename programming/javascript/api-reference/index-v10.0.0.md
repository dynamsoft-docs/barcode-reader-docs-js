---
layout: default-layout
title: API Reference Index - Dynamsoft Barcode Reader JavaScript Edition
description: Introduction to Dynamsoft Barcode Reader JavaScript Edition. Integrate once, and run the library on all major modern browsers.
keywords: BarcodeReader, api reference, javascript, js, barcode decoding
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
permalink: /programming/javascript/api-reference/index-v10.0.0.html
---

# JavaScript API Reference

Dynamsoft Barcode Reader JavaScript Edition v10.0.0 is built based on the [Dynamsoft Capture Vision Architecture](). This is the index page for the API reference docs which will help you learn and use the SDK in your application.

## Sample Usage

Before introducing the APIs, let us take a look at how the SDK is used with a simple code snippet:

```js
await Dynamsoft.License.LicenseManager.initLicense('DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9');
let router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
let imageSource = await Dynamsoft.DCE.CameraEnhancer.createInstance();
router.setInput(imageSource);
router.addResultReceiver({
    onDecodedBarcodesReceived: (results)=> {
      let n = results.barcodesResultItems.length;
      for (let i = 0; i < n; i++){
        let result = results.barcodesResultItems[i];
        console.log("Barcode No. " + (i+1));
        console.log("Format: " + result.formatString);
        console.log("Barcode Text: " + result.text);
      }
    }
});
router.startCapturing();
```

As shown in the code, there are a few components involved in making a barcode reading application. We will introduce these components and their APIs below.

## License

Dynamsoft Barcode Reader requires a license to work. To license the SDK, use the class `LicenseManager`.

### LicenseManager

This class has the following methods:

| API Name                                                            | Description                            |
| ------------------------------------------------------------------- | -------------------------------------- |
| *static* [initLicense()](BarcodeReader.md#createinstance)           | Creates a `BarcodeReader` instance.    |
| *static* [setDeviceFriendlyName()](BarcodeReader.md#destroycontext) | Destroys the `BarcodeReader` instance. |

### Interfaces

- [LicenseVerificationListener]()

## Capture Vision Router

Capture Vision Router is the fundamental module in the [Dynamsoft Capture Vision Architecture](). Read more on its [major responsibilities](architecture/#capture-vision-router).

## CaptureVisionRouter

This class has the following methods:

| API Name                                                            | Description                            |
| ------------------------------------------------------------------- | -------------------------------------- |
| *static* [createInstance()](BarcodeReader.md#createinstance)           | Creates a `BarcodeReader` instance.    |
| *static* [setDeviceFriendlyName()](BarcodeReader.md#destroycontext) | Destroys the `BarcodeReader` instance. |

### Interfaces

### Enums

## Initialization Control

The following static methods and properties help to set up the runtime environment for the library:

* [engineResourcePath](InitializationControl.md#engineresourcepath)
* [loadWasm()](InitializationControl.md#loadwasm)
* [isWasmLoaded()](InitializationControl.md#iswasmloaded)
* [version](InitializationControl.md#version)
* [detectEnvironment()](InitializationControl.md#detectenvironment)
* [onWarning](InitializationControl.md#onwarning)

## Interfaces and Enums

In order to make the code more predictable and readable, the library defines a series of supporting interfaces and enumerations:

### Interfaces

* [LocalizationResult](interface/LocalizationResult.md)
* [Region](interface/Region.md)
* [RuntimeSettings](interface/RuntimeSettings.md)
* [FurtherModes](interface/FurtherModes.md)
* [ScannerPlayCallbackInfo](interface/ScannerPlayCallbackInfo.md)
* [ScanSettings](interface/ScanSettings.md)
* [TextResult](interface/TextResult.md)
* [VideoDeviceInfo](interface/VideoDeviceInfo.md)
* [imagesource](interface/imagesource.md)
* [dsimage](interface/dsimage.md)

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
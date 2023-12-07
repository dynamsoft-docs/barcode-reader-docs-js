---
layout: default-layout
title: BarcodeReader Module - Dynamsoft Barcode Reader JavaScript Edition API
description: This page introduces the BarcodeReader module in Dynamsoft Barcode Reader JavaScript Edition.
keywords: barcode reader, module, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---
<!-- 2.0.20 -- Updated on 11/28/2023-->

# BarcodeReader Module

The BarcodeReader module is defined in the namespace `Dynamsoft.DBR`. It includes a class named "BarcodeReaderModule" along with various interfaces and enumerations.

## BarcodeReaderModule Class

This class defines common functionality in the `BarcodeReader` module. At present, there is only one API.

| API Name                                                             | Description                                      |
| -------------------------------------------------------------------- | ------------------------------------------------ |
| `static` [getVersion()](./barcode-reader-module-class.md#getversion) | Returns the version of the BarcodeReader module. |

## Interfaces

* [SimplifiedBarcodeReaderSettings](./interfaces/simplified-barcode-reader-settings.md)
* [BarcodeDetails](./interfaces/barcode-details.md)
* [OneDCodeDetails](./interfaces/oned-code-details.md)
* [QRCodeDetails](./interfaces/qr-code-details.md)
* [PDF417Details](./interfaces/pdf417-details.md)
* [DataMatrixDetails](./interfaces/datamatrix-details.md)
* [AztecDetails](./interfaces/aztec-details.md)
* [LocalizedBarcodeElement](./interfaces/localized-barcode-element.md)
* [DecodedBarcodeElement](./interfaces/decoded-barcode-element.md)
* [ExtendedBarcodeResult](./interfaces/extended-barcode-result.md)
* [CandidateBarcodeZonesUnit](./interfaces/candidate-barcode-zones-unit.md)
* [LocalizedBarcodesUnit](./interfaces/localized-barcodes-unit.md)
* [ScaledUpBarcodeImageUnit](./interfaces/scaled-up-barcode-image-unit.md)
* [DeformationResistedBarcodeImageUnit](./interfaces/deformation-resisted-barcode-image-unit.md)
* [ComplementedBarcodeImageUnit](./interfaces/complemented-barcode-image-unit.md)
* [DecodedBarcodesUnit](./interfaces/decoded-barcodes-unit.md)
* [BarcodeResultItem](./interfaces/barcode-result-item.md)
* [DecodedBarcodesResult](./interfaces/decoded-barcodes-result.md)

## Enums

* [EnumBarcodeFormat]({{ site.dcv_enumerations }}barcode-reader/barcode-format.html?lang=js)
* [EnumLocalizationMode]({{ site.dcv_enumerations }}barcode-reader/localization-mode.html?lang=js)
* [EnumDeblurMode]({{ site.dcv_enumerations }}barcode-reader/deblur-mode.html?lang=js)
* [EnumQRCodeErrorCorrectionLevel]({{ site.dcv_enumerations }}barcode-reader/qr-code-error-correction-level.html?lang=js)
* [EnumExtendedBarcodeResultType]({{ site.dcv_enumerations }}barcode-reader/extended-barcode-result-type.html?lang=js)

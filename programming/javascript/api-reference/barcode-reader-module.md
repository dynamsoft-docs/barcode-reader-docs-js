---
layout: default-layout
title: BarcodeReader Module - Dynamsoft Barcode Reader JavaScript Edition API
description: This page introduces the BarcodeReader module in Dynamsoft Barcode Reader JavaScript Edition.
keywords: barcode reader, module, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# DynamsoftBarcodeReader Module

The BarcodeReader module is defined in the namespace `Dynamsoft.DBR`. It includes a class named "BarcodeReaderModule" along with various interfaces and enumerations.

## BarcodeReaderModule Class

This class defines common functionality in the `BarcodeReader` module. At present, there is only one API.

| API Name                                                             | Description                                      |
| -------------------------------------------------------------------- | ------------------------------------------------ |
| `static` [getVersion()](./barcode-reader-module-class.md#getversion) | Returns the version of the BarcodeReader module. |

## Interfaces

* [AztecDetails](./interfaces/aztec-details.md)
* [BarcodeDetails](./interfaces/barcode-details.md)
* [BarcodeResultItem](./interfaces/barcode-result-item.md)
* [CandidateBarcodeZone](./interfaces/candidate-barcode-zone.md)
* [CandidateBarcodeZonesUnit](./interfaces/candidate-barcode-zones-unit.md)
* [ComplementedBarcodeImageUnit](./interfaces/complemented-barcode-image-unit.md)
* [DataMatrixDetails](./interfaces/datamatrix-details.md)
* [DecodedBarcodeElement](./interfaces/decoded-barcode-element.md)
* [DecodedBarcodesResult](./interfaces/decoded-barcodes-result.md)
* [DecodedBarcodesUnit](./interfaces/decoded-barcodes-unit.md)
* [DeformationResistedBarcode](./interfaces/deformation-resisted-barcode.md)
* [DeformationResistedBarcodeImageUnit](./interfaces/deformation-resisted-barcode-image-unit.md)
* [ExtendedBarcodeResult](./interfaces/extended-barcode-result.md)
* [LocalizedBarcodeElement](./interfaces/localized-barcode-element.md)
* [LocalizedBarcodesUnit](./interfaces/localized-barcodes-unit.md)
* [OneDCodeDetails](./interfaces/oned-code-details.md)
* [PDF417Details](./interfaces/pdf417-details.md)
* [QRCodeDetails](./interfaces/qr-code-details.md)
* [ScaledUpBarcodeImageUnit](./interfaces/scaled-up-barcode-image-unit.md)
* [SimplifiedBarcodeReaderSettings](./interfaces/simplified-barcode-reader-settings.md)

## Enums

* [EnumBarcodeFormat]({{ site.dcvb_enums }}barcode-reader/barcode-format.html?lang=js)
* [EnumDeblurMode]({{ site.dcvb_enums }}barcode-reader/deblur-mode.html?lang=js)
* [EnumExtendedBarcodeResultType]({{ site.dcvb_enums }}barcode-reader/extended-barcode-result-type.html?lang=js)
* [EnumLocalizationMode]({{ site.dcvb_enums }}barcode-reader/localization-mode.html?lang=js)
* [EnumQRCodeErrorCorrectionLevel]({{ site.dcvb_enums }}barcode-reader/qr-code-error-correction-level.html?lang=js)

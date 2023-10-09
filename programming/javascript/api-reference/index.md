---
layout: default-layout
title: Dynamsoft Document Normalizer JavaScript API Reference - Main Page
description: This is the main page of Dynamsoft Document Normalizer for JavaScript SDK API Reference.
keywords: DocumentNormalizer, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
breadcrumbText: API Reference
noTitleIndex: true

---

# API Reference - JavaScript

## Dynamsoft License

- [`LicenseManager`]({{ site.dcv_js_api }}license/license-manager.html)
<!--- [`LicenseVerificationListener`]({{ site.dcv_js_api }}license/license-verification-listener.html)-->

## Capture Vision Router

- [`Instantiate`]({{ site.dcv_js_api }}capture-vision-router/instantiate.html)
- [`Single-File Processing`]({{ site.dcv_js_api }}capture-vision-router/single-file-processing.html)
- [`Multiple-File Processing`]({{ site.dcv_js_api }}capture-vision-router/multiple-file-processing.html)
- [`Settings`]({{ site.dcv_js_api }}capture-vision-router/settings.html)
<!--- [`Intermediate Result`]({{ site.dcv_js_api }}capture-vision-router/intermediate-result.html)-->

## Dynamsoft Core - Input

- [`ImageSourceAdapter`]({{ site.dcv_js_api }}core/basic-structures/image-source-adapter.html)

## Dynamsoft Core - BasicStructures

- [`Arc`]({{ site.dcv_js_api }}core/basic-structures/arc.html)
- [`Contour`]({{ site.dcv_js_api }}core/basic-structures/contour.html)
- [`Corner`]({{ site.dcv_js_api }}core/basic-structures/corner.html)
- [`DSFile`]({{ site.dcv_js_api }}core/basic-structures/ds-file.html)
- [`DSImageData`]({{ site.dcv_js_api }}core/basic-structures/ds-image-data.html)
- [`DSRect`]({{ site.dcv_js_api }}core/basic-structures/ds-rect.html)
- [`Edge`]({{ site.dcv_js_api }}core/basic-structures/edge.html)
- [`FileImageTag`]({{ site.dcv_js_api }}core/basic-structures/file-image-tag.html)
- [`ImageTag`]({{ site.dcv_js_api }}core/basic-structures/image-tag.html)
- [`LineSegment`]({{ site.dcv_js_api }}core/basic-structures/line-segment.html)
- [`PDFReadingParameter`]({{ site.dcv_js_api }}core/basic-structures/pdf-reading-parameter.html)
- [`Point`]({{ site.dcv_js_api }}core/basic-structures/point.html)
- [`Polygon`]({{ site.dcv_js_api }}core/basic-structures/polygon.html)
- [`Quadrilateral`]({{ site.dcv_js_api }}core/basic-structures/quadrilateral.html)
- [`Rect`]({{ site.dcv_js_api }}core/basic-structures/rect.html)
- [`VideoFrameTag`]({{ site.dcv_js_api }}core/basic-structures/video-frame-tag.html)


## Dynamsoft Core - IntermediateResults

- [`BinaryImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/binary-image-unit.html)
<!--- [`CandidateQuadEdgesUnit`]({{ site.ddn_js_api }}candidate-quad-edges-unit.html)-->
- [`ColourImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/colour-image-unit.html)
- [`ContoursUnit`]({{ site.dcv_js_api }}core/intermediate-results/contours-unit.html)
<!--- [`CornersUnit`]({{ site.ddn_js_api }}corners-unit.html)-->
<!--- [`DetectedQuadElement`]({{ site.ddn_js_api }}detected-quad-element.html)-->
<!--- [`DetectedQuadsUnit`]({{ site.ddn_js_api }}detected-quads-unit.html)-->
- [`EnhancedGrayscaleImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/enhanced-grayscale-image-unit.html)
- [`GrayscaleImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/grayscale-image-unit.html)
- [`IntermediateResultExtraInfo`]({{ site.dcv_js_api }}core/intermediate-results/intermediate-result-extra-info.html)
<!--- [`IntermediateResultManager`]({{ site.dcv_js_api }}core/intermediate-results/intermediate-result-manager.html)-->
- [`IntermediateResultReceiver`]({{ site.dcv_js_api }}core/intermediate-results/intermediate-result-receiver.html)
- [`IntermediateResultUnit`]({{ site.dcv_js_api }}core/intermediate-results/intermediate-result-unit.html)
- [`IntermediateResult`]({{ site.dcv_js_api }}core/intermediate-results/intermediate-result.html)
- [`LineSegmentsUnit`]({{ site.dcv_js_api }}core/intermediate-results/line-segments-unit.html)
<!--- [`LongLinesUnit`]({{ site.ddn_js_api }}long-lines-unit.html)-->
<!--- [`NormalizedImageElement`]({{ site.ddn_js_api }}normalized-image-element.html)-->
<!--- [`NormalizedImageUnit`]({{ site.ddn_js_api }}normalized-images-unit.html)-->
- [`ObservationParameters`]({{ site.dcv_js_api }}core/intermediate-results/observation-parameters.html)
- [`PredetectedRegionElement`]({{ site.dcv_js_api }}core/intermediate-results/predetected-region-element.html)
- [`PredetectedRegionsUnit`]({{ site.dcv_js_api }}core/intermediate-results/predetected-regions-unit.html)
- [`RegionObjectElement`]({{ site.dcv_js_api }}core/intermediate-results/region-object-element.html)
- [`ScaledDownColourImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/scaled-down-colour-image-unit.html)
- [`TextRemovedBinaryImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/text-removed-binary-image-unit.html)
- [`TextZonesUnit`]({{ site.dcv_js_api }}core/intermediate-results/text-zones-unit.html)
- [`TextureDetectionResultUnit`]({{ site.dcv_js_api }}core/intermediate-results/texture-detection-result-unit.html)
- [`TextureRemovedBinaryImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/texture-removed-binary-image-unit.html)
- [`TextureRemovedGrayscaleImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/texture-removed-grayscale-image-unit.html)
- [`TransformedGrayscaleImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/transformed-grayscale-image-unit.html)
- [`LocalizedBarcodeElement`]({{ site.js_api }}localized-barcode-element.html)
- [`DecodedBarcodeElement`]({{ site.js_api }}decoded-barcode-element.html)
- [`ExtendedBarcodeResult`]({{ site.js_api }}extended-barcode-result.html)
- [`CandidateBarcodeZonesUnit`]({{ site.js_api }}candidate-barcode-zones-unit.html)
- [`LocalizedBarcodesUnit`]({{ site.js_api }}localized-barcodes-unit.html)
- [`ScaledUpBarcodeImageUnit`]({{ site.js_api }}scaled-up-barcode-image-unit.html)
- [`DeformationResistedBarcodeImageUnit`]({{ site.js_api }}deformation-resisted-barcode-image-unit.html)
- [`ComplementedBarcodeImageUnit`]({{ site.js_api }}complemented-barcode-image-unit.html)
- [`DecodedBarcodesUnit`]({{ site.js_api }}decoded-barcodes-unit.html)


## Dynamsoft Core - FinalResult

- [`CapturedResult`]({{ site.dcv_js_api }}core/basic-structures/captured-result.html)
- [`CapturedResultFilter`]({{ site.dcv_js_api }}core/basic-structures/captured-result-filter.html)
- [`CapturedResultItem`]({{ site.dcv_js_api }}core/basic-structures/captured-result-item.html)
- [`CapturedResultReceiver`]({{ site.dcv_js_api }}core/basic-structures/captured-result-receiver.html)
<!--- [`DetectedQuadResultItem`]({{ site.ddn_js_api }}detected-quad-result-item.html)-->
<!--- [`DetectedQuadsResult`]({{ site.ddn_js_api }}detected-quads-result.html)-->
<!--- [`NormalizedImageResultItem`]({{ site.ddn_js_api }}normalized-image-result-item.html)-->
<!--- [`NormalizedImagesResult`]({{ site.ddn_js_api }}normalized-images-result.html)-->
- [`OriginalImageResultItem`]({{ site.dcv_js_api }}core/basic-structures/original-image-result-item.html)
- [`BarcodeResultItem`]({{ site.js_api }}barcode-result-item.html)
- [`DecodedBarcodesResult`]({{ site.js_api }}decoded-barcodes-result.html)

## Dynamsoft Core - Detailed Barcode Results

- [`AztecDetails`]({{ site.js_api }}aztec-details.html)
- [`BarcodeDetails`]({{ site.js_api }}barcode-details.html)
- [`DataMatrixDetails`]({{ site.js_api }}data-matrix-details.html)
- [`OneDCodeDetails`]({{ site.js_api }}oned-code-details.html)
- [`PDF417Details`]({{ site.js_api }}pdf417-details.html)
- [`QRCodeDetails`]({{ site.js_api }}qr-code-details.html)

## Dynamsoft Utility

- [`ImageManager`]({{ site.dcv_js_api }}utility/image-manager.html)
- [`MultiFrameResultCrossFilter`]({{ site.dcv_js_api }}utility/multi-frame-result-cross-filter.html)

## Enumerations

- [`BarcodeFormat`]({{ site.dcv_enumerations }}barcode-reader/barcode-format.html?lang=js)
- [`BufferOverflowProtectionMode`]({{ site.dcv_enumerations }}core/buffer-overflow-protection-mode.html?lang=js)
- [`CapturedResultItemType`]({{ site.dcv_enumerations }}core/captured-result-item-type.html?lang=js)
- [`CaptureState`]({{ site.dcv_enumerations }}capture-vision-router/capture-state.html?lang=js)
- [`CornerType`]({{ site.dcv_enumerations }}core/corner-type.html?lang=js)
- [`DeblurMode`]({{ site.dcv_enumerations }}barcode-reader/deblur-mode.html?lang=js)
- [`ErrorCode`]({{ site.dcv_enumerations }}core/error-code.html?lang=js)
- [`ExtendedBarcodeResultType`]({{ site.dcv_enumerations }}barcode-reader/extended-barcode-result-type.html?lang=js)
- [`GrayscaleTransformationMode`]({{ site.dcv_enumerations }}core/grayscale-transformation-mode.html?lang=js)
- [`image-capture-distance-mode`]({{ site.dcv_enumerations }}core/image-capture-distance-mode.html?lang=js)
- [`ImagePixelFormat`]({{ site.dcv_enumerations }}core/image-pixel-format.html?lang=js)
- [`ImageSourceState`]({{ site.dcv_enumerations }}core/image-source-state.html?lang=js)
- [`ImageTagType`]({{ site.dcv_enumerations }}core/image-tag-type.html?lang=js)
- [`IntermediateResultUnitType`]({{ site.dcv_enumerations }}core/intermediate-result-unit-type.html?lang=js)
- [`LocalizationMode`]({{ site.dcv_enumerations }}barcode-reader/localization-mode.html?lang=js)
<!--- [`MappingStatus`]({{ site.enums }}code-parser/mapping-status.html?lang=js)-->
- [`PDFReadingMode`]({{ site.dcv_enumerations }}core/pdf-reading-mode.html?lang=js)
- [`QRCodeErrorCorrectionLevel`]({{ site.dcv_enumerations }}barcode-reader/qr-code-error-correction-level.html?lang=js)
- [`RegionObjectElementType`]({{ site.dcv_enumerations }}core/region-object-element-type.html?lang=js)
- [`SectionType`]({{ site.dcv_enumerations }}core/section-type.html?lang=js)
- [`TargetType`]({{ site.dcv_enumerations }}core/target-type.html?lang=js)
<!--- [`ValidationStatus`]({{ site.enums }}code-parser/validation-status.html?lang=js)-->
<!--- [`video-frame-quality.html`]({{ site.enums }}core/video-frame-quality.html?lang=js)-->
- [`ColourChannelUsageType`]({{ site.dcv_enumerations }}core/colour-channel-usage-type.html?lang=js)
---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - BarcodeReader
description: This page shows the BarcodeReader Class of Dynamsoft Barcode Reader JavaScript SDK.
keywords: RuntimeSettings, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: RuntimeSettings
---


# RuntimeSettings

## Attributes

| Attribute | Type |
|---------- | ---- |
| [`barcodeFormatIds`](#barcodeformatids) | *number &#124; [EnumBarcodeFormat](../enum/EnumBarcodeFormat.md)* |
| [`barcodeFormatIds_2`](#barcodeformatids_2) | *int* |
| [`expectedBarcodesCount`](#expectedbarcodescount) | *int* |
| [`deblurLevel`](#deblurlevel) | *int* |
| [`localizationModes`](#localizationmodes) | *number &#124; [EnumLocalizationMode](../enum/EnumLocalizationMode.md)* |
| [`region`](#region) | [`RegionDefinition`](RegionDefinition.md) |
| [`minBarcodeTextLength`](#minbarcodetextlength) | *int* |
| [`minResultConfidence`](#minresultconfidence) | *int* |
| [`resultCoordinateType`](#resultcoordinatetype) | [`ResultCoordinateType`]({{ site.enumerations }}result-enums.html#resultcoordinatetype) |
| [`furtherModes`](#furthermodes) | [`FurtherModes`](FurtherModes.md) |
| [`deblurModes`](#deblurmodes) | [`DeblurMode`]({{ site.enumerations }}parameter-mode-enums.html#deblurmode)\[10\] | 
| [`timeout`](#timeout) | *int* |

### barcodeFormatIds
Sets the formats of the barcode in BarcodeFormat group 1 to be read. Barcode formats in BarcodeFormat group 1 can be combined.
```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED &#124; Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE;
await reader.updateRuntimeSettings(runtimeSettings);
```
<br />

### barcodeFormatIds_2
Sets the formats of the barcode in BarcodeFormat group 2 to be read. Barcode formats in BarcodeFormat group 1 can be combined.
```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.barcodeFormatIds_2 = Dynamsoft.DBR.EnumBarcodeFormat_2.BF2_POSTALCODE &#124; Dynamsoft.DBR.EnumBarcodeFormat_2.BF2_POSTNET;
await reader.updateRuntimeSettings(runtimeSettings);
```
<br />

### expectedBarcodesCount
Sets the number of barcodes expected to be detected for each image.

**Value Range** [0, 0x7fffffff]

**Default Value** 0

**Remarks**       
  * 0: means Unknown and it will return the result of the first successful [localization mode](../../..//parameters/scenario-settings/how-to-set-localization-modes.md) attempt.
  * 1: try to find one barcode. If one barcode is found, the library will stop the localization process and perform barcode decoding. 
  * n: try to find n barcodes. If the library only finds m (m < n) barcode, it will try different algorithms till n barcodes are found or all algorithms are tried.
```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.expectedBarcodesCount = 3;
await reader.updateRuntimeSettings(runtimeSettings);
```
<br />

### deblurLevel
Sets the degree of blurriness of the barcode.

**Value Range** [0, 9]

**Default Value** 9
```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.deblurLevel = 9;
await reader.updateRuntimeSettings(runtimeSettings);
```
<br />

### localizationModes
Sets the mode and priority for localization algorithms.

**Value Range:** Please see [EnumLocalizationMode](../enum/EnumLocalizationMode.md)

**Default Value** [LM_CONNECTED_BLOCKS, LM_SCAN_DIRECTLY, LM_STATISTICS, LM_LINES, LM_SKIP, LM_SKIP, LM_SKIP, LM_SKIP]

```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.localizationModes = [Dynamsoft.DBR.EnumLocalizationMode
.LM_CONNECTED_BLOCKS, Dynamsoft.DBR.EnumLocalizationMode.LM_SCAN_DIRECTLY, Dynamsoft.DBR.EnumLocalizationMode.LM_LINES, 0, 0, 0, 0, 0];
await reader.updateRuntimeSettings(runtimeSettings);
```
<br />

### region
Sets the [RegionDefinition](RegionDefinition.md) including the regionTop, regionLeft, regionRight, regionBottom and regionMeasuredByPercentage. To learn more about how the region parameters work, please refer to the [RegionDefinition section of the Parameters Template](https://www.dynamsoft.com/barcode-reader/parameters/structure-and-interfaces-of-parameters.html?ver=latest#regiondefinition-and-how-it-works)
```js
// Use a region positioned at the centre with 50% width and 50% height of the frame
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.region.regionLeft = 25;
runtimeSettings.region.regionTop = 25;
runtimeSettings.region.regionRight = 75;
runtimeSettings.region.regionBottom = 75;
runtimeSettings.region.regionMeasuredByPercentage = true;
await reader.updateRuntimeSettings(runtimeSettings);
```
> Experimental feature:
>
> When using the  [BarcodeScanner](../BarcodeScanner.md) class, `region` can be an array. For example `region = [r0, r1, r2]`, 0th frame use `r0`, 1st use `r1`, 2nd use `r2`, 3rd use `r0`, and then loop like this. 
>
> ```js
> let runtimeSettings = await reader.getRuntimeSettings();
> runtimeSettings.region = [
>   null, // full image
>   {regionLeft:25,regionTop:25,regionRight:75,regionBottom:75,regionMeasuredByPercentage:true}, // center 50% 
>   {regionLeft:5,regionTop:45,regionRight:95,regionBottom:55,regionMeasuredByPercentage:true}, // width 90%, height 10% 
> ];
> await reader.updateRuntimeSettings(runtimeSettings);
> ```
<br />

### minBarcodeTextLength
Sets the minimum barcode text length that the SDK will detect. If a barcode's text is lower than this value, the SDK will reject that result. A value of 0 means there is no limitation on the barcode text length.

**Value Range** [0, 0x7fffffff]

**Default Value** 0
```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.minBarcodeTextLength = 6; // reject any barcodes that have text longer than 6 characters
await reader.updateRuntimeSettings(runtimeSettings);
```
<br />

### minResultConfidence
Sets the minimum confidence of the barcode result that the SDK will accept. If a barcode result's confidence is lower than this value, the result is rejected. A value of 0 means there is no limitation on the result confidence.

**Value Range** [0, 0x7fffffff]

**Default Value** 0
```js
let runtimeSettings = await reader.getRuntimeSettings();
runtimeSettings.minResultConfidence = 30; // reject any barcodes that have a confidence lower than 30
await reader.updateRuntimeSettings(runtimeSettings);
```
<br />

* barcodeFormatIds: *number &#124; [EnumBarcodeFormat](../enum/EnumBarcodeFormat.md)*

  > Sets the formats of the barcode in BarcodeFormat group 1 to be read. Barcode formats in BarcodeFormat group 1 can be combined.
  > ```js
  > let runtimeSettings = await reader.getRuntimeSettings();
  > runtimeSettings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED &#124; Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE;
  > await reader.updateRuntimeSettings(runtimeSettings);
  > ```

  <br />

### resultCoordinateType
Determines whether the result coordinates 
* barcodeFormatIds_2: *number &#124; [EnumBarcodeFormat_2](../enum/EnumBarcodeFormat_2.md)*

  > Sets the formats of the barcode in BarcodeFormat group 2 to be read. Barcode formats in BarcodeFormat group 1 can be combined.

  <br />

* deblurLevel: *number*

  > Sets the degree of blurriness of the barcode.

  <br />

* expectedBarcodesCount: *number*

  > Sets the number of barcodes expected to be detected for each image.

  <br />

* localizationModes: *number&#91;&#93; &#124; [EnumLocalizationMode](../enum/EnumLocalizationMode.md)&#91;&#93;*

  > Sets the mode and priority for localization algorithms.

  <br />

* minResultConfidence: *number*

  <br />

* region: *[RegionDefinition](RegionDefinition.md) &#124; [RegionDefinition](RegionDefinition.md)&#91;&#93;*

  > Sets the region definition including the regionTop, regionLeft, regionRight, regionBottom and regionMeasuredByPercentage.
  >
  > ```js
  > // Use a region of center 50% width and 50% height
  > let runtimeSettings = await reader.getRuntimeSettings();
  > runtimeSettings.region.regionLeft = 25;
  > runtimeSettings.region.regionTop = 25;
  > runtimeSettings.region.regionRight = 75;
  > runtimeSettings.region.regionBottom = 75;
  > runtimeSettings.region.regionMeasuredByPercentage = true;
  > await reader.updateRuntimeSettings(runtimeSettings);
  > ```
  >
  > Experimental feature:
  >
  > In [BarcodeScanner](../BarcodeScanner.md), `region` can be an array. For example `region = [r0, r1, r2]`, 0th frame use `r0`, 1st use `r1`, 2nd use `r2`, 3rd use `r0`, and then loop like this. 
  >
  > ```js
  > let runtimeSettings = await reader.getRuntimeSettings();
  > runtimeSettings.region = [
  >   null, // full image
  >   {regionLeft:25,regionTop:25,regionRight:75,regionBottom:75,regionMeasuredByPercentage:true}, // center 50% 
  >   {regionLeft:5,regionTop:45,regionRight:95,regionBottom:55,regionMeasuredByPercentage:true}, // width 90%, height 10% 
  > ];
  > await reader.updateRuntimeSettings(runtimeSettings);
  > ```

  <br />

* resultCoordinateType: *number &#124; [EnumResultCoordinateType](../enum/EnumResultCoordinateType.md)*

  <br />

* timeout: *number*

  > Sets the maximum amount of time (in milliseconds) that should be spent searching for a barcode per page. 
  > It does not include the time taken to load/decode an image (Tiff, PNG, etc) from disk into memory.

  <br />

Some advanced parameters are not listed. See [C++ PublicRuntimeSettings](https://www.dynamsoft.com/barcode-reader/programming/c-cplusplus/struct/PublicRuntimeSettings.html?src=cpp&&ver=latest) for more info.



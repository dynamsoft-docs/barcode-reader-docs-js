---
layout: default-layout
title: How to Reduce Duplicate Scans and Optimize Scan Usage
keywords: Dynamsoft Barcode Reader, FAQ, JavaScript, tech basic, scans, duplicate, re-reads
description: How to Reduce Duplicate Scans and Optimize Scan Usage
needAutoGenerateSidebar: false
---

# How to Reduce Duplicate Scans and Optimize Scan Usage?

[<< Back to FAQ index](index.md)

## Version 10
If you're experiencing more scans usage than expected with the barcode reading SDK, use the below strategies to address this issue effectively:

### 1. Donot count identical Result
With version 10 and above of the DBR SDK, the `enableResultDeduplication` is set to forget a result 3 seconds after it is first received. During this time frame, if an identical result appears, it is ignored. If you want to forget the identical result for more duration you can use the setDuplicateForgetTime function as well with `enableResultDeduplication`. 

```javascript
// Filter out unchecked and duplicate results.
const filter = new MultiFrameResultCrossFilter();
// Filter out unchecked barcodes 
filter.enableResultCrossVerification(
    EnumCapturedResultItemType.CRIT_BARCODE,
    true
);  
// Filter out duplicate barcodes within 3 seconds by default.
filter.enableResultDeduplication(
    EnumCapturedResultItemType.CRIT_BARCODE,
    true
); 
// Filter out duplicate barcodes within 5 seconds.
filter.setDuplicateForgetTime(
    EnumCapturedResultItemType.CRIT_BARCODE,
    5000
);
await router.addResultFilter(filter);
```
**_NOTE:_** - setSuplicateForgetTime can be set upto 10 seconds.

### 2. Limit Barcode Formats: 
If you're specifically scanning a particular barcode format, consider limiting the barcode format options to prevent other formats from being decoded and counted unnecessarily.

you can limit the barcode formats in two ways:

- set the barcode format using the `getSimplifiedSettings`
```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.barcodeSettings.barcodeFormatIds =
  Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED |
  Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE ;
await router.updateSettings("ReadSingleBarcode", settings);
```

- to set the barcode format using the template check out the [template section]({{site.dcvb_js_api}}capture-vision-router/settings.html)


Implementing these steps can help streamline your barcode scanning process, reduce unnecessary scans, and optimize resource usage effectively.








---
layout: default-layout
title: Why am I unable to scan an Aztec code in the helloworld sample?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, hello world sample, aztec code
description: Why am I unable to scan an Aztec code in the helloworld sample?
needAutoGenerateSidebar: false
---

# Why am I unable to scan an Aztec code in the helloworld sample?

[<< Back to FAQ index](index.md)
# Version 10
```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.barcodeSettings.barcodeFormatIds =
  Dynamsoft.DBR.EnumBarcodeFormat.BF_AZTEC;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

## For version 8 and version 9

The reason for this is that the JavaScript edition defaults to the `compact engine`, rather than the `full engine`. The compact engine currently only supports `1D`, `QR`, `PDF417`, and `DataMatrix` codes.

To switch to the full engine, please call the following before creating the `BarcodeReader/BarcodeScanner` instance:

```javascript
Dynamsoft.DBR.BarcodeScanner._bUseFullFeature = true;
```

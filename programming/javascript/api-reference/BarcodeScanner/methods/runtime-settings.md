---
layout: default-layout
title: BarcodeScanner Runtime Settings Methods - Dynamsoft Barcode Reader JavaScript Edition API
description: This page shows BarcodeScanner Runtime Settings Methods of Dynamsoft Barcode Reader JavaScript SDK.
keywords: updateRuntimeSettings, runtime settings methods, BarcodeScanner, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: false
permalink: /programming/javascript/api-reference/BarcodeScanner/methods/runtime-settings.html
---
<!--NOTE, This page is used until version 8.2.3-->

> This page is applicable to version 8.2.3

# Javascript API Reference - `BarcodeScanner` Runtime Settings Methods

| Method               | Description |
|----------------------|-------------|
| [updateRuntimeSettings()](#updateruntimesettings) | Modify and update the current runtime settings. |

---

## updateRuntimeSettings

Update the runtime settings with a given object or use the string `speed`, `balance`, or `coverage` to use our preset settings for `BarcodeScanner`. The default setting is `speed`. Overrides [BarcodeReader.UpdateRuntimeSettings](../../BarcodeReader/methods/parameter-and-runtime-settings.md#updateruntimesettings).

```javascript
updateRuntimeSettings(settings) returns Promise
```

### Parameters

`settings` [*RuntimeSettings*](../interfaces.md#runtimesettings) | *string* 

### Return Value

`Promise<void>`

### Sample

```javascript
await scanner.updateRuntimeSettings('balance');
let settings = await scanner.getRuntimeSettings();
settings.barcodeFormatIds = Dynamsoft.EnumBarcodeFormat.BF_ONED;
await scanner.updateRuntimeSettings(settings);
```

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

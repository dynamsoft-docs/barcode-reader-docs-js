---
layout: default-layout
title: BarcodeReader Parameter and Runtime Settings Methods - Dynamsoft Barcode Reader JavaScript Edition API
description: This page shows BarcodeReader Parameter and Runtime Settings methods of Dynamsoft Barcode Reader JavaScript SDK.
keywords: getModeArgument, setModeArgument, getRuntimeSettings, resetRuntimeSettings, updateRuntimeSettings, parameter and runtime settings methods, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: false
permalink: /programming/javascript/api-reference/BarcodeReader/methods/parameter-and-runtime-settings.html
---
<!--NOTE, This page is used until version 8.2.3-->

> This page is applicable to version 8.2.3

# Javascript API Reference - `BarcodeReader` Parameter and Runtime Settings Methods

| Method               | Description |
|----------------------|-------------|
| [`getModeArgument()`](#getmodeargument) | Get argument value for the specified mode parameter. |
| [`setModeArgument()`](#setmodeargument) | Set argument value for the specified mode parameter. |
| [`getRuntimeSettings()`](#getruntimesettings) | Get current runtime settings. |
| [`resetRuntimeSettings()`](#resetruntimesettings) | Reset runtime settings to default. |
| [`updateRuntimeSettings()`](#updateruntimesettings) | Modify and update the current runtime settings. |

---

## getModeArgument

Get the argument value for the specified mode parameter.

```javascript
getModeArgument(modeName, index, argumentName) returns Promise
```

### Parameters

`modeName` *string*  
`index` *number*  
`argumentName` *string*

### Return Value

`Promise<string>`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## setModeArgument

Set the argument value for the specified mode parameter.

```javascript
setModeArgument(modeName, index, argumentName, argumentValue) returns Promise
```

### Parameters

- `modeName` *string*  
- `index` *number*  
- `argumentName` *string*  
- `argumentValue` *string*

### Return Value

`Promise<void>`

### Sample

```javascript
await reader.setModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy", "1");
```

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## getRuntimeSettings

Get the current runtime settings.

```javascript
getRuntimeSettings() returns Promise
```

### Return Value

Promise<[RuntimeSettings](../../global-interfaces.md#runtimesettings)>


### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## resetRuntimeSettings

Reset all runtime settings to default values.

```javascript
resetRuntimeSettings() returns Promise
```

### Return Value

`Promise<void>`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## updateRuntimeSettings

Update the runtime settings with a given object or use the string `speed`, `balance`, or `coverage` to use our preset settings for `BarcodeReader`. The default setting is `coverage`.

```javascript
updateRuntimeSettings(settings) returns Promise
```

### Parameters

`settings` [*RuntimeSettings*](../../global-interfaces.md#runtimesettings) | *string* 

### Return Value

`Promise<void>`

### Sample

```javascript
await reader.updateRuntimeSettings('balance');
let settings = await reader.getRuntimeSettings();
settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED;
await reader.updateRuntimeSettings(settings);
```

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)


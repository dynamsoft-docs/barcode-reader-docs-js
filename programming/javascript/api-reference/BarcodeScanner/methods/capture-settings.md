---
layout: default-layout
title: BarcodeScanner Capture Settings - Dynamsoft Barcode Reader JavaScript Edition API
description: This page shows BarcodeScanner Capture Settings of Dynamsoft Barcode Reader JavaScript SDK.
keywords: getCapabilities, getResolution, setResolution, getScanSettings, updateScanSettings, getVideoSettings, updateVideoSettings, setColorTemperature, setExposureCompensation, setFrameRate, setZoom, turnOffTorch, turnOnTorch, capture settings, BarcodeScanner, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: false
permalink: /programming/javascript/api-reference/BarcodeScanner/methods/capture-settings.html
---
<!--NOTE, This page is used until version 8.2.3-->

> This page is applicable to version 8.2.3

# Javascript API Reference - `BarcodeScanner` Capture Settings

| Method               | Description |
|----------------------|-------------|
| [getCapabilities()](#getcapabilities) | Get the camera capabilities. |
| [getResolution()](#getresolution) | Get current video resolution. |
| [setResolution()](#setresolution) | Set current video resolution. |
| [getScanSettings()](#getscansettings) | Get current scan settings. |
| [updateScanSettings()](#updatescansettings) | Modify and update scan settings. |
| [getVideoSettings()](#getvideosettings) | Get current video settings. |
| [updateVideoSettings()](#updatevideosettings) | Modify and update video settings. |
| [setColorTemperature()](#setcolortemperature) | Adjust the video colour temperature. |
| [setExposureCompensation()](#setexposurecompensation) | Adjust the video exposure level. |
| [setFrameRate()](#setframerate) | Adjust the video frame rate. |
| [setZoom()](#setzoom) | Adjust the video zoom ratio. |
| [turnOffTorch()](#turnofftorch) | Turn off the torch/flashlight. |
| [turnOnTorch()](#turnontorch) | Turn on the torch/flashlight. |

---

## getCapabilities

Get the camera capabilities.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```javascript
getCapabilities() returns MediaTrackCapabilities
```

### Return Value

`MediaTrackCapabilities`

### Example

```javascript
> scanner.getCapabilities()
< {
  "aspectRatio":{"max":3840,"min":0.000462962962962963},
  "colorTemperature": {max: 7000, min: 2850, step: 50},
  "deviceId":"1e...3af7",
  "exposureCompensation": {max: 2.0000040531158447, min: -2.0000040531158447, step: 0.16666699945926666},
  "exposureMode":["continuous","manual"],
  "facingMode":["environment"],
  "focusMode":["continuous","single-shot","manual"],
  "frameRate":{"max":30,"min":0},
  "groupId":"71...a935",
  "height":{"max":2160,"min":1},
  "resizeMode":["none","crop-and-scale"],
  "torch":true,
  "whiteBalanceMode":["continuous","manual"],
  "width":{"max":3840,"min":1},
  "zoom":{max: 606, min: 100, step: 2}
  }
 ```

### :+1: Tips and Tricks 

Check out the following APIs to modify your device capabilities (if supported).

- [setColorTemperature](#setcolortemperature) - Adjust the video colour temperature.  
- [setExposureCompensation](#setexposurecompensation) - Adjust the video exposure level.  
- [setFrameRate](#setframerate) - Adjust the video frame rate.  
- [setZoom](#setzoom) - Adjust the video zoom ratio.  
- [turnOffTorch](#turnofftorch) - Turn off the torch/flashlight.  
- [turnOnTorch](#turnontorch) -Turn on the torch/flashlight. 

## getResolution

Get current video resolution.

```javascript
getResolution() returns number[]
```

### Return Value

`number[]`

### Sample

```javascript
let rsl = await scanner.getResolution();
console.log(rsl.width + " x " + rsl.height);
```

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## setResolution

Set the camera resolution.

```javascript
setResolution(width, height) returns Promise
```

### Parameters

- `width` *number* | *number[]*
- `height` *number*  

### Return Value

<code>Promise<<a href="../interfaces.html#scannerplaycallbackinfo">ScannerPlayCallbackInfo</a>></code>

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## getScanSettings

Get current scan settings of `BarcodeScanner` and saves it into a struct.

```javascript
getScanSettings() returns Promise
```

### Return Value

<code>Promise<<a href="../interfaces.html#scansettings">ScanSettings</a>></code>

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## updateScanSettings

Modify and update scan settings.

```javascript
updateScanSettings(settings) returns Promise
```

### Parameters
`settings` [*`ScanSettings`*](../interfaces.md#scansettings)

### Return Value

`Promise<void>`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)


## getVideoSettings

Get current video settings of `BarcodeScanner` and saves it into a struct.

```javascript
getVideoSettings() returns MediaStreamConstraints
```

### Return Value

`MediaStreamConstraints`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## updateVideoSettings

Modify and update video settings.

```javascript
updateVideoSettings(MediaStreamConstraints) returns Promise
```

### Parameters
`MediaStreamConstraints` *any*

### Return Value

<code>Promise<<a href="../interfaces.html#scannerplaycallbackinfo">ScannerPlayCallbackInfo</a> | void></code>

### Sample

```javascript
await scanner.updateVideoSettings({ 
    video: { width: { ideal: 1280 }, 
             height: { ideal: 720 }, 
             facingMode: { ideal: 'environment' } 
    }
});
```

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## setColorTemperature

Adjust the video colour temperature.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.
> Check if this capability is supported by the camera using [getCapabilities](#getcapabilities).

```javascript
setColorTemperature(value) returns Promise
```

### Parameters

`value` *number*  

### Return Value

`Promise<void>`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## setExposureCompensation

Adjust the video exposure level.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.
> Check if this capability is supported by the camera using [getCapabilities](#getcapabilities).

```javascript
setExposureCompensation(value) returns Promise
```

### Parameters

`value` *number*  

### Return Value

`Promise<void>`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## setFrameRate

Adjust the video frame rate.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.
> Check if this capability is supported by the camera using [getCapabilities](#getcapabilities).

```javascript
setFrameRate(value) returns Promise
```

### Parameters

`value` *number*  

### Return Value

`Promise<void>`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## setZoom

Adjust the video zoom ratio.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.
> Check if this capability is supported by the camera using [getCapabilities](#getcapabilities).

```javascript
setZoom(value) returns Promise
```

### Parameters

`value` *number*  

### Return Value

`Promise<void>`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## turnOffTorch

Turn off the torch/flashlight.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.
> Check if this capability is supported by the camera using [getCapabilities](#getcapabilities).

```javascript
turnOffTorch() returns Promise
```

### Return Value

`Promise<void>`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## turnOnTorch

Turn on the torch/flashlight.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.
> Check if this capability is supported by the camera using [getCapabilities](#getcapabilities).

```javascript
turnOnTorch() returns Promise
```

### Return Value

`Promise<void>`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

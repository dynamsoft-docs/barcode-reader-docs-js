---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - BarcodeReader
description: This page shows the BarcodeReader Class of Dynamsoft Barcode Reader JavaScript SDK.
keywords: BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: BarcodeReader
---

# BarcodeReader for Images

A low-level barcode reader that processes still images and return barcode results. The following code snippet shows its basic usage.

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
let results = await reader.decode(imageSource);
for(let result of results){
  console.log(result.barcodeText);
}
```

<br />

## API Index

### Create and Destroy Instances

| API Name | Description |
|---|---|
| [createInstance](#createinstance) | Creates a `BarcodeReader` instance. |
| [destroy](#destroy) | Destroies the BarcodeReader instance. |
| [bDestroyed](#bdestroyed) | Indicates whether the instance has been destroyed. |

### Decode Barcodes

| API Name | Description |
|---|---|
| [decode](#decode) | Decodes barcodes from an image. |
| [decodeBase64String](#decodebase64string) | Decodes barcodes from a base64-encoded image (with or without MIME). |
| [decodeUrl](#decodeurl) | Decodes barcodes from an image specified by its URL. |
| [decodeBuffer](#decodebuffer) | Decodes barcodes from raw image data. |

### Change Settings

| API Name | Description |
|---|---|
| [getRuntimeSettings](#getruntimesettings) | Returns the current runtime settings. |
| [updateRuntimeSettings](#updateruntimesettings) | Updates runtime settings with a given struct or a preset template. |
| [resetRuntimeSettings](#resetruntimesettings) | Resets all parameters to default values. |
| [getModeArgument](#getmodeargument) | Returns the argument value for the specified mode parameter. |
| [setModeArgument](#setmodeargument) | Sets the argument value for the specified mode parameter. |

### Auxiliary

| API Name | Description |
|---|---|
| [bSaveOriCanvas](#bsaveoricanvas) | Whether to save the original image into a &lt;canvas&gt; element. |
| [oriCanvas](#oricanvas) | An `HTMLCanvasElement` that holds the original image. |

<br />

## Create and Destroy Instances

<br />

### createInstance

Creates a `BarcodeReader` instance.

**Syntax**

`static` createInstance&#40;&#41;: *Promise&lt;BarcodeReader&gt;*

**Parameters**

None.

**Return value**

A promise resolving to the created `BarcodeReader` object.

**Code snippet**

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
```

<br />

### destroy

Destroies the `BarcodeReader` instance. If your page needs to create new instances from time to time, don't forget to destroy unused old instances.

**Syntax**

destroy&#40;&#41;: *Promise&lt;void&gt;*

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code snippet**

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
// ... decode ...
reader.destroy();
```

<br />

### bDestroyed

Indicates whether the instance has been destroyed.

**Syntax**

bDestroyed: *boolean*

<br />

## Decode Barcodes

<br />

### decode

Decodes barcodes from an image. 

**Syntax**

decode &#40;source: *[Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob) &#124; [Buffer](https://nodejs.org/api/buffer.html#buffer_class_buffer) &#124; [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) &#124; [Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array) &#124; [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray)&#124; [HTMLImageElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement) &#124; [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement) &#124; [HTMLVideoElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLVideoElement)&#124; string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*
  
**Parameters**

`source`: specifies the image to decode. The supported image formats include `png`, `jpeg`, `bmp`, `gif` and a few others (some browsers support `webp`, `tif`). Also note that the image can be specified in a lot of ways including binary data, base64 string (with MIME), URL, etc.

**Return value**

A promise resolving to a `TextResult` object that contains all the barcode results found in this image.

**Code snippet**

```js
let results1 = await reader.decode(blob);
let results2 = await reader.decode(htmlImageElement);
let results3 = await reader.decode(url);
let results4 = await reader.decode(strBase64WithMime); // like `data:image/png;base64,iV************`
```

You can even use an `HTMLVideoElement` as the source. If the video is playing, the current frame will be decoded.

```js
let results;
try{
  // The current frame will be decoded.
  results = await reader.decode(htmlVideoElement);
}catch(ex){
  // If no frame in the video, throws an exception.   
}
```

**See also**

[BarcodeScanner](./BarcodeScanner.md) for continuous barcode decoding from a video.

<br />

### decodeBase64String

Decodes barcodes from a base64-encoded image (with or without MIME).

**Syntax**
decodeBase64String&#40;base64Str: *string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

**Parameters**

`base64Str`: specifies the image represented by a string.

**Return value**

A promise resolving to a `TextResult` object that contains all the barcode results found in this image.

**Code snippet**

```js
let results = await reader.decodeBase64String(strBase64); //e.g. `data:image/jpg;base64,Xfjshekk....` or `Xfjshekk...`.
for(let result of results){
  console.log(result.barcodeText);
}
```

<br />

### decodeUrl

Decodes barcodes from an image specified by its URL. Note that the image should either be from the same domain or has the 'Access-Control-Allow-Origin' header set to allow access from your current domain.

**Syntax**

decodeUrl&#40;url: *string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

**Parameters**

`url`: specifies the image with its URL.

**Return value**

A promise resolving to a `TextResult` object that contains all the barcode results found in this image.

**Code snippet**

```js
let results = await reader.decodeUrl("https://www.yourdomain.com/imageWithBarcodes.png");
for(let result of results){
    console.log(result.barcodeText);
}
```

<br />

### decodeBuffer

Decodes barcodes from raw image data.

**Syntax**

decodeBuffer&#40;buffer: *[Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array) &#124; [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray) &#124; [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) &#124; [Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob) &#124; [Buffer](https://nodejs.org/api/buffer.html#buffer_class_buffer),width: *number*, height: *number*, stride: *number*,format: *[EnumImagePixelFormat](./enum/EnumImagePixelFormat.md)*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

**Parameters**

`buffer`: specifies the image represented by a `Uint8Array`, `Uint8ClampedArray`, `ArrayBuffer`, `Blob` or `Buffer` object.

**Return value**

A promise resolving to a `TextResult` object that contains all the barcode results found in this image.

<br />

## Change Settings
 
<br />

### getRuntimeSettings

Returns the current runtime settings.

**Syntax**

getRuntimeSettings&#40;&#41;: *Promise&lt;[RuntimeSettings](./interface/RuntimeSettings.md)&gt;*

**Parameters**

None.

**Return value**

A promise resolving to a `RuntimeSettings` object that contains the settings for barcode reading.

**Code snippet**

```js
let settings = await reader.getRuntimeSettings();
settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE; // Decodes only QR code.
await reader.updateRuntimeSettings(settings);
```

**See also**

[RuntimeSettings](./interface/RuntimeSettings.md)

<br />

### updateRuntimeSettings

Updates runtime settings with a given struct or a preset template represented by one of the following strings
- `speed`: fast but may miss a few codes;
- `coverage`: slow but try to find all codes, this is the default setting for a `BarcodeReader` instance;
- `balance`: between `speed` and `coverage`;
- `single`: optimized for scanning one single barcode from a video input, this is supported only by the sub-class [`BarcodeScanner`](./BarcodeScanner.md) and is also the default setting for a `BarcodeScanner` instance.

**Syntax**

updateRuntimeSettings&#40;settings: *[RuntimeSettings](./interface/RuntimeSettings.md) &#124; string*&#41;: *Promise&lt;void&gt;*

**Parameters**

`settings`: a `RuntimeSettings` object that contains the new settings for barcode reading.

**Return value**

A promise that resolves when the operation succeeds.

**Code snippet**

```js
await reader.updateRuntimeSettings('balance');
let settings = await reader.getRuntimeSettings();
settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED;
await reader.updateRuntimeSettings(settings);
```

<br />

### resetRuntimeSettings

Resets all parameters to default values.

For a `BarcodeReader` instance, it is equivalent to setting the `coverage` template.

For a [`BarcodeScanner`](./BarcodeScanner.md) instance, it is equivalent to setting the `single` template.

**Syntax**

resetRuntimeSettings&#40;&#41;: *Promise&lt;void&gt;*

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code snippet**

```js
await reader.resetRuntimeSettings();
```

<br />

### getModeArgument

Returns the argument value for the specified mode parameter.

**Syntax**
getModeArgument&#40;modeName: *string*, index: *number*, argumentName: *string*&#41;: *Promise&lt;string&gt;*

**Parameters**

`modeName`: specifies the mode which contains one or multiple elements.
`index`: specifies an element of the mode by its index.
`argumentName`: specifies the argument.

**Return value**

A promise resolving to a string which represents the value of the argument.

**Code snippet**

```js
let argumentValue = await reader.getModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy");
```

**See also**

[C++ getModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#getmodeargument)

<br />

### setModeArgument

Sets the argument value for the specified mode parameter.

**Syntax**

setModeArgument&#40;modeName: *string*, index: *number*, argumentName: *string*, argumentValue: *string*&#41;: *Promise&lt;void&gt;*

**Parameters**

`modeName`: specifies the mode which contains one or multiple elements.
`index`: specifies an element of the mode by its index.
`argumentName`: specifies the argument.
`argumentValue`: specifies the value.

**Return value**

A promise that resolves when the operation succeeds.

**Code snippet**

```js
await reader.setModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy", "1");
```

**See also**

[C++ setModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#setmodeargument)

<br />

## Auxiliary

<br />

### bSaveOriCanvas

Whether to save the original image into a &lt;canvas&gt; element. The original image refers to the actual image the library tried to read barcodes from.

Note that the result is an *HTMLCanvasElement* element and you can insert it into the DOM to show the image.

**Syntax**

bSaveOriCanvas: *boolean* = false;

**Code snippet**

```js
reader.bSaveOriCanvas = true;
let results = await reader.decode(source);
document.body.append(reader.oriCanvas);
```

<br />

### oriCanvas

An [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/Canvas) that holds the original image. The original image refers to the actual image the library tried to read barcodes from.

**Syntax**
`readonly` oriCanvas: *[HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement) &#124; [OffscreenCanvas](https://developer.mozilla.org/en-US/docs/Web/API/OffscreenCanvas)*

**Code snippet**

```js
reader.bSaveOriCanvas = true;
let results = await reader.decode(source);
document.body.append(reader.oriCanvas);
```
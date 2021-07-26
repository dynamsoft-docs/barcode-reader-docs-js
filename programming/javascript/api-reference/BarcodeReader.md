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

&nbsp;

## API Index

<div class="doc-card-prefix doc-card-list-prefix"></div>

> Create and Destroy Instances
> <hr>
> * [createInstance](#createinstance)
> * [destroy](#destroy)
> * [bDestroyed](#bdestroyed)
> 
> Decode Barcodes
> <hr>
> * [decode](#decode)
> * [decodeBase64String](#decodebase64string)
> * [decodeUrl](#decodeurl)
> * [decodeBuffer](#decodebuffer)
> 
> Change Settings
> <hr>
> * [getRuntimeSettings](#getruntimesettings)
> * [updateRuntimeSettings](#updateruntimesettings)
> * [resetRuntimeSettings](#resetruntimesettings)
> * [getModeArgument](#getmodeargument)
> * [setModeArgument](#setmodeargument)
> 
> Auxiliary
> <hr>
> * [bSaveOriCanvas](#bsaveoricanvas)
> * [oriCanvas](#oricanvas)

&nbsp;

## Create and Destroy Instances

&nbsp;

### createInstance

Creates a `BarcodeReader` instance.

**Syntax**

`static` createInstance&#40;&#41;: *Promise&lt;[BarcodeReader](#barcodereader)&gt;*

**Parameters**

None.

**Code snippet**

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
```

&nbsp;

### destroy

Destroies the `BarcodeReader` instance. If your page needs to create new instances from time to time, don't forget to destroy unused old instances.

**Syntax**

destroy&#40;&#41;: *Promise&lt;void&gt;*

**Parameters**

None.

**Code snippet**

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
// ... decode ...
reader.destroy();
```

&nbsp;

### bDestroyed

Indicates whether the instance has been destroyed.

**Syntax**

bDestroyed: *boolean*

&nbsp;

## Decode Barcodes

&nbsp;

### decode

Decodes barcodes from an image. The supported image formats include `png`, `jpeg`, `bmp`, `gif` and a few others (some browsers support `webp`, `tif`). Also note that the image can be specified in a lot of ways including binary data, base64 string (with MIME), URL, etc.

**Syntax**

decode &#40;source: *[Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob) &#124; [Buffer](https://nodejs.org/api/buffer.html#buffer_class_buffer) &#124; [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) &#124; [Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array) &#124; [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray)&#124; [HTMLImageElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement) &#124; [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement) &#124; [HTMLVideoElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLVideoElement)&#124; string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*
  
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

&nbsp;

### decodeBase64String

Decodes barcodes from a base64-encoded image (with or without MIME).

**Syntax**
decodeBase64String&#40;base64: *string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

**Code snippet**

```js
let results = await reader.decodeBase64String(strBase64); //e.g. `data:image/jpg;base64,Xfjshekk....` or `Xfjshekk...`.
for(let result of results){
  console.log(result.barcodeText);
}
```

&nbsp;

### decodeUrl

Decodes barcodes from an image specified by its URL. Note that the image should either be from the same domain or has the 'Access-Control-Allow-Origin' header set to allow access from your current domain.

**Syntax**

decodeUrl&#40;url: *string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

**Code snippet**

```js
let results = await reader.decodeUrl("https://www.yourdomain.com/imageWithBarcodes.png");
for(let result of results){
    console.log(result.barcodeText);
}
```

&nbsp;

### decodeBuffer

Decodes barcodes from raw image data.

**Syntax**

decodeBuffer&#40;buffer: *[Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array) &#124; [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray) &#124; [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) &#124; [Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob) &#124; [Buffer](https://nodejs.org/api/buffer.html#buffer_class_buffer),width: *number*, height: *number*, stride: *number*,format: *[EnumImagePixelFormat](./enum/EnumImagePixelFormat.md)*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

&nbsp;

## Change Settings
 
&nbsp;

### getRuntimeSettings

Returns the current runtime settings.

**Syntax**

getRuntimeSettings&#40;&#41;: *Promise&lt;[RuntimeSettings](./interface/RuntimeSettings.md)&gt;*

**Code snippet**

```js
let settings = await reader.getRuntimeSettings();
settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE; // Decodes only QR code.
await reader.updateRuntimeSettings(settings);
```

**See also**

[RuntimeSettings](./interface/RuntimeSettings.md)

&nbsp;

### updateRuntimeSettings

Updates runtime settings with a given struct or a preset template represented by one of the following strings
- `speed`: fast but may miss a few codes;
- `coverage`: slow but try to find all codes, this is the default setting for a `BarcodeReader` instance;
- `balance`: between `speed` and `coverage`;
- `single`: optimized for scanning one single barcode from a video input, this is supported only by the sub-class [`BarcodeScanner`](./BarcodeScanner.md) and is also the default setting for a `BarcodeScanner` instance.

**Syntax**

updateRuntimeSettings&#40;settings: *[RuntimeSettings](./interface/RuntimeSettings.md) &#124; string*&#41;: *Promise&lt;void&gt;*

**Code snippet**

```js
await reader.updateRuntimeSettings('balance');
let settings = await reader.getRuntimeSettings();
settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED;
await reader.updateRuntimeSettings(settings);
```

&nbsp;

### resetRuntimeSettings

Resets all parameters to default values.

For a `BarcodeReader` instance, it is equivalent to setting the `coverage` template.

For a [`BarcodeScanner`](./BarcodeScanner.md) instance, it is equivalent to setting the `single` template.

**Syntax**

resetRuntimeSettings&#40;&#41;: *Promise&lt;void&gt;*

**Code snippet**

```js
await reader.resetRuntimeSettings();
```

&nbsp;

### getModeArgument

Returns the argument value for the specified mode parameter.

**Syntax**
getModeArgument&#40;modeName: *string*, index: *number*, argumentName: *string*&#41;: *Promise&lt;string&gt;*

**Code snippet**

```js
let argumentValue = await reader.getModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy");
```

**See also**

[C++ getModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#getmodeargument)

&nbsp;

### setModeArgument

Sets the argument value for the specified mode parameter.

**Syntax**

setModeArgument&#40;modeName: *string*, index: *number*, argumentName: *string*, argumentValue: *string*&#41;: *Promise&lt;string&gt;*

**Code snippet**

```js
await reader.setModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy", "1");
```

**See also**

[C++ setModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#setmodeargument)

&nbsp;

## Auxiliary

&nbsp;

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

&nbsp;

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
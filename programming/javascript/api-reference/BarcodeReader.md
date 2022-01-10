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



## API Index

### Create and Destroy Instances

| API Name | Description |
|---|---|
| [createInstance](#createinstance) | Creates a `BarcodeReader` instance. |
| [destroyContext](#destroycontext) | Destroies the BarcodeReader instance. |
| [isContextDestroyed](#iscontextdestroyed) | Indicates whether the instance has been destroyed. |

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
| [ifSaveOriginalImageInACanvas](#ifsaveoriginalimageinacanvas) | Whether to save the original image into a &lt;canvas&gt; element. |
| [getOriginalImageInACanvas](#getoriginalimageinacanvas) | Returns an `HTMLCanvasElement` that holds the original image. |

## createInstance

Creates a `BarcodeReader` instance.

```typescript
static createInstance(): Promise<BarcodeReader>
```

**Parameters**

None.

**Return value**

A promise resolving to the created `BarcodeReader` object.

**Code snippet**

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
```



## destroyContext

Destroies the `BarcodeReader` instance. If your page needs to create new instances from time to time, don't forget to destroy unused old instances.

```typescript
destroyContext(): Promise<void>
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code snippet**

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
// ... decode ...
reader.destroyContext();
```



## isContextDestroyed

Returns whether the instance has been destroyed.

```typescript
isContextDestroyed(): boolean
```

## decode

Decodes barcodes from an image. 

```typescript
decode(source: Blob | Buffer | ArrayBuffer | Uint8Array | Uint8ClampedArray | HTMLImageElement | HTMLCanvasElement | HTMLVideoElement | string): Promise<TextResult[]>
```

**Parameters**

`source`: specifies the image to decode. The supported image formats include `png`, `jpeg`, `bmp`, `gif` and a few others (some browsers support `webp`, `tif`). Also note that the image can be specified in a lot of ways including binary data, base64 string (with MIME), URL, etc.

> To speed up the reading, the image will be scaled down when it exceeds a size limit either horizontally or vertically. The limit is 2048 pixels on mobile devices and 4096 on other devices.

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
  // If there is no frame in the video, throw an exception.
}
```

**See also**

* [Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob)
* [Buffer](https://nodejs.org/api/buffer.html#buffer_class_buffer)
* [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer)
* [Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array)
* [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray)
* [HTMLImageElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement)
* [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement)
* [HTMLVideoElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLVideoElement)
* [TextResult](./interface/TextResult.md)



## decodeBase64String

Decodes barcodes from a base64-encoded image (with or without MIME).

```typescript
decodeBase64String(base64Str: string): Promise<TextResult[]>
```

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

**See also**

* [TextResult](./interface/TextResult.md)



## decodeUrl

Decodes barcodes from an image specified by its URL. Note that the image should either be from the same domain or has the 'Access-Control-Allow-Origin' header set to allow access from your current domain.

```typescript
decodeUrl(url: string): Promise<TextResult[]>
```

**Parameters**

`url`: specifies the image by its URL.

**Return value**

A promise resolving to a `TextResult` object that contains all the barcode results found in this image.

**Code snippet**

```js
let results = await reader.decodeUrl("https://www.yourdomain.com/imageWithBarcodes.png");
for(let result of results){
    console.log(result.barcodeText);
}
```

**See also**

* [TextResult](./interface/TextResult.md)



## decodeBuffer

Decodes barcodes from raw image data.

```typescript
decodeBuffer(buffer: Blob | Buffer | ArrayBuffer | Uint8Array | Uint8ClampedArray, width: number, height: number, stride: number, format: EnumImagePixelFormat): Promise<TextResult[]>
```

**Parameters**

`buffer`: specifies the image represented by a `Uint8Array`, `Uint8ClampedArray`, `ArrayBuffer`, `Blob` or `Buffer` object.

**Return value**

A promise resolving to a `TextResult` object that contains all the barcode results found in this image.

**See also**

* [Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob)
* [Buffer](https://nodejs.org/api/buffer.html#buffer_class_buffer)
* [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer)
* [Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array)
* [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray)
* [EnumImagePixelFormat](./enum/EnumImagePixelFormat.md)
* [TextResult](./interface/TextResult.md)



## getRuntimeSettings

Returns the current runtime settings.

```typescript
getRuntimeSettings(): Promise<RuntimeSettings>
```

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

* [RuntimeSettings](./interface/RuntimeSettings.md)



## updateRuntimeSettings

Updates runtime settings with a given struct or a preset template represented by one of the following strings
- `speed`: fast but may miss a few codes;
- `coverage`: slow but try to find all codes, this is the default setting for a `BarcodeReader` instance;
- `balance`: between `speed` and `coverage`;
- `single`: optimized for scanning one single barcode from a video input, this is supported only by the sub-class [`BarcodeScanner`](./BarcodeScanner.md) and is also the default setting for a `BarcodeScanner` instance.


> NOTE
> 
> If the settings `barcodeFormatIds`, `barcodeFormatIds_2` and `region` have been changed by the customer, changing the template will preserve the previous settings.

```typescript
updateRuntimeSettings(settings: RuntimeSettings | string): Promise<void>
```

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

**See also**

* [RuntimeSettings](./interface/RuntimeSettings.md)



## resetRuntimeSettings

Resets all parameters to default values.

For a `BarcodeReader` instance, it is equivalent to setting the `coverage` template.

For a [`BarcodeScanner`](./BarcodeScanner.md) instance, it is equivalent to setting the `single` template.

```typescript
resetRuntimeSettings(): Promise<void>
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code snippet**

```js
await reader.resetRuntimeSettings();
```



## getModeArgument

Returns the argument value for the specified mode parameter.

```typescript
getModeArgument(modeName: string, index: number, argumentName: string): Promise<string>
```

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

* [C++ getModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#getmodeargument)



## setModeArgument

Sets the argument value for the specified mode parameter.

```typescript
setModeArgument(modeName: string, index: number, argumentName: string, argumentValue: string): Promise<void>
```

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

* [C++ setModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#setmodeargument)



## ifSaveOriginalImageInACanvas

Whether to save the original image into a &lt;canvas&gt; element. The original image refers to the actual image the library tried to read barcodes from.

Note that the result is an `HTMLCanvasElement` element and you can insert it into the DOM to show the image.

```typescript
ifSaveOriginalImageInACanvas: boolean;
```

**Default value**

`false`

**Code snippet**

```js
reader.ifSaveOriginalImageInACanvas = true;
let results = await reader.decode(source);
document.body.append(reader.getOriginalImageInACanvas());
```

## getOriginalImageInACanvas

An [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/Canvas) that holds the original image. The original image refers to the actual image the library tried to read barcodes from.

```typescript
getOriginalImageInACanvas(): HTMLCanvasElement | OffscreenCanvas
```

**Code snippet**

```js
reader.ifSaveOriginalImageInACanvas = true;
let results = await reader.decode(source);
document.body.append(reader.getOriginalImageInACanvas());
```

**See also**

* [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement)
* [OffscreenCanvas](https://developer.mozilla.org/en-US/docs/Web/API/OffscreenCanvas)
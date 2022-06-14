---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - v9.0.2 BarcodeReader
description: This page shows the BarcodeReader Class of Dynamsoft Barcode Reader JavaScript SDK.
keywords: BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: BarcodeReader
permalink: /programming/javascript/api-reference/BarcodeReader.html
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
| [createInstance()](#createinstance) | Creates a `BarcodeReader` instance. |
| [destroyContext()](#destroycontext) | Destroies the BarcodeReader instance. |
| [isContextDestroyed()](#iscontextdestroyed) | Indicates whether the instance has been destroyed. |

### Decode Barcodes

| API Name | Description |
|---|---|
| [decode()](#decode) | Decodes barcodes from an image. |
| [decodeBase64String()](#decodebase64string) | Decodes barcodes from a base64-encoded image (with or without MIME). |
| [decodeUrl()](#decodeurl) | Decodes barcodes from an image specified by its URL. |
| [decodeBuffer()](#decodebuffer) | Decodes barcodes from raw image data. |

### Decode Barcodes on multiple images from an Image Source

| API Name | Description |
|---|---|
| [setImageSource](#setimagesource) | Sets an image source for continous scanning. |
| [onUniqueRead](#onuniqueread) | This event is triggered when a new, unduplicated barcode is found. |
| [onImageRead](#onimageread) | This event is triggered after the library finishes scanning an image. |
| [startScanning()](#startscanning) | Starts continuous scanning of incoming images. |
| [stopScanning()](#stopscanning) | Stops continuous scanning. |
| [pauseScanning()](#pausescanning) | Pause continuous scanning but keep the video stream. |
| [resumeScanning()](#resumescanning) | Resumes continuous scanning. |
| [getScanSettings()](#getscansettings) | Returns the current scan settings. |
| [updateScanSettings()](#updatescansettings) | Changes scan settings with the object passed in. |

### Change Settings

| API Name | Description |
|---|---|
| [getRuntimeSettings()](#getruntimesettings) | Returns the current runtime settings. |
| [updateRuntimeSettings()](#updateruntimesettings) | Updates runtime settings with a given struct or a preset template. |
| [resetRuntimeSettings()](#resetruntimesettings) | Resets all parameters to default values. |
| [outputRuntimeSettingsToString()](#outputruntimesettingstostring) | Return the current RuntimeSettings in the form of a string. |
| [getModeArgument()](#getmodeargument) | Returns the argument value for the specified mode parameter. |
| [setModeArgument()](#setmodeargument) | Sets the argument value for the specified mode parameter. |

### Auxiliary

| API Name | Description |
|---|---|
| [ifSaveOriginalImageInACanvas](#ifsaveoriginalimageinacanvas) | Whether to save the original image into a &lt;canvas&gt; element. |
| [getOriginalImageInACanvas()](#getoriginalimageinacanvas) | Returns an `HTMLCanvasElement` that holds the original image. |

## createInstance

Creates a `BarcodeReader` instance.

```typescript
static createInstance(): Promise<BarcodeReader>
```

### Return Value

A promise resolving to the created `BarcodeReader` object.

### Code Snippet

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
```

## destroyContext

Destroies the `BarcodeReader` instance. If your page needs to create new instances from time to time, don't forget to destroy unused old instances.

```typescript
destroyContext(): void
```

### Code Snippet

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

### Parameters

`source`: specifies the image to decode. The supported image formats include `png`, `jpeg`, `bmp`, `gif` and a few others (some browsers support `webp`, `tif`). Also note that the image can be specified in a lot of ways including binary data, base64 string (with MIME), URL, etc.

> To speed up the reading, the image will be scaled down when it exceeds a size limit either horizontally or vertically. The limit is 2048 pixels on mobile devices and 4096 on other devices.
>
> If the content in the binary data is raw img data, such as `RGBA`, please refer to [decodeBuffer()](#decodebuffer).

### Return Value

A promise resolving to a `TextResult\[\]` object that contains all the barcode results found in this image.

### Code Snippet

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

### See Also

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

### Parameters

`base64Str`: specifies the image represented by a string.

### Return Value

A promise resolving to a `TextResult\[\]` object that contains all the barcode results found in this image.

### Code Snippet

```js
let results = await reader.decodeBase64String(strBase64); //e.g. `data:image/jpg;base64,Xfjshekk....` or `Xfjshekk...`.
for(let result of results){
  console.log(result.barcodeText);
}
```

### See Also

* [TextResult](./interface/TextResult.md)

## decodeUrl

Decodes barcodes from an image specified by its URL. Note that the image should either be from the same domain or has the 'Access-Control-Allow-Origin' header set to allow access from your current domain.

```typescript
decodeUrl(url: string): Promise<TextResult[]>
```

### Parameters

`url`: specifies the image by its URL.

### Return Value

A promise resolving to a `TextResult\[\]` object that contains all the barcode results found in this image.

### Code Snippet

```js
let results = await reader.decodeUrl("https://www.yourdomain.com/imageWithBarcodes.png");
for(let result of results){
    console.log(result.barcodeText);
}
```

### See Also

* [TextResult](./interface/TextResult.md)

## decodeBuffer

Decodes barcodes from raw image data. It is an advanced API, if you don't know what you are doing, use [decode](#decode) instead. 

```typescript
decodeBuffer(buffer: Blob | Buffer | ArrayBuffer | Uint8Array | Uint8ClampedArray, width: number, height: number, stride: number, format: EnumImagePixelFormat): Promise<TextResult[]>
```

### Parameters

`buffer`: specifies the raw image represented by a `Uint8Array`, `Uint8ClampedArray`, `ArrayBuffer`, `Blob` or `Buffer` object.

`width`: image width.

`height`: image height.

`stride`: `image-width * pixel-byte-length`.

`format`: pixel format.

### Return Value

A promise resolving to a `TextResult\[\]` object that contains all the barcode results found in this image.

### Code Snippet

```js
let results = await reader.decodeBuffer(u8RawImage, 1280, 720, 1280 * 4, Dynamsoft.DBR.EnumImagePixelFormat.IPF_ABGR_8888);
for(let result of results){
    console.log(result.barcodeText);
}
```

### See Also

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

### Return Value

A promise resolving to a `RuntimeSettings` object that contains the settings for barcode reading.

### Code Snippet

```js
let settings = await reader.getRuntimeSettings();
settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE; // Decodes only QR code.
await reader.updateRuntimeSettings(settings);
```

### See Also

* [RuntimeSettings](./interface/RuntimeSettings.md)

## updateRuntimeSettings

Updates runtime settings with a given struct or a preset template represented by one of the following strings

* `speed`: fast but may miss a few codes;
* `coverage`: slow but try to find all codes, this is the default setting for a `BarcodeReader` instance;
* `balance`: between `speed` and `coverage`;
* `single`: optimized for scanning one single barcode from a video input, this is supported only by the sub-class [`BarcodeScanner`](./BarcodeScanner.md) and is also the default setting for a `BarcodeScanner` instance.

> NOTE
>
> If the settings `barcodeFormatIds`, `barcodeFormatIds_2` and `region` have been changed by the customer, changing the template will preserve the previous settings.

```typescript
updateRuntimeSettings(settings: RuntimeSettings | string): Promise<void>
```

### Parameters

`settings`: a `RuntimeSettings` object that contains the new settings for barcode reading.

### Return Value

A promise that resolves when the operation succeeds.

### Code Snippet

```js
await reader.updateRuntimeSettings('balance');
let settings = await reader.getRuntimeSettings();
settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED;
await reader.updateRuntimeSettings(settings);
```

### See Also

* [RuntimeSettings](./interface/RuntimeSettings.md)

## resetRuntimeSettings

Resets all parameters to default values.

For a `BarcodeReader` instance, it is equivalent to setting the `coverage` template.

For a [`BarcodeScanner`](./BarcodeScanner.md) instance, it is equivalent to setting the `single` template.

```typescript
resetRuntimeSettings(): Promise<void>
```

### Parameters

None.

### Return Value

A promise that resolves when the operation succeeds.

### Code Snippet

```js
await reader.resetRuntimeSettings();
```

## outputRuntimeSettingsToString

Return the current RuntimeSettings in the form of a string.

```typescript
outputRuntimeSettingsToString(): Promise<string>
```

### Return Value

A promise resolving to a string which represents the current RuntimeSettings.

## getModeArgument

Returns the argument value for the specified mode parameter.

```typescript
getModeArgument(modeName: string, index: number, argumentName: string): Promise<string>
```

### Parameters

`modeName`: specifies the mode which contains one or multiple elements.
`index`: specifies an element of the mode by its index.
`argumentName`: specifies the argument.

### Return Value

A promise resolving to a string which represents the value of the argument.

### Code Snippet

```js
let argumentValue = await reader.getModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy");
```

### See Also

* [C++ getModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#getmodeargument)

## setModeArgument

Sets the argument value for the specified mode parameter.

```typescript
setModeArgument(modeName: string, index: number, argumentName: string, argumentValue: string): Promise<void>
```

### Parameters

`modeName`: specifies the mode which contains one or multiple elements.
`index`: specifies an element of the mode by its index.
`argumentName`: specifies the argument.
`argumentValue`: specifies the value.

### Return Value

A promise that resolves when the operation succeeds.

### Code Snippet

```js
await reader.setModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy", "1");
```

### See Also

* [C++ setModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#setmodeargument)

## ifSaveOriginalImageInACanvas

Whether to save the original image into a &lt;canvas&gt; element. The original image refers to the actual image the library tried to read barcodes from.

Note that the result is an `HTMLCanvasElement` element and you can insert it into the DOM to show the image.

```typescript
ifSaveOriginalImageInACanvas: boolean;
```

**Default value**

`false`

### Code Snippet

```js
reader.ifSaveOriginalImageInACanvas = true;
let results = await reader.decode(source);
document.body.append(reader.getOriginalImageInACanvas());
```

## getOriginalImageInACanvas

An [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/Canvas) that holds the original image. The original image refers to the actual image the library tried to read barcodes from.

```typescript
getOriginalImageInACanvas(): HTMLCanvasElement
```

### Code Snippet

```js
reader.ifSaveOriginalImageInACanvas = true;
let results = await reader.decode(source);
document.body.append(reader.getOriginalImageInACanvas());
```

### See Also

* [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement)

## setImageSource

Sets an image source for continous scanning.

```typescript
setImageSource(imageSource: ImageSource): boolean;
```

### Arguments

`imageSource` : Specifies the image source.

### Code Snippet

```javascript
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
await enhancer.setUIElement(Dynamsoft.DBR.BarcodeReader.defaultUIElementURL);
reader.setImageSource(enhancer);
reader.onUniqueRead = (txt, result) => {
    console.log(txt);
}
reader.startScanning(true);
```

## onUniqueRead

This event is triggered when a new, unduplicated label is found.

```typescript
onUniqueRead: (txt: string, result: TextResult) => void
```

### Arguments

`txt` : a string that holds the label text (one single line).

`result` : a `TextResult` object that contains more detailed info about the returned text.

### Code Snippet

```javascript
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
await enhancer.setUIElement(Dynamsoft.DBR.BarcodeReader.defaultUIElementURL);
reader.setImageSource(enhancer);
reader.onUniqueRead = (txt, result) => {
    console.log(txt);
}
reader.startScanning(true);
```

### See Also

* [TextResult](./interface/TextResult.md)

## onImageRead

This event is triggered after the library finishes scanning a image.

```typescript
onImageRead: (results: TextResult[]) => void
```

### Arguments

`results` : `TextResult` objects that contain all the label results in this image.

### Code Snippet

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
await enhancer.setUIElement(Dynamsoft.DBR.BarcodeReader.defaultUIElementURL);
reader.setImageSource(enhancer);
reader.onImageRead = results => {
    for (let result of results) {
      console.log(result.barcodeText);
    }
};
reader.startScanning(true);
```

### See Also

* [TextResult](./interface/TextResult.md)

## startScanning

Open the camera and starts continuous scanning of incoming images.

```typescript
startScanning(appendOrShowUI?: boolean): Promise<PlayCallbackInfo>;
```

### Parameters

`appendOrShowUI` : this parameter specifies how to handle the UI that comes with the bound CameraEnhancer instance. When set to true, if the UI doesn't exist in the DOM tree, the CameraEnhancer instance will append it in the DOM and show it; if the UI already exists in the DOM tree but is hidden, it'll be displayed. When not set or set to false, it means not to change the original state of that UI: if it doesn't exist in the DOM tree, nothing shows up on the page; if it exists in the DOM tree, it may or may not show up depending on its original state.

### Return Value

A promise resolving to a `PlayCallbackInfo` object which contains the resolution of the video.

### Code Snippet

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
await enhancer.setUIElement(Dynamsoft.DBR.BarcodeReader.defaultUIElementURL);
reader.setImageSource(enhancer);
reader.onUniqueRead = (txt, result) => {
    console.log(txt);
}
reader.startScanning(true);
```

### See Also

* [TextResult](./interface/TextResult.md)

## pauseScanning

Pause continuous scanning but keep the video stream.

```typescript
pauseScanning(): void;
```

## resumeScanning

Resumes continuous scanning.

```typescript
resumeScanning(): void;
```

## stopScanning

Stops continuous scanning and closes the video stream.

```typescript
stopScanning(hideUI?: boolean): void;
```

### Parameters

`hideUI` : this parameter specifies how to handle the UI that comes with the bound CameraEnhancer instance. When set to true, if the UI doesn't exist in the DOM tree or it exists but is hidden, nothing is done; if the UI already exists in the DOM tree and is shown, it'll be hidden. When not set or set to false, it means not to change the original state of that UI: if it doesn't exist in the DOM tree, nothing happens; if it exists in the DOM tree, it may or may not be hidden depending on its original state.

### Code Snippet

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
await enhancer.setUIElement(Dynamsoft.DBR.BarcodeReader.defaultUIElementURL);
reader.setImageSource(enhancer);
reader.onUniqueRead = (txt, result) => {
    console.log(txt);
    reader.stopScanning(true);
}
await reader.startScanning(true);
```

### See Also

* [TextResult](./interface/TextResult.md)

## getScanSettings

Returns the current scan settings.

```typescript
getScanSettings(): Promise<ScanSettings>
```

### Return Value

A promise resolving to a `ScanSettings` .

### Code Snippet

```js
let scanSettings = await reader.getScanSettings();
scanSettings.intervalTime = 50;
scanSettings.duplicateForgetTime = 1000;
await reader.updateScanSettings(scanSettings);
```

### See Also

* [ScanSettings](./interface/ScanSettings.md)

## updateScanSettings

Changes scan settings with the object passed in.

```typescript
updateScanSettings(settings: ScanSettings): Promise<void>
```

**Parameters**

`settings` : specifies the new scan settings.

### Return Value

A promise that resolves when the operation succeeds.

### Code Snippet

```js
let scanSettings = await reader.getScanSettings();
scanSettings.intervalTime = 50;
scanSettings.duplicateForgetTime = 1000;
await reader.updateScanSettings(scanSettings);
```

### See Also

* [ScanSettings](./interface/ScanSettings.md)

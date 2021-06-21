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


# BarcodeReader

A low-level barcode reader that processes still images and return barcode results. The following code snippet shows its basic usage.

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
let results = await reader.decode(imageSource);
for(let result of results){
  console.log(result.barcodeText);
}
```

## Index

[**Create and Destroy Instances**](#create-and-destroy-instances)

* [createInstance](#createinstance)
* [destroy](#destroy)
* [bDestroyed](#bdestroyed)

<br>

[**Decode Barcodes**](#decode-barcodes)

* [decode](#decode)
* [decodeBase64String](#decodebase64string)
* [decodeUrl](#decodeurl)
* [decodeBuffer](#decodebuffer)

<br>

[**Change Settings**](#decoding-settings)

* [getRuntimeSettings](#getruntimesettings)
* [updateRuntimeSettings](#updateruntimesettings)
* [resetRuntimeSettings](#resetruntimesettings)
* [getModeArgument](#getmodeargument)
* [setModeArgument](#setmodeargument)

<br>

[**Auxiliary**](#auxiliary)


* [bSaveOriCanvas](#bsaveoricanvas)
* [oriCanvas](#oricanvas)

<br>

## Create and Destroy Instances

### createInstance

* `static` createInstance&#40;&#41;: *Promise&lt;[BarcodeReader](#barcodereader)&gt;*

  Creates a `BarcodeReader` instance.

   ```js
   let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
   ```

<br>

### destroy

* destroy&#40;&#41;: *Promise&lt;void&gt;*

  Destroies the `BarcodeReader` instance. If your page needs to create new instances from time to time, don't forget to destroy unused old instances.

  ```js
  let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
  // ... decode ...
  reader.destroy();

<br>

### bDestroyed

* bDestroyed: *boolean*

  Indicates whether the instance has been destroyed.

<br>

## Decode Barcodes

### decode

* decode &#40;source: *[Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob) &#124; [Buffer](https://nodejs.org/api/buffer.html#buffer_class_buffer) &#124; [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) &#124; [Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array) &#124; [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray)*<br>
  
  *&#124; [HTMLImageElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement) &#124; [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement) &#124; [HTMLVideoElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLVideoElement)*<br>
  
  *&#124; string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

  Decodes barcodes from an image. 
  
  The supported image formats include `png`, `jpeg`, `bmp`, `gif` and a few others (some browsers support `webp`, `tif`). Also note that the image can be specified in a lot of ways including binary data, base64 string (with MIME), URL, etc.

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

  For continuous barcode decoding from a video, use a [BarcodeScanner](./BarcodeScanner.md) instance instead.

<br>

### decodeBase64String

* decodeBase64String&#40;base64: *string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

  Decodes barcodes from a base64-encoded image (with or without MIME).
  
  ```js
  let results = await reader.decodeBase64String(strBase64); //e.g. `data:image/jpg;base64,Xfjshekk....` or `Xfjshekk...`.
  for(let result of results){
    console.log(result.barcodeText);
  }
  ```

<br>

### decodeUrl

* decodeUrl&#40;url: *string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

  Decodes barcodes from an image specified by its URL. Note that the image should either be from the same domain or has the 'Access-Control-Allow-Origin' header set to allow access from your current domain.

  ```js
  let results = await reader.decodeUrl("https://www.yourdomain.com/imageWithBarcodes.png");
  for(let result of results){
      console.log(result.barcodeText);
  }
  ```

<br>

### decodeBuffer

* decodeBuffer&#40;<br>
  &nbsp;&nbsp;&nbsp;&nbsp;buffer: *[Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array) &#124; [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray) &#124; [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) &#124; [Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob) &#124; [Buffer](https://nodejs.org/api/buffer.html#buffer_class_buffer)*,<br>
  &nbsp;&nbsp;&nbsp;&nbsp;width: *number*, height: *number*, stride: *number*,<br>
  &nbsp;&nbsp;&nbsp;&nbsp;format: *[EnumImagePixelFormat](./enum/EnumImagePixelFormat.md)*<br>
  &#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

  Decodes barcodes from raw image data.

<br>

## Change Settings

### getRuntimeSettings

* getRuntimeSettings&#40;&#41;: *Promise&lt;[RuntimeSettings](./interface/RuntimeSettings.md)&gt;*

  Returns the current runtime settings.
  
  ```js
  let settings = await reader.getRuntimeSettings();
  settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE; // Decodes only QR code.
  await reader.updateRuntimeSettings(settings);
  ```

<br>

### updateRuntimeSettings

* updateRuntimeSettings&#40;settings: *[RuntimeSettings](./interface/RuntimeSettings.md) &#124; string*&#41;: *Promise&lt;void&gt;*

  Updates runtime settings with a given struct or a preset template represented by one of the following strings
  
  - `speed`: fast but may miss a few codes;
  - `coverage`: slow but try to find all codes, this is the default setting;
  - `balance`: between `speed` and `coverage`.
  
  ```js
  await reader.updateRuntimeSettings('balance');
  let settings = await reader.getRuntimeSettings();
  settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED;
  await reader.updateRuntimeSettings(settings);
  ```

<br>

### resetRuntimeSettings

* resetRuntimeSettings&#40;&#41;: *Promise&lt;void&gt;*

  Resets all parameters to default values (which is essentially the preset `coverage` template).
  
  ```js
  await reader.resetRuntimeSettings();
  ```

<br>

### getModeArgument

* getModeArgument&#40;modeName: *string*, index: *number*, argumentName: *string*&#41;: *Promise&lt;string&gt;*

  Returns the argument value for the specified mode parameter.
 
  ```js
  let argumentValue = await reader.getModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy");
  ```

  *@see* [C++ getModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#getmodeargument)

<br>

### setModeArgument

* setModeArgument&#40;modeName: *string*, index: *number*, argumentName: *string*, argumentValue: *string*&#41;: *Promise&lt;string&gt;*

  Sets the argument value for the specified mode parameter.

  ```js
  await reader.setModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy", "1");
  ```

  *@see* [C++ setModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#setmodeargument)

<br>

## Auxiliary

### bSaveOriCanvas

* bSaveOriCanvas: *boolean* = false;

  Whether to save the original image into a &lt;canvas&gt; element. The original image refers to the actual image the library tried to read barcodes from.

  Note that the result is an *HTMLCanvasElement* element and you can insert it into the DOM to show the image.

  ```js
  reader.bSaveOriCanvas = true;
  let results = await reader.decode(source);
  document.body.append(reader.oriCanvas);
  ```

<br>

### oriCanvas

* `readonly` oriCanvas: *[HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement) &#124; [OffscreenCanvas](https://developer.mozilla.org/en-US/docs/Web/API/OffscreenCanvas)*

  An [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/Canvas) that holds the original image. The original image refers to the actual image the library tried to read barcodes from.

  ```js
  reader.bSaveOriCanvas = true;
  let results = await reader.decode(source);
  document.body.append(reader.oriCanvas);
  ```

<br>


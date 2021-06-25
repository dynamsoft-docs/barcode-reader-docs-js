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

<div class="doc-card-prefix"></div>

## Index

> [**Create and Destroy Instances**](#create-and-destroy-instances)
> 
> * [createInstance](#createinstance)
> * [destroy](#destroy)
> * [bDestroyed](#bdestroyed)
> <hr>
> [**Decode Barcodes**](#decode-barcodes)
> 
> * [decode](#decode)
> * [decodeBase64String](#decodebase64string)
> * [decodeUrl](#decodeurl)
> * [decodeBuffer](#decodebuffer)
> <hr>
> [**Change Settings**](#decoding-settings)
> 
> * [getRuntimeSettings](#getruntimesettings)
> * [updateRuntimeSettings](#updateruntimesettings)
> * [resetRuntimeSettings](#resetruntimesettings)
> * [getModeArgument](#getmodeargument)
> * [setModeArgument](#setmodeargument)
> <hr>
> [**Auxiliary**](#auxiliary)
> 
> * [bSaveOriCanvas](#bsaveoricanvas)
> * [oriCanvas](#oricanvas)

## Create and Destroy Instances

<div class="doc-card-prefix"></div>

> ### createInstance
> <hr>
> `static` createInstance&#40;&#41;: *Promise&lt;[BarcodeReader](#barcodereader)&gt;*
> <hr>
> Creates a `BarcodeReader` instance.
> #### Example
> ```js
> let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
> ```

<div class="doc-card-prefix"></div>

> ### destroy
> <hr>
> destroy&#40;&#41;: *Promise&lt;void&gt;*
> <hr>
> Destroies the `BarcodeReader` instance. If your page needs to create new instances from time to time, don't forget to destroy unused old instances.
> #### Example
> ```js
> let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
> // ... decode ...
> reader.destroy();
> ```

<div class="doc-card-prefix"></div>

> ### bDestroyed
> <hr>
> bDestroyed: *boolean*
> <hr>
> Indicates whether the instance has been destroyed.

## Decode Barcodes

<div class="doc-card-prefix"></div>

> ### decode
> <hr>
> decode &#40;source: *[Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob) &#124; [Buffer](https://nodejs.org/api/buffer.html#buffer_class_buffer) &#124; [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) &#124; [Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array) &#124; [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray)&#124; [HTMLImageElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement) &#124; [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement) &#124; [HTMLVideoElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLVideoElement)&#124; string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*
> <hr>
> Decodes barcodes from an image. 
>   
> The supported image formats include `png`, `jpeg`, `bmp`, `gif` and a few others (some browsers support `webp`, `tif`). Also note that the image can be specified in a lot of ways including binary data, base64 string (with MIME), URL, etc.
> #### Example
> ```js
> let results1 = await reader.decode(blob);
> let results2 = await reader.decode(htmlImageElement);
> let results3 = await reader.decode(url);
> let results4 = await reader.decode(strBase64WithMime); // like `data:image/png;base64,iV************`
> ```

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

<div class="doc-card-prefix"></div>


### decodeBase64String

* decodeBase64String&#40;base64: *string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

  Decodes barcodes from a base64-encoded image (with or without MIME).
  
  ```js
  let results = await reader.decodeBase64String(strBase64); //e.g. `data:image/jpg;base64,Xfjshekk....` or `Xfjshekk...`.
  for(let result of results){
    console.log(result.barcodeText);
  }
  ```

<div class="doc-card-prefix"></div>


### decodeUrl

* decodeUrl&#40;url: *string*&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

  Decodes barcodes from an image specified by its URL. Note that the image should either be from the same domain or has the 'Access-Control-Allow-Origin' header set to allow access from your current domain.

  ```js
  let results = await reader.decodeUrl("https://www.yourdomain.com/imageWithBarcodes.png");
  for(let result of results){
      console.log(result.barcodeText);
  }
  ```

<div class="doc-card-prefix"></div>


### decodeBuffer

* decodeBuffer&#40;<div class="doc-card-prefix"></div>

  &nbsp;&nbsp;&nbsp;&nbsp;buffer: *[Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array) &#124; [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray) &#124; [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) &#124; [Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob) &#124; [Buffer](https://nodejs.org/api/buffer.html#buffer_class_buffer)*,<div class="doc-card-prefix"></div>

  &nbsp;&nbsp;&nbsp;&nbsp;width: *number*, height: *number*, stride: *number*,<div class="doc-card-prefix"></div>

  &nbsp;&nbsp;&nbsp;&nbsp;format: *[EnumImagePixelFormat](./enum/EnumImagePixelFormat.md)*<div class="doc-card-prefix"></div>

  &#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

  Decodes barcodes from raw image data.

<div class="doc-card-prefix"></div>


## Change Settings

### getRuntimeSettings

* getRuntimeSettings&#40;&#41;: *Promise&lt;[RuntimeSettings](./interface/RuntimeSettings.md)&gt;*

  Returns the current runtime settings.
  
  ```js
  let settings = await reader.getRuntimeSettings();
  settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE; // Decodes only QR code.
  await reader.updateRuntimeSettings(settings);
  ```
  *@see* [RuntimeSettings](./interface/RuntimeSettings.md)

<div class="doc-card-prefix"></div>


### updateRuntimeSettings

* updateRuntimeSettings&#40;settings: *[RuntimeSettings](./interface/RuntimeSettings.md) &#124; string*&#41;: *Promise&lt;void&gt;*

  Updates runtime settings with a given struct or a preset template represented by one of the following strings
  
  - `speed`: fast but may miss a few codes;
  - `coverage`: slow but try to find all codes, this is the default setting for a `BarcodeReader` instance;
  - `balance`: between `speed` and `coverage`;
  - `single`: optimized for scanning one single barcode from a video input, this is supported only by the sub-class [`BarcodeScanner`](./BarcodeScanner.md) and is also the default setting for a `BarcodeScanner` instance.
  
  ```js
  await reader.updateRuntimeSettings('balance');
  let settings = await reader.getRuntimeSettings();
  settings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED;
  await reader.updateRuntimeSettings(settings);
  ```

<div class="doc-card-prefix"></div>


### resetRuntimeSettings

* resetRuntimeSettings&#40;&#41;: *Promise&lt;void&gt;*

  Resets all parameters to default values.
  
  For a `BarcodeReader` instance, it is equivalent to setting the `coverage` template.

  For a [`BarcodeScanner`](./BarcodeScanner.md) instance, it is equivalent to setting the `single` template.
  
  ```js
  await reader.resetRuntimeSettings();
  ```

<div class="doc-card-prefix"></div>


### getModeArgument

* getModeArgument&#40;modeName: *string*, index: *number*, argumentName: *string*&#41;: *Promise&lt;string&gt;*

  Returns the argument value for the specified mode parameter.
 
  ```js
  let argumentValue = await reader.getModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy");
  ```

  *@see* [C++ getModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#getmodeargument)

<div class="doc-card-prefix"></div>


### setModeArgument

* setModeArgument&#40;modeName: *string*, index: *number*, argumentName: *string*, argumentValue: *string*&#41;: *Promise&lt;string&gt;*

  Sets the argument value for the specified mode parameter.

  ```js
  await reader.setModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy", "1");
  ```

  *@see* [C++ setModeArgument](https://www.dynamsoft.com/barcode-reader/programming/cplusplus/api-reference/cbarcodereader-methods/parameter-and-runtime-settings-basic.html?ver=latest#setmodeargument)

<div class="doc-card-prefix"></div>


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

<div class="doc-card-prefix"></div>


### oriCanvas

* `readonly` oriCanvas: *[HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement) &#124; [OffscreenCanvas](https://developer.mozilla.org/en-US/docs/Web/API/OffscreenCanvas)*

  An [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/Canvas) that holds the original image. The original image refers to the actual image the library tried to read barcodes from.

  ```js
  reader.bSaveOriCanvas = true;
  let results = await reader.decode(source);
  document.body.append(reader.oriCanvas);
  ```

<div class="doc-card-prefix"></div>



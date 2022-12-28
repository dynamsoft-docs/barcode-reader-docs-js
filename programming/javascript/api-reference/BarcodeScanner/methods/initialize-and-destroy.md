---
layout: default-layout
title: BarcodeScanner Initialize and Destroy Methods - Dynamsoft Barcode Reader JavaScript Edition API
description: This page shows BarcodeScanner Initialize and Destroy Methods of Dynamsoft Barcode Reader JavaScript SDK.
keywords: createInstance, destroy, getUIElement, setUIElement, initialize and destroy methods, BarcodeScanner, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: false
permalink: /programming/javascript/api-reference/BarcodeScanner/methods/initialize-and-destroy.html
---
<!--NOTE, This page is used until version 8.2.3-->


# Javascript API Reference - `BarcodeScanner` Initialize and Destroy Methods

| Method               | Description |
|----------------------|-------------|
| [`createInstance()`](#createinstance) | Create a  `BarcodeScanner` object. |
| [`destroy()`](#destroy) | Destroy the `BarcodeScanner` object. |
| [`getUIElement()`](#getuielement) | Get HTML element containing the `BarcodeScanner` object. |
| [`setUIElement()`](#setuielement) | Set HTML element containing the `BarcodeScanner` object. |

---

## createInstance

Create a `BarcodeScanner` object. Overrides `BarcodeReader.createInstance`.

```javascript
createInstance(config) returns Promise
```

### Parameters

`config`<sub>optional</sub> *any*  

### Return Value

<code>Promise<<a href="../#barcodescanner">BarcodeScanner</a>></code>

[test](../index.md#barcodescanner)

### Sample

```javascript
let scanner = await Dynamsoft.BarcodeScanner.createInstance();
```

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## destroy

Destroy the `BarcodeScanner` object. Equivalent to the previous method `deleteInstance()`. Overrides `BarcodeReader.destroy`.

```javascript
destroy() returns Promise
```

### Return Value

`Promise<any>`

## getUIElement

Get the HTML element containing the `BarcodeScanner` object.

```javascript
getUIElement() returns HTMLElement
```

### Return Value

`HTMLElement`

### Sample

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

## setUIElement

Set HTML element containing the `BarcodeScanner` object.

```javascript
setUIElement(elementOrUrl) returns Promise
```

### Parameters

`elementOrUrl` *HTMLElement | string*  

### Return Value

`Promise<void>`

### Sample

```html
<!-- Define an element that shows only the video input -->
<!-- The video element will be created and appended to the DIV element with the class dce-video-container , make sure the class name is the same.
Besides, the CSS property position of the DIV element must be either relative, absolute, fixed, or sticky. -->
<div class="dce-video-container" style="position:relative;width:100%;height:500px;"></div>
<script>
    let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
    await scanner.setUIElement(document.getElementsByClassName("dce-video-container")[0]);
    await scanner.open();
</script>
```

[Read barcodes from live camera](https://demo.dynamsoft.com/dbr_wasm/barcode_reader_javascript.html)

### :+1: Tips and Tricks 

* This API changes the UI on the fly. If you want the UI to change as soon as the camera is created, use [`defaultUIElementURL`](../accessors.md#defaultuielementurl) instead.

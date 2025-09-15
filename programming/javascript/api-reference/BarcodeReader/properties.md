---
layout: default-layout
title: BarcodeReader Properties - Dynamsoft Barcode Reader JavaScript Edition API
description: This page shows BarcodeReader Properties of Dynamsoft Barcode Reader JavaScript SDK.
keywords: _bUseFullFeature, bDestroyed, bSaveOriCanvas, oriCanvas, properties, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: false
permalink: /programming/javascript/api-reference/BarcodeReader/properties.html
---
<!--NOTE, This page is used until version 8.2.3-->

> This page is applicable to version 8.2.3

# Javascript API Reference - `BarcodeReader` Properties

| Property             | Description |
|----------------------|-------------|
| [_bUseFullFeature](#_busefullfeature) | If set to `false`, use the compact-featured WASM module. |
| `bDestroyed` | Indicates whether a `BarcodeReader` object has been destroyed. | 
| `bSaveOriCanvas` | If set to `true`, save the original image to canvas. | 
| `oriCanvas` | The original canvas element. | 

---

## _bUseFullFeature

Set usage of compact or full featured SDK. If set to `false`, use the compact-featured WASM module.

*Note: this API may change in the future.*

```javascript
Dynamsoft.BarcodeReader._bUseFullFeature = Boolean
```

### Default Value

`false` for web

### Sample

```javascript
Dynamsoft.BarcodeReader._bUseFullFeature = false;
await Dynamsoft.BarcodeReader.loadWasm();
```

### :+1: Tips and Tricks

* Check out [what features are included](../../user-guide/features-requirements.md#compact-and-full-editions) in compact and full version.
* This property **must** be set before [loadWasm](methods/initialize-and-destroy.md#loadwasm).
* We recommend using the compact version in video decoding for its small size and quick initialization.
* This property cannot be set in NodeJS and will always use the fully featured version. 

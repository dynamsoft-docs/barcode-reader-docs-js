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


# Initialization Control

The following static methods and properties help to set up the runtime environment for the library.

* [_bUseFullFeature](#_busefullfeature)
* [engineResourcePath](#engineresourcepath)
* [loadWasm](#loadwasm)
* [isLoaded](#isloaded)
* [version](#version)
* [detectEnvironment](#detectenvironment)

<div class="doc-card-prefix"></div>

> ### _bUseFullFeature
> <hr>
> `static` _bUseFullFeature: *boolean*
> <hr>
> Whether to use the full engine. The property needs to be set before [loadWasm](#loadwasm). The default is 'false'.
> #### Example
> ```js
> Dynamsoft.DBR.BarcodeReader._bUseFullFeature = true;
> await Dynamsoft.DBR.BarcodeReader.loadWasm();
> ```
> 
> *@see* [differences between compact and full WASM engines](../../user-guide/?ver=latest#specify-which-engine-to-use).

<div class="doc-card-prefix"></div>

> ### engineResourcePath
> <hr>
> `static` engineResourcePath: *string*
> <hr>
> Specifies the path to find the engine(s). The property needs to be set before [loadWasm](#loadwasm). If not specified, the library will try to find the engine in the same location as the main JavaScript file (dbr.js).
> #### Example
> ```js
> Dynamsoft.DBR.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/";
> await Dynamsoft.DBR.BarcodeReader.loadWasm();
> ```

<div class="doc-card-prefix"></div>

> ### loadWasm
> <hr>
> `static` loadWasm&#40;&#41;: *Promise&lt;void&gt;*
> <hr>
> Downloads and compiles the engine to get it loaded/ready for a BarcodeReader or BarcodeScanner instance to be created. You can call this API to silently set the operating environment of the library as soon as the page is loaded, avoiding unnecessary waiting time when using the library later.
> 
> If this API is not called beforehand, it will be called automatically when creating an instance of BarcodeReader or BarcodeScanner.
> #### Example
> ```js
> window.addEventListener('DOMContentLoaded', (event) => {
>    Dynamsoft.DBR.BarcodeReader.loadWasm();
> });
> ```

<div class="doc-card-prefix"></div>

> ### isLoaded
> <hr>
> `static` isLoaded&#40;&#41;: *boolean*
> <hr>
> Returns whether the engine is loaded/ready.

<div class="doc-card-prefix"></div>

> ### version
> <hr>
> `readonly` `static` version: *string*
> <hr>
> Returns the version of the library including the detailed version numbers of the engine and the main JavaScript code.
> 
> Needs to call after [loadWasm](#loadwasm).
> #### Example
> ```js
> console.log(Dynamsoft.DBR.BarcodeReader.version); // "loading...(JS 8.2.5.20210426)"
> await Dynamsoft.DBR.BarcodeReader.loadWasm();
> console.log(Dynamsoft.DBR.BarcodeReader.version); // "8.4.0.8960(JS 8.2.5.20210426)"
> ```

<div class="doc-card-prefix"></div>

> ### detectEnvironment
> <hr>
> `static` detectEnvironment&#40;&#41;: *Promise&lt;any&gt;*
> <hr>
> Returns a report on the current running environments.
> #### Example
> ```js
> console.log(Dynamsoft.DBR.BarcodeReader.detectEnvironment());
> // {"wasm":true, "worker":true, "getUserMedia":true, "camera":true, "browser":"Chrome", "version":90, "OS":"Windows"}
> ```
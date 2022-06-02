---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - v8.2.5 Initialization Control
description: This page shows the BarcodeReader Class of Dynamsoft Barcode Reader JavaScript SDK.
keywords: BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: BarcodeReader
permalink: /programming/javascript/api-reference/InitializationControl-v8.2.5.html
---

# Initialization Control

The following static methods and properties help to set up the runtime environment for the library.

* [_bUseFullFeature](#_busefullfeature)
* [engineResourcePath](#engineresourcepath)
* [loadWasm](#loadwasm)
* [isLoaded](#isloaded)
* [version](#version)
* [detectEnvironment](#detectenvironment)



## _bUseFullFeature

Whether to use the full engine. The property needs to be set before [loadWasm](#loadwasm).

```typescript
static _bUseFullFeature: boolean
```

**Default value**

`false`

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader._bUseFullFeature = true;
await Dynamsoft.DBR.BarcodeReader.loadWasm();
```

**See also** 

* [differences between compact and full WASM engines](../user-guide/index.html#specify-which-engine-to-use).



## engineResourcePath

Specifies the path to find the engine(s). The property needs to be set before [loadWasm](#loadwasm). If not specified, the library will try to find the engine in the same location as the main JavaScript file (dbr.js).

```typescript
static engineResourcePath: string
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/";
await Dynamsoft.DBR.BarcodeReader.loadWasm();
```



## loadWasm

Downloads and compiles the engine to get it loaded/ready for a BarcodeReader or BarcodeScanner instance to be created. You can call this API to silently set the operating environment of the library as soon as the page is loaded, avoiding unnecessary waiting time when using the library later.

If this API is not called beforehand, it will be called automatically when creating an instance of BarcodeReader or BarcodeScanner.

```typescript
static loadWasm(): Promise<void>
```

**Code Snippet**

```js
window.addEventListener('DOMContentLoaded', (event) => {
   Dynamsoft.DBR.BarcodeReader.loadWasm();
});
```



## isLoaded

Returns whether the engine is loaded/ready.

```typescript
static isLoaded(): boolean
```



## version

Returns the version of the library including the detailed version numbers of the engine and the main JavaScript code.

Needs to call after [loadWasm](#loadwasm).

```typescript
readonly static version: string
```

**Code Snippet**

```js
console.log(Dynamsoft.DBR.BarcodeReader.version);
await Dynamsoft.DBR.BarcodeReader.loadWasm();
console.log(Dynamsoft.DBR.BarcodeReader.version);
```



## detectEnvironment

Returns a report on the current running environments.

```typescript
static detectEnvironment(): Promise<any>
```

**Code Snippet**

```js
console.log(Dynamsoft.DBR.BarcodeReader.detectEnvironment());
// {"wasm":true, "worker":true, "getUserMedia":true, "camera":true, "browser":"Chrome", "version":90, "OS":"Windows"}
```

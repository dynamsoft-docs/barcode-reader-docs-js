---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript Edition API - Initialization Control
description: Follow this API reference and learn to set up initialization control functionality in Dynamsoft Barcode Reader JavaScript Edition.
keywords: BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: BarcodeReader
permalink: /programming/javascript/api-reference/InitializationControl.html
---

# Initialization Control

The following static methods and properties help to set up the runtime environment for the library.

- [Initialization Control](#initialization-control)
  - [engineResourcePath](#engineresourcepath)
  - [loadWasm](#loadwasm)
  - [isWasmLoaded](#iswasmloaded)
  - [version](#version)
  - [detectEnvironment](#detectenvironment)
  - [onWarning](#onwarning)

## engineResourcePath

Specifies the path to find the engine(s). The property needs to be set before [loadWasm](#loadwasm). If not specified, the library will try to find the engine in the same location as the main JavaScript file (dbr.js).

```typescript
static engineResourcePath: string
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.3.1/dist/";
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

### :+1: Tips and Tricks 
* [How to get rid of the delay when opening the camera?](delay-when-open-camera.html)

## isWasmLoaded

Returns whether the engine is loaded/ready.

```typescript
static isLoaded(): boolean
```

## version

Returns the version of the library including the detailed version numbers of the engine and the main JavaScript code.

The engine version is only valid after [loadWasm](#loadwasm) has been called.

```typescript
readonly static version: string
```

**Code Snippet**

```js
console.log(Dynamsoft.DBR.BarcodeReader.version);
// loading...(JS 8.8.3.20211011)
await Dynamsoft.DBR.BarcodeReader.loadWasm();
console.log("When loaded..." + Dynamsoft.DBR.BarcodeReader.version);
// 8.8.0.10403(JS 8.8.3.20211011)
```

## detectEnvironment

Returns a report on the current running environments.

```typescript
static detectEnvironment(): Promise<any>
```

**Code Snippet**

```js
console.log(Dynamsoft.DBR.BarcodeReader.detectEnvironment());
// {"wasm":true, "worker":true, "getUserMedia":true, "camera":true, 
// "browser":"Chrome", "version":90, "OS":"Windows"}
```

## onWarning

A callback which is triggered when the running environment is not ideal. In this version, it may get triggered in two scenarios:

1. If the page is opened from the disk
2. The page is hosted in a HTTP site without SSL

In both cases, the following warning is returned:

```js
{
    id: 2,
    message: "Not connected via SSL (HTTPS), the SDK may not work correctly."
}
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeScanner.onWarning = warning => console.log(warning.message);
```

**See Also**

[Warning](interface/warning.md)
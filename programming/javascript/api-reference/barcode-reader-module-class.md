---
layout: default-layout
title: BarcodeReader Module - Dynamsoft Barcode Reader JavaScript Edition API
description: This page introduces APIs related to the BarcodeReaderModule Class of Dynamsoft Barcode Reader JavaScript Edition.
keywords: capture vision, Barcode Reader Module, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: BarcodeReader Module
---

# BarcodeReaderModule Class

The `BarcodeReaderModule` Class is defined in the namespace `Dynamsoft.DBR`. It defines common functionality.

| API Name                                           | Description                                                         |
| -------------------------------------------------- | ------------------------------------------------------------------- |
| static [`getVersion()`](#getversion)               | Returns the version of the `BarcodeReader` module.                  |
| static [`engineResourcePath`](#engineresourcepath) | Sets or returns the path to find the resources files (.wasm, etc.). |

### getVersion

Returns the version of the `BarcodeReader` module.

**Code snippet**

```javascript
const version = await Dynamsoft.DBR.BarcodeReaderModule.getVersion();
console.log(version);
```

### engineResourcePath

Sets or returns the path to find the resources files (.wasm, etc.).

**Code snippet**

```javascript
Dynamsoft.DBR.BarcodeReaderModule.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.0.11/dist/";
```
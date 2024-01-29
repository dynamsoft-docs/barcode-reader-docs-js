---
layout: default-layout
title: BarcodeReaderModule Class - Dynamsoft Barcode Reader JavaScript Edition API
description: This page introduces APIs related to the BarcodeReaderModule Class of Dynamsoft Barcode Reader JavaScript Edition.
keywords: capture vision, Barcode Reader Module, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# BarcodeReaderModule Class

The `BarcodeReaderModule` Class is defined in the namespace `Dynamsoft.DBR`.

| API Name                           | Description                                        |
| ---------------------------------- | -------------------------------------------------- |
| static [getVersion()](#getversion) | Returns the version of the `BarcodeReader` module. |

### getVersion

Returns the version of the `BarcodeReader` module.

```typescript
static getVersion(): string;
```

**Code snippet**

```javascript
const version = Dynamsoft.DBR.BarcodeReaderModule.getVersion();
console.log(version);
```
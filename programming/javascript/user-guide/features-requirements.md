---
layout: default-layout
title: Features & Requirements - Dynamsoft Barcode Reader JavaScript Edition
description: This page shows features and requirements of Dynamsoft Barcode Reader JavaScript SDK.
keywords: user guide, features, requirements, javascript, js
needAutoGenerateSidebar: true
permalink: /programming/javascript/user-guide/features-requirements.html
---

# Features & Requirements

## Features

### Supported Symbologies:

- 1D barcode: *Code 39 (including Code 39 Extended)*, *Code 128*, *Code 93*, *Codabar*, *Interleaved 2 of 5 (ITF)*, *EAN-13*, *EAN-8*, *UPC-A*, *UPC-E*, *Industrial 2 of 5* (Code 2 of 5 Industry, Standard 2 of 5, Code 2 of 5), and *MSI (Modified Plessey)*.
- 2D barcode: *PDF417*, *QR (including Micro QR Code and Model 1)*, *DataMatrix*, *Aztec*, *MaxiCode*, and *DotCode*.    
- GS1 Databar: *Omnidirectional*, *Truncated*, *Stacked*, *Stacked Omnidirectional*, *Expanded*, *Expanded Stacked* and *Limited*.
- Patch Code
- GS1 Composite Code  
- Postal Code: *USPS Intelligent Mail*, *PostNet*, *Planet*, *Australian Post*, *UK Royal Mail (RM4SCC)*.  

### Supported Data Sources: 

`Blob`, `HTMLImageElement`, `HTMLVideoElement`, and `URL`, etc.  

### Compact and Full Editions  

Two editions - Compact and Full - are available. The Compact Edition includes basic features with smaller size allowing for faster download and compiling. The Full Edition includes full features but with a larger size.

The following table shows available features between the two editions:
    
  | Features | Compact edition | Full edition |
  |:-:|:-:|:-:|
  | `wasm` size<sup>1</sup>\(gzip\) | 976 KB | 1.3 MB |
  | 1D | &#10003; | &#10003; |
  | QR | &#10003; | &#10003; |
  | Micro QR | - | &#10003; |
  | PDF417 | &#10003; | &#10003; |
  | Micro PDF417 | - | &#10003; |
  | DataMatrix | &#10003; | &#10003; |
  | Aztec | - | &#10003; |
  | MaxiCode | - | &#10003; |
  | Patch Code | - | &#10003; |
  | GS1 Composite Code | - | &#10003; |
  | GS1 DataBar | - | &#10003; |
  | DotCode | - | &#10003; |
  | Postal Code | - | &#10003; |
  | DPM | - | &#10003; |
  | getRuntimeSettings | &#10003; | &#10003; |
  | updateRuntimeSettings | &#10003; | &#10003; |
  | getIntermediateResults | - | &#10003; |
  | initRuntimeSettingsWithString | - | &#10003; |
  | outputSettingsToString | - | &#10003; |
  | *recommended scenario<sup>2</sup>* | Customer Facing Application | Enterprise Solution  |
    
<sup>1</sup> The `wasm` file size is of version 8.1.2. In other versions, the size may differ.  
  
<sup>2</sup> For the scenario where a user only needs to scan a barcode once, the Compact Edition is recommended as it downloads and compiles faster. For scenarios where a user needs to continuously scan many barcodes or where specific uncommon barcodes or advanced features are required, use the Full Edition by simply setting the following before you call `loadWasm()` or `CreateInstance()`.

``` javascript
Dynamsoft.DBR.BarcodeReader._bUseFullFeature = true;
```

## System Requirements

This library requires some advanced features supported by all modern mainstream browsers:

- `WebAssembly`, `Blob`, `URL`/`createObjectURL`, `Web Workers`  
    
    These four features are required for the library to work.

- `MediaDevices`/`getUserMedia` 
    
    This is only required for in-browser video streaming. If a browser does not support this API, "Single Frame Mode" will be used automatically. If the API exists but doesn't work correctly, "Single Frame Mode" can be used as an alternative.  

The following table is a list of supported browsers:

Browser Name | Version
:-: | :-:
Chrome | v57+ (v59+ on Android/iOS<sup>1</sup>)
Firefox | v52+ (v55+ on Android/iOS<sup>1</sup>)
Edge<sup>2</sup> | v16+
Safari<sup>3</sup> | v11+

<sup>1</sup> iOS 14.3+ is required for camera video streaming in Chrome and Firefox or Apps using webviews.
<sup>2</sup> On Edge, due to strict Same-origin policy, you must host the library on the same domain as your webpage.  
<sup>3</sup> Safari 11.2.2 ~ 11.2.6 are not supported.
     
*NOTE*

Apart from the browsers, the operating systems running on the target devices may impose some limitations of their own that could restrict the use of the library. Browser compatibility ultimately depends on whether the browser on that particular operating system supports the features listed above.  


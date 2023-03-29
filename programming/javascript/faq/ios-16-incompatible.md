---
layout: default-layout
title: Why Javascript SDK does not pick up barcodes on iOS 16.4?
keywords: iOS, incompatible, JS, V7.5.0, V8.8.7
description: Why Javascript SDK does not pick up barcodes on iOS 16.4?
needAutoGenerateSidebar: false
---

# Why Javascript SDK does not pick up barcodes on iOS 16.4?

[<< Back to FAQ index](index.md)

## Background

iOS 16.4 was published on March 27th, 2023. In this version, all browsers on iOS have begun to support OffscreenCanvas . Unfortunately, Apple's implementation is incomplete (not the first time that Apple break things around). 
 

Impact: We used OffscreenCanvas in old versions of DBR JS. Specifically in versions **7.5.0 ~ 8.8.7**. Fortunately, we gave up on OffscreenCanvas back in v9.0.0. Therefore, all 9+ versions are not affected.
 
## Solution:

 
The JS team has suggested the following solutions:
 

### Option 1: 

Disable the API directly before creating a BarcodeScanner instance

```
    window.OffscreenCanvas = null;
    let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
    //...
```

The catch: if the user uses OffscreenCanvas themselves or other libraries use OffscreenCanvas, then this will break them!
 

### Option 2: 

If you are not sure whether OffscreenCanvas can be disabled, you can change a setting of the instance after creating the BarcodeScanner instance:
```
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
scanner.ifSaveOriginalImageInACanvas = true;
```
The catch: this approach may slow DBR JS down a little bit it but the difference can be ignored on devices capable of running iOS16.4.
 
### Option 3: 

[Recommended if convenient for the customer] Simply upgrade to version 9! This will get rid of this issue among a few other not-so-vicious issues. And you get better performance with our improved algorithm (upgrade guide).
The catch: upgrade across major versions could have potential stability issues.

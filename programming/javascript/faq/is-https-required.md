---
layout: default-layout
title: Is HTTPs absolutely required?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, HTTPS
description: Is HTTPs absolutely required?
needAutoGenerateSidebar: false
---

# Is HTTPS absolutely required?

[<< Back to FAQ index](index.md)

HTTPS is required to utilize `getUserMedia`/`MediaDevices` and initialize online license keys. If HTTPS is not enabled, and those features are not utilized, the library will default to [singleFrameMode](https://www.dynamsoft.com/barcode-reader/programming/javascript/api-reference/BarcodeScanner/properties.html?ver=latest#singleframemode)(will not have live video capabilities) and you will also need an offline license key.

---
layout: default-layout
title: How to get the logs for the SDK?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, logs
description: How to get the logs for the SDK?
needAutoGenerateSidebar: false
---

# How to get the logs for the SDK?

[<< Back to FAQ index](index.md)

## Version 10
The SDK can provide logs via the `Core` module.
```javascript
Dynamsoft.Core.CoreModule.onLog = console.log;
```

## Version 9
The SDK can provide logs via the browser console. Logging can be activated by the `_onLog` property.

```javascript
Dynamsoft.DBR.BarcodeReader._onLog = console.log;
```

---
layout: default-layout
title: How to get rid of the delay in opening the camera?
keywords: Dynamsoft Barcode Reader, FAQ, delay,camera,loadwasm
description: How to get rid of the delay in opening the camera?
needAutoGenerateSidebar: false
---

# ow to get rid of the delay in opening the camera?

[<< Back to FAQ index](index.md)

There are multiple ways to get rid the delay in opening the camera -


## 1. load Wasm in advance

    ```javascript
    Dynamsoft.DBR.BarcodeReader.loadWasm();
    ```

## 2. pre-open the camera in advance

Run the following code in advance.
```
navigator.mediaDevices.getUserMedia({video: true}).then(mediaStream=>{
  mediaStream.getTracks().forEach((track) => {
    track.stop();
  });
}, err=>{});
```

## 3. Skip Camera inspection(use default camera)

```javascript
scanner.ifSkipCameraInspection = true;
```

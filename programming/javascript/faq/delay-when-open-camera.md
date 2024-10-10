---
layout: default-layout
title: How to get rid of the delay when opening the camera?
keywords: Dynamsoft Barcode Reader, FAQ, delay,camera,loadwasm
description: How to get rid of the delay when opening the camera?
needAutoGenerateSidebar: false
---

# How to get rid of the delay when opening the camera?

[<< Back to FAQ index](index.md)

## Version 10
### 1. Invoke loadWasm
Preload `BarcodeReader` or other specified module proactively to save time on the initial decoding by skipping the module loading at the time of instance creation.

```javascript
await Dynamsoft.Core.CoreModule.loadWasm(["DBR"]);
```
### 2. skip camera inspection
You can bypass the camera selection[ifSkipCameraInspection](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/camera-control.html#ifskipcamerainspection)
```javascript
	cameraEnhancer.ifSkipCameraInspection
```

### 3. Pre-open camera in advance
Run the following code before calling `createInstance`.
```
navigator.mediaDevices.getUserMedia({video: true}).then(mediaStream=>{
  mediaStream.getTracks().forEach((track) => {
    track.stop();
  });
}, err=>{});
```

## Version 9
### 1. Invoke loadWasm in advance

```javascript
Dynamsoft.DBR.BarcodeReader.loadWasm();
```

### 2. Pre-open the camera in advance

Run the following code before calling `createInstance`.
```
navigator.mediaDevices.getUserMedia({video: true}).then(mediaStream=>{
  mediaStream.getTracks().forEach((track) => {
    track.stop();
  });
}, err=>{});
```

### 3. Skip Camera inspection(use default camera)

```javascript
scanner.ifSkipCameraInspection = true;
```

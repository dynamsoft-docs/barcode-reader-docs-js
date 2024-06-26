---
layout: default-layout
title: How to check the camera permissions programmatically in Dynamsoft Barcode Reader JavaScript SDK?
keywords: JavaScript, JS, camera, permission
description: How to check the camera permissions programmatically in Dynamsoft Barcode Reader JavaScript SDK?
needAutoGenerateSidebar: false
---

# How to check the camera permissions programmatically in Dynamsoft Barcode Reader JavaScript SDK?

[<< Back to FAQ index](index.md)

## version 10 or recent
In version 10, use the `dynamsoft camera enhancer` to utilize the [testCameraAccess](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/camera-control.html#testCameraAccess) method to check the camera status programmatically.


## version 9.6.10 till version 10
 you can utilize the [testCameraAccess](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/BarcodeScanner.html#testcameraaccess) method to check the camera status programmatically.

## version older than 9.6.10
 you can check the status using a try-catch block as shown below:

```javascript
try {
  await scanner.open(); // or 'await scanner.show()'
} catch(e) {
  if(e.name === "NotAllowedError") {
    // it means the user denied permission  
    // add your code here to guide users to grant permission
  }
}
```

In case permission is denied, you can prompt the user (using an alert or something similar) to manually grant permission for your website to access the camera via the site settings.

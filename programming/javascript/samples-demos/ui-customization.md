---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - UI Customization Samples
description: Dynamsoft Barcode Reader SDK for JavaScript - UI Customization
keywords: javascript, js, barcode, vanilla, ui
noTitleIndex: true
breadcrumbText: UI Customization
permalink: /programming/javascript/samples-demos/ui-customization.html
---

# JavaScript UI Customization Samples

Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") provides a built-in GUI to help developers build an interactive barcode reading interface.

## Default GUI

The following official sample demonstrates the default GUI built into the library.

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/2.ui-tweaking/1.read-video-show-result.html">Use the Default Camera UI - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/main/2.ui-tweaking/1.read-video-show-result.html">Use the Default Camera UI - Source Code</a>

**GUI Elements**

If you check the GUI on the demo page, you will find that it consists of the following elements

* The video element that streams the video from a camera
* A laser beam moving vertically which indicates the working status of the library
* A dropdown box for selecting a camera
* A dropdown box for specifying the resolution for the selected camera
* A close button that closes the GUI when clicked

There are a few other elements

* Before the video starts streaming, there is a spinner that indicates the loading process
* When a barcode is found, the location of the barcode is highlighted in the video stream
* If no camera is found on the device or camera access is denied on the page, the GUI will show a camera icon, which, when clicked, allows the user to select a local image or invoke the system camera interface

## Hide Built-in Controllers

As mentioned above, the default UI comes with quite a few elements. Some of them might not fit the style of your own application. The following code snippet removes the camera selector, the resolution selector, the close button as well as changes the backgournd color.

```javascript
document.getElementById('UIElement').appendChild(scanner.getUIElement());
document.querySelector('#UIElement div').style.background = '';
document.getElementsByClassName('dce-sel-camera')[0].hidden = true;
document.getElementsByClassName('dce-sel-resolution')[0].hidden = true;
document.getElementsByClassName('dce-btn-close')[0].hidden = true;
```

Check out the official sample:

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/2.ui-tweaking/2.read-video-no-extra-control.html">Hide Built-in Controllers - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/main/2.ui-tweaking/2.read-video-no-extra-control.html">Hide Built-in Controllers - Source Code</a>

## Use External Controllers

Based on the previous sample, you can build your own UI elements to control the barcode scanning process.

For example, the following code adds a camera selector

```html
<select id="cameraList"></select>
```

```javascript
async function updateCameras() {
    let cameras = await scanner.getAllCameras();
    let cameraList = document.getElementById('cameraList');
    cameraList.options.length = 0;
    for (let camera of cameras) {
        let opt = new Option(camera.label, camera.deviceId);
        cameraList.options.add(opt);
    }
}
document.getElementById('cameraList').onchange = async function() {
    try {
        await scanner.setCurrentCamera(document.getElementById('cameraList').value);
    } catch (ex) {
        alert('Play video failed: ' + (ex.message || ex));
    }
};
```

For more related customization, check out the following official sample:

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/2.ui-tweaking/3.read-video-with-external-control.html">Use External Controllers - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/main/2.ui-tweaking/3.read-video-with-external-control.html">Use External Controllers - Source Code</a>

## Enlarge the Video Stream

The library is usually used on mobile devices which have small screens. When scanning barcodes with the mobile camera, the video stream will be limited in the video element and may not be clear enough. Ideally, we should use the whole screen to play the video and find barcodes.

The GUI is pure HTML, so changing the size of the element is very easy. For example, the following enlarges the element to be the full size of the viewport.

```javascript
document.getElementById('UIElement').style.height = '100vh';
document.getElementById('UIElement').style.width = '100vw';
document.getElementById('UIElement').style.position = 'absolute';
```

Check out the following sample on how to enlarge the video stream to read a barcode and then change it back to its normal size.

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/2.ui-tweaking/4.difference-video-size.html">Enlarge the Video Stream - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/main/2.ui-tweaking/4.difference-video-size.html">Enlarge the Video Stream - Source Code</a>

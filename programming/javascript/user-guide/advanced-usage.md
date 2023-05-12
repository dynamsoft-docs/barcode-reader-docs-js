---
layout: default-layout
title: Advanced Usage - Dynamsoft Barcode Reader JavaScript Edition
description: This page shows how to customize advanced features of Dynamsoft Barcode Reader JavaScript SDK.
keywords: user guide, advanced customizations, debug, area, region, javascript, js
needAutoGenerateSidebar: true
permalink: /programming/javascript/user-guide/advanced-usage.html
---

# Advanced Usage

- [Advanced Usage](#advanced-usage)
  - [Read a specific area/region](#read-a-specific-arearegion)
  - [Always draw a square as the scan region](#always-draw-a-square-as-the-scan-region)
  - [Account for newline characters in the barcode result](#account-for-newline-characters-in-the-barcode-result)
  - [Show internal logs](#show-internal-logs)
  - [Cut down power usage](#cut-down-power-usage)
  - [Remove highlighting of unverified linear barcodes](#remove-highlighting-of-unverified-linear-barcodes)
  - [Set mode arguments](#set-mode-arguments)
  - [Display images in different stages of the reading process](#display-images-in-different-stages-of-the-reading-process)
  - [Hosting the SDK](#hosting-the-sdk)
    - [Step One: Deploy the dist folder](#step-one-deploy-the-dist-folder)
    - [Step Two: Configure the Server](#step-two-configure-the-server)
    - [Step Three: Include the SDK from the server](#step-three-include-the-sdk-from-the-server)

## Read a specific area/region

To speed up the scanning process, you can choose to scan only a specific area/region.

```javascript
let settings = await scanner.getRuntimeSettings();
/*
 * The following code shrinks the decoding region by 25% on all sides
 */
settings.region.regionMeasuredByPercentage = 1;
settings.region.regionLeft = 25;
settings.region.regionTop = 25;
settings.region.regionRight = 75;
settings.region.regionBottom = 75;
await scanner.updateRuntimeSettings(settings);
```

[Try in JSFiddle](https://jsfiddle.net/DynamsoftTeam/taykq592/)

## Always draw a square as the scan region

When reading square barcodes such as QR codes, it will help to keep the scan region also a square, the following code does the trick

```javascript
scanner.onPlayed = async info => {
    let sideLen = Math.min(info.width,info.height)*0.4;
    let precentW = Math.round(sideLen/info.width*100)
    let precentH = Math.round(sideLen/info.height*100);
    let rs = await scanner.getRuntimeSettings();
    rs.region.regionLeft = (100 - precentW) / 2;
    rs.region.regionRight = (100 + precentW) / 2;
    rs.region.regionTop = (100 - precentH) / 2;
    rs.region.regionBottom = (100 + precentH) / 2;
    rs.region.regionMeasuredByPercentage = 1;
    await scanner.updateRuntimeSettings(rs);
}
```

[Try in JSFiddle](https://jsfiddle.net/DynamsoftTeam/srny764o/)

## Account for newline characters in the barcode result

When it comes to HTML, newline characters ( `\n` ) are not interpreted as they normally would. Therefore, if a barcode result contains a newline character, and you display the result in an modal dialogue box or some other text elements, then the newline character will probably be ignored.

There are two ways in which you can resolve this:

1. Wrap the element used to display the result in a `<pre>` element.
2. Manually replace each `\n` character in the result with `<br>`

## Show internal logs

Include the following in your code to print internal logs in the console.

```javascript
Dynamsoft.DBR.BarcodeReader._onLog = console.log;
```

## Cut down power usage

> Applicable to version 9.2.10+

BarcodeScanner is designed for best performance, which means once it starts scanning, it'll keep the CPU focused on barcode reading with no pause. As a result, it quickly drains the device battery and causes the device to overheat. To cut down power usage, we can configure two things:

1. Pause the barcode reading when capturing the next video frame;
2. Explicitly pause the SDK altogether for a short period after each successful read.

```js
const scanSettings = await scanner.getScanSettings();
scanSettings.captureAndDecodeInParallel = false; // When set to false, the SDK will pause reading when capturing the next frame. Otherwise, the SDK will capture the next frame while reading the current frame, which means it never stops.
scanSettings.intervalTime = 1000; // Tells the SDK to pause for 1 second after reading a frame before capturing the next frame.
await scanner.updateScanSettings(scanSettings);
```

## Remove highlighting of unverified linear barcodes

> Applicable to version 9.3.0+

When linear barcodes are found but not verified, they will be highlighted in the video feed, but in a lighter color. If you wish to highlight only the verified barcodes, you can use the following code:

```js
scanner.barcodeFillStyleBeforeVerification = "transparent"; // default value: "rgba(248,252,0,0.2)"
scanner.barcodeStrokeStyleBeforeVerification = "transparent"; // default value: "transparent"
```

## Set mode arguments

To precisely control a mode, you can adjust its specific parameters.

```javascript
let settings = await scanner.getRuntimeSettings();

/*
 * The following code sets the sensitivity of the TextureDetectionModes to 9
 */

settings.furtherModes.textureDetectionModes = [
    Dynamsoft.DBR.EnumTextureDetectionMode.TDM_GENERAL_WIDTH_CONCENTRATION, 0, 0, 0, 0, 0, 0, 0
];

await scanner.updateRuntimeSettings(settings);
// The 2nd parameter 0 specifies the 0th mode of TextureDetectionModes, 
// which is "Dynamsoft.DBR.EnumTextureDetectionMode.TDM_GENERAL_WIDTH_CONCENTRATION" in this case.
await scanner.setModeArgument("TextureDetectionModes", 0, "Sensitivity", "9");
```

## Display images in different stages of the reading process

The original canvases are saved when setting `ifSaveOriginalImageInACanvas` to `true`. The method `getOriginalImageInACanvas()` returns a canvas which holds the image to be passed to the barcode reader engine for decoding. 

The intermediate result canvases are created when `intermediateResultTypes` is set to a value other than `IRT_NO_RESULT` . Then these intermediate result canvases can be returned with the method `getIntermediateCanvas()` to be used for showing and debugging the barcode reading process. 

> *NOTE*
>  
> For efficiency, the SDK may utilize WebGL (Web Graphics Library) for preprocessing an image before passing it to the barcode reader engine. If WebGL is used, the image captured from the camera will not be rendered on the canvas, instead, it gets processed by WebGL first and then is passed to the barcode reader engine directly. In this case, there won't be an original canvas.
> 
> Therefore, if `ifSaveOriginalImageInACanvas` is set to `true` for a `BarcodeScanenr` instance, the WebGL feature will be disabled for that instance.
>
> You can manually disable the WebGL feature by setting `_bUseWebgl` as `false`. If WebGL is disabled, when you try to get the intermediate result canvas (with `getIntermediateCanvas()`) specified by `EnumIntermediateResultType.IRT_ORIGINAL_IMAGE` , the canvas will be exactly the same image as you would get with `getOriginalImageInACanvas()` .

The following shows how to display these images on the page

```html
<div id='scannerV' style="width:50vw;height:50vh"></div>
<div id='cvses'></div>
```

```javascript
// original canvas
(async () => {
    let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
    document.getElementById('scannerV').appendChild(scanner.getUIElement());
    scanner.ifSaveOriginalImageInACanvas = true;
    scanner.onUniqueRead = async (txt, result) => {
        try {
            let cvs = scanner.getOriginalImageInACanvas();
            document.getElementById('cvses').appendChild(cvs);
            scanner.destroyContext();
        } catch (ex) {
            console.error(ex);
        }
    };
    await scanner.show();
})();
```

```javascript
// intermediate result canvas
(async () => {
    let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
    document.getElementById('scannerV').appendChild(scanner.getUIElement());
    let rs = await scanner.getRuntimeSettings();
    rs.intermediateResultTypes = Dynamsoft.DBR.EnumIntermediateResultType.IRT_ORIGINAL_IMAGE;
    await scanner.updateRuntimeSettings(rs);
    scanner.onUniqueRead = async (txt, result) => {
        try {
            let cvss = await scanner.getIntermediateCanvas();
            for (let cvs of cvss) {
                document.getElementById('cvses').appendChild(cvs);
            }
            scanner.destroyContext();
        } catch (ex) {
            console.error(ex);
        }
    };
    await scanner.show();
})();
```

## Hosting the SDK

### Step One: Deploy the dist folder

Once you have downloaded the SDK, you can locate the "dist" directory and copy it to your server (usually as part of your website / web application).

Some of the files in this directory:

* `dbr.js` // The main SDK file
* `dbr.mjs` // For using the SDK as a module (`<script type="module">`)
* `dbr.ui.html` // Defines the default scanner UI
* `dbr-<version>.worker.js` // Defines the worker thread for barcode reading
* `dbr-<version>.wasm.js` // Compact edition of the SDK (.js)
* `dbr-<version>.wasm` // Compact edition of the SDK (.wasm)
* `dbr-<version>.full.wasm.js` // Full edition of the SDK (.js)
* `dbr-<version>.full.wasm` // Full edition of the SDK (.wasm)

### Step Two: Configure the Server

* Set the MIME type for `.wasm` as `application/wasm` on your webserver.
  
  The goal is to configure your server to send the correct Content-Type header for the wasm file so that it is processed correctly by the browser.

  Different types of webservers are configured differently, for example:

  + <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Learn/Server-side/Apache_Configuration_htaccess#media_types_and_character_encodings" title="Apache">Apache</a>
  + <a target="_blank" href="https://docs.microsoft.com/en-us/iis/configuration/system.webserver/staticcontent/mimemap" title="IIS">IIS</a>
  + <a target="_blank" href="https://www.nginx.com/resources/wiki/start/topics/examples/full/#mime-types" title="NGINX">NGINX</a>

* Enable HTTPS

  Due to the browser <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Web/Security/Secure_Contexts" title="security restriction">security restriction</a> on camera video streaming access, a secure HTTPS connection is required to use the SDK with camera.

  > For convenience, self-signed certificates can be used during development and testing.

### Step Three: Include the SDK from the server

Now that the SDK is hosted on your server, you can include it accordingly.

```html
<script src="https://www.yourwebsite.com/dynamsoft-javascript-barcode/dist/dbr.js"></script>
```

Optionally, you may also need to [specify the location of the "engine" files](index.md#specify-the-location-of-the-engine-files).

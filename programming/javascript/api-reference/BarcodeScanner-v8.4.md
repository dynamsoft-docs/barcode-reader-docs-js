---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - BarcodeScanner
description: This page shows the BarcodeScanner class of Dynamsoft Barcode Reader JavaScript SDK.
keywords: BarcodeScanner, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: BarcodeScanner
---


# BarcodeScanner

A barcode scanner object gets access to a camera via the [MediaDevices](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices) interface, then uses its built-in UI to show the camera input and perform continuous barcode scanning on the incoming frames.

The default built-in UI of each barcode scanner is defined in the file "dbr.scanner.html". If used directly, the UI will fit the entire page and sit on top. There are a few ways to customize it, read more on how to [Customize the UI](https://www.dynamsoft.com/barcode-reader/programming/javascript/user-guide/?ver=latest#customize-the-ui).

Although a barcode scanner is designed to scan barcodes from a video input, it also supports a special mode called [singleFrameMode](#singleFrameMode) which allows the user to select a still image or take a shot with the mobile camera for barcode scanning.

The `BarcodeScanner` is a child class of [BarcodeReader](./BarcodeReader.md) and inherits all its methods and properties which will not be covered in this article.

The following code snippet shows the basic usage of the `BarcodeScanner` class.

```js
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
scanner.onUnduplicatedRead = txt => console.log(txt);
await scanner.show();
```

<br />

## Index

[**Create and Destroy Instances**](#create-and-destroy-instances)

* [createInstance](#createinstance)
* [destroy](#destroy)
* [bDestroyed](#bdestroyed)

<br />

[**Decode Barcodes**](#decode-barcodes)

* [onUnduplicatedRead](#onunduplicatedread)
* [onFrameRead](#onframeread)
* [decodeCurrentFrame](#decodecurrentframe)

<br />

[**UI Interaction**](#ui-interaction)

* [show](#show)
* [hide](#hide)
* [pauseScan](#pausescan)
* [resumeScan](#resumescan)

<br />

[**Scan Settings**](#scan-settings)

* [bPlaySoundOnSuccessfulRead](#bplaysoundonsuccessfulread)
* [soundOnSuccessfullRead](#soundonsuccessfullread)
* [bVibrateOnSuccessfulRead](#bvibrateonsuccessfulread)
* [vibrateDuration](#vibrateduration)
* [singleFrameMode](#singleFrameMode)
* [getScanSettings](#getscansettings)
* [updateScanSettings](#updatescansettings)

<br />

[**UI Control**](#ui-control)

* [getUIElement](#getuielement)
* [setUIElement](#setuielement)
* [defaultUIElementURL](#defaultuielementurl)
* [regionMaskFillStyle](#regionmaskfillstyle)
* [regionMaskLineWidth](#regionmasklinewidth)
* [regionMaskStrokeStyle](#regionmaskstrokestyle)
* [barcodeFillStyle](#barcodefillstyle)
* [barcodeLineWidth](#barcodelinewidth)
* [barcodeStrokeStyle](#barcodestrokestyle)

<br />

[**Camera Control**](#camera-control)

* [getAllCameras](#getallcameras)
* [getCurrentCamera](#getcurrentcamera)
* [setCurrentCamera](#setcurrentcamera)
* [getResolution](#getresolution)
* [setResolution](#setresolution)
* [getVideoSettings](#getvideosettings)
* [updateVideoSettings](#updatevideosettings)
* [openVideo](#openvideo)
* [showVideo](#showvideo)
* [play](#play)
* [onPlayed](#onplayed)
* [pause](#pause)
* [stop](#stop)

[**Advanced Camera Control**](#advanced-camera-control)

* [getCameraSettings](#getcamerasettings)
* [getCapabilities](#getcapabilities)
* [setFrameRate](#setframerate)
* [setColorTemperature](#setcolortemperature)
* [setExposureCompensation](#setexposurecompensation)
* [setZoom](#setzoom)
* [turnOnTorch](#turnontorch)
* [turnOffTorch](#turnofftorch)

<br />

The following are inherited from the `BarcodeReader` Class.

[**Decode Barcodes**](./BarcodeReader.md#decode-barcodes)

* [decode](./BarcodeReader.md#decode)
* [decodeBase64String](./BarcodeReader.md#decodebase64string)
* [decodeUrl](./BarcodeReader.md#decodeurl)
* [decodeBuffer](./BarcodeReader.md#decodebuffer)

<br />

[**Change Settings**](./BarcodeReader.md#decoding-settings)

* [getRuntimeSettings](./BarcodeReader.md#getruntimesettings)
* [updateRuntimeSettings](./BarcodeReader.md#updateruntimesettings)
* [resetRuntimeSettings](./BarcodeReader.md#resetruntimesettings)
* [getModeArgument](./BarcodeReader.md#getmodeargument)
* [setModeArgument](./BarcodeReader.md#setmodeargument)

<br />

[**Auxiliary**](./BarcodeReader.md#auxiliary)

* [bSaveOriCanvas](./BarcodeReader.md#bsaveoricanvas)
* [oriCanvas](./BarcodeReader.md#oricanvas)

<br />

## Create and Destroy Instances

### createInstance

* `static` createInstance&#40;&#41;: *Promise&lt;[BarcodeScanner](#barcodescanner)&gt;*

  Creates a `BarcodeScanner` instance.

  ```js
  let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
  ```

<br />

### destroy

* destroy&#40;&#41;: *Promise&lt;void&gt;*

  Destroys the `BarcodeScanner` instance. If your page needs to create a new instance from time to time, don't forget to destroy unused old instances.

  ```js
  let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
  // ... decode ...
  scanner.destroy();
  ```
  
<br />

### bDestroyed

* bDestroyed: *boolean*

  Indicates whether the instance has been destroyed.

<br />

## Decode Barcodes

### onUnduplicatedRead

* `event` onUnduplicatedRead?: *&#40;txt: string, result: [TextResult](./interface/TextResult.md)&#41; => void*

  This event is triggered when a new, unduplicated barcode is found.

  `txt` holds the barcode text string. `result` contains more detailed info.
  
  The library keeps each barcode result (type and value) in the buffer for a period of time (can be set with [duplicateForgetTime](./interface/ScanSettings.md)) during which if a new result is an exact match, it's seen as a duplicate and will again be kept for that period of time while the old result is removed and so on.

  ```js
  scanner.onUnduplicatedRead = (txt, result) => {
    alert(txt);
    console.log(result);
  }
  ```

<br />

### onFrameRead

* `event` onFrameRead?: *&#40;results: [TextResult](./interface/TextResult.md)&#91;&#93;&#41; => void*

  This event is triggered after the library finishes scanning a frame.

  The `results` object contains all the barcode results in this frame.

  ```js
  scanner.onFrameRead = results => {
    for(let result of results){
      console.log(result.barcodeText);
    }
  };
  ```

<br />

### decodeCurrentFrame

* decodeCurrentFrame&#40;&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

  Scans the current frame of the video for barcodes.

  ```js
  await scanner.showVideo();
  console.log(await scanner.decodeCurrentFrame());
  ```

## UI Interaction

### show

* show&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

  Binds UI, opens the camera, starts decoding, and removes the UIElement `display` style if the original style is `display:none;`.

  ```js
  scanner.onUnduplicatedRead = (txt, result) => { 
    alert(txt); console.log(result); };
  await scanner.show();
  ```

<br />

### hide

* hide&#40;&#41;: *Promise&lt;void&gt;*

  Stops decoding, releases camera and unbinds UI.

  ```js
  await scanner.show();
  //...scan barcodes
  await scanner.hide();
  ```

<br />



<div class="doc-h3-prefix"></div>

### hide

<div class="doc-card-prefix"></div>

> ### hide
>
> <hr>
>
> * hide&#40;&#41;: *Promise&lt;void&gt;*
>
> <hr>
>
> Stop decoding, release camera, unbind UI.
>
> #### Parameters
> 
> - para1: this is para1
> - para2: this is para2
> 
> #### Returns
> 
> *Promise&lt;void&gt;*
>
> A promise that blah blah blah
> 
> #### Example
> 
> ```js
> await scanner.open();
> await scanner.hide();
> 
> await scanner.openVideo();
> await scanner.hide();
> ```


> ### pauseScan
>
> <hr>
> 
> * pauseScan&#40;&#41;: *void*
>
> <hr>
>
>   Pauses the decoding process.
>

<br />

### resumeScan

* resumeScan&#40;&#41;: *void*

  Resumes the decoding process.

<br />

## Scan Settings

* [bPlaySoundOnSuccessfulRead](#bplaysoundonsuccessfulread)
* [soundOnSuccessfullRead](#soundonsuccessfullread)
* [bVibrateOnSuccessfulRead](#bvibrateonsuccessfulread)
* [vibrateDuration](#vibrateduration)
* [singleFrameMode](#singleFrameMode)
* [getScanSettings](#getscansettings)
* [updateScanSettings](#updatescansettings)


### bPlaySoundOnSuccessfulRead

* bPlaySoundOnSuccessfulRead: *(boolean &#124; string)*;

  Whether and when to play sound on barcode recognition (user input is required on iOS for any sound to play). Allowed values are
  
  - `false`: never play sound; <!--never-->
  - `true`: play sound when one or multiple barcodes are found on a frame; <!--always-->
  - `frame`: same as `true`;
  - `unduplicated`: play sound when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, play only once).
  
  ```js
  // A user gesture required. 
  startPlayButton.addEventListener('click', function() {
    scanner.bPlaySoundOnSuccessfulRead = true;
  });
  ```

<br />

<section>

### soundOnSuccessfullRead

* soundOnSuccessfullRead: [HTMLAudioElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLAudioElement)

  The sound to play when the scanner get successfull read.
  ```js
  scanner.soundOnSuccessfullRead = new Audio("./pi.mp3");
  ```

</section>

<br />

### bVibrateOnSuccessfulRead

* bVibrateOnSuccessfulRead: *(boolean &#124; string) = false*

  Whether to vibrate when the scanner reads a barcode successfully.
  Default value is `false`, which does not vibrate.
  Use `frame` or `true` to vibrate when any barcode is found within a frame.
  Use `unduplicated` to vibrate only when any unique/unduplicated barcode is found within a frame.
  ```js
  // Can I use? https://caniuse.com/?search=vibrate
  // A user gesture required. https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#chrome_enterprise_policies
  startVibrateButton.addEventListener('click', function() {
    scanner.bVibrateOnSuccessfulRead = true;
  });
  ```

<br />

### vibrateDuration

* vibrateDuration: *number = 300*

  Get or set how long (ms) the vibration lasts.
>
  *@see* [bVibrateOnSuccessfulRead](#bvibrateonsuccessfulread)

<br />

### getScanSettings

* getScanSettings&#40;&#41;: *Promise&lt;[ScanSettings](./interface/ScanSettings.md)&gt;*

  Get current scan settings.
  ```js
  let scanSettings = await scanner.getScanSettings();
  scanSettings.intervalTime = 50;
  scanSettings.duplicateForgetTime = 1000;
  await scanner.updateScanSettings(scanSettings);
  ```

<br />

### updateScanSettings

* updateScanSettings&#40;settings: *[ScanSettings](./interface/ScanSettings.md)*&#41;: *Promise&lt;void&gt;*

  Modify and update scan settings.
  ```js
  let scanSettings = await scanner.getScanSettings();
  scanSettings.intervalTime = 50;
  scanSettings.duplicateForgetTime = 1000;
  await scanner.updateScanSettings(scanSettings);
  ```

<br />


### openVideo

* openVideo&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

  Bind UI, open the camera, but not decode.
  ```js
  await scanner.setUIElement(document.getElementById("my-barcode-scanner"));
  await scanner.openVideo();
  console.log(await scanner.decodeCurrentFrame());
  ```

<br />

### showVideo

* showVideo&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

  Bind UI, open the camera, but not decode.
  ```js
  await scanner.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/dbr.scanner.html");
  await scanner.showVideo();
  console.log(await scanner.decodeCurrentFrame());
  ```

<br />

## Play and Pause

### onPlayed

* `event` onPlayed?: *&#40;info: [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&#41; => void*

  Triggered when the camera video stream is played.
  ```js
  scanner.onplayed = rsl=>{ console.log(rsl.width+'x'+rsl.height) };
  await scanner.show(); // or open, play, setCurrentCamera, like these.
  ```

<br />

### play

* play&#40;deviceId?: *string*, width?: *number*, height?: *number*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](../interface/ScannerPlayCallbackInfo.md)&gt;*

  Continue the video.
  ```js
  scanner.pause();
  \\*** a lot of work ***
  await scanner.play();
  ```

<br />

### pause

* pause&#40;&#41;: *void*

  Pause the video. Do not release the camera.

<br />

### stop

* stop&#40;&#41;: *void*

  Stop the video, and release the camera.

<br />

## UI

### defaultUIElementURL

* `static` defaultUIElementURL: *string*

  The url of the default scanner UI.
>
  Can only be changed before [createInstance](#createinstance).
>
  ```js
  Dynamsoft.DBR.BarcodeScanner.defaultUIElementURL = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/dbr.scanner.html";
  let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
  await scanner.show();
  ```

<br />

### regionMaskFillStyle

* regionMaskFillStyle: *string = "rgba(0,0,0,0.5)"*

  Set the style used when filling the mask beyond the region.

<br />

### regionMaskStrokeStyle

* regionMaskStrokeStyle: *string = "rgb(254,142,20)"*

  Set the style of the region border.

<br />

### regionMaskLineWidth

* regionMaskLineWidth: *number = 2*

  Set the style used when filling in located barcode.

<br />

### barcodeFillStyle

* barcodeFillStyle: *string = "rgba(254,180,32,0.3)"*

  Set the style used when filling in located barcode.

<br />

### barcodeStrokeStyle

* barcodeStrokeStyle: *string = "rgba(254,180,32,0.9)"*

  Set the style of the located barcode border.

<br />

### barcodeLineWidth

* barcodeLineWidth: *number = 1*

  Set the width of the located barcode border.

<br />

### getUIElement

* getUIElement&#40;&#41;: *HTMLElement*

  Get HTML element containing the [BarcodeScanner](#barcodescanner) instance.

<br />

### setUIElement

* setUIElement&#40;elementOrUrl: *HTMLElement &#124; string*&#41;: *Promise&lt;void&gt;*

  Set html element containing the `BarcodeScanner` instance.
  ```html
  <video class="dbrScanner-video" playsinline="true"></video>
  <script>
    let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
    await scanner.setUIElement(document.getElementsByClassName("dbrScanner-video")[0]);
    await scanner.open();
  </script>
  ```
  ```html
  <!-- <video class="dbrScanner-video" playsinline="true"></video> -->
  <script>
    let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
    await scanner.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/dbr.scanner.html");
    await scanner.show();
> </script>
> ```

<br />

## Camera Settings

### getAllCameras

* getAllCameras&#40;&#41;: *Promise&lt;[VideoDeviceInfo](./interface/VideoDeviceInfo.md)&#91;&#93;&gt;*

> Get infomation of all available cameras on the device.
> ```js
> let cameras = await scanner.getAllCameras();
> if(cameras.length){
>   await scanner.setCurrentCamera(cameras[0]);
> }
> ```

<br />

### getCurrentCamera

* getCurrentCamera&#40;&#41;: *Promise&lt;[VideoDeviceInfo](./interface/VideoDeviceInfo.md) &#124; null&gt;*

> Get information about the currently used camera.
> ```js
> let camera = await scanner.getCurrentCamera();
> ```

<br />

### setCurrentCamera

* setCurrentCamera&#40;cameraInfoOrDeviceId: *any*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

> Choose the camera and play it by its information or devide id.
> ```js
> let cameras = await scanner.getAllCameras();
> if(cameras.length){
>   await scanner.setCurrentCamera(cameras[0]);
> }
> ```

<br />

### getResolution

* getResolution&#40;&#41;: *number&#91;&#93;*

> Get current camera resolution.
> ```js
> let rsl = await scanner.getResolution();
> console.log(rsl.width + " x " + rsl.height);
> ```

<br />

### setResolution

* setResolution&#40;width: *number &#124; number&#91;&#93;*, height: *number*&#41;

> Set current camera resolution.
> ```js
> await scanner.setResolution(width, height);
> ```

<br />

### getVideoSettings

* getVideoSettings&#40;&#41;: *[MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints)*

> Get current video settings.

<br />

### updateVideoSettings

* updateVideoSettings&#40;[MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints): *any*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md) &#124; void&gt;*

> Modify and update video settings.
> ```js
> await scanner.updateVideoSettings({ video: {width: {ideal: 1280}, height: {ideal: 720}, facingMode: {ideal: 'environment'}} });
> ```

<br />

### getCapabilities

* getCapabilities&#40;&#41;: *[MediaTrackCapabilities](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/getCapabilities)*

> Get the camera capabilities. Chrome only.
> Only available when the scanner is open.
> ```console
> > scanner.getCapabilities()
> < {
>   "aspectRatio":{"max":3840,"min":0.000462962962962963},
>   "colorTemperature":{max: 7000, min: 2850, step: 50},
>   "deviceId":"1e...3af7",
>   "exposureCompensation": {max: 2.0000040531158447, min: -2.0000040531158447, step: 0.16666699945926666},
>   "exposureMode":["continuous","manual"],
>   "facingMode":["environment"],
>   "focusMode":["continuous","single-shot","manual"],
>   "frameRate":{"max":30,"min":0},
>   "groupId":"71...a935",
>   "height":{"max":2160,"min":1},
>   "resizeMode":["none","crop-and-scale"],
>   "torch":true,
>   "whiteBalanceMode":["continuous","manual"],
>   "width":{"max":3840,"min":1},
>   "zoom":{max: 606, min: 100, step: 2}
> }
> ```

<br />

### turnOnTorch

* turnOnTorch&#40;&#41;: *Promise&lt;void&gt;*

> Turn on the torch/flashlight. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.turnOnTorch();
> ```
> *@see* [turnOffTorch](#turnofftorch) [getCapabilities](#getcapabilities)

<br />

### turnOffTorch

* turnOffTorch&#40;&#41;: *Promise&lt;void&gt;*

> Turn off the torch. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.turnOffTorch();
> ```
> *@see* [turnOnTorch](#turnontorch) [getCapabilities](#getcapabilities)

<br />

### setColorTemperature

* setColorTemperature&#40;value: *number*&#41;: *Promise&lt;void&gt;*

> Adjusts the color temperature. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.setColorTemperature(5000);
> ```
> *@see* [getCapabilities](#getcapabilities)

<br />

### setExposureCompensation

* setExposureCompensation&#40;value: *number*&#41;: *Promise&lt;void&gt;*

> Adjusts the exposure level. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.setExposureCompensation(-0.7);
> ```
> *@see* [getCapabilities](#getcapabilities)

<br />

### setZoom

* setZoom&#40;value: *number*&#41;: *Promise&lt;void&gt;*

> Adjusts the zoom ratio. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.setZoom(400);
> ```
> *@see* [getCapabilities](#getcapabilities)

<br />

### setFrameRate

* setFrameRate&#40;value: *number*&#41;: *Promise&lt;void&gt;*

> Adjusts the frame rate. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.setFrameRate(10);
> ```
> *@see* [getCapabilities](#getcapabilities)

<br />

## Decoding Settings

### getRuntimeSettings

* getRuntimeSettings&#40;&#41;: *Promise&lt;[RuntimeSettings](./interface/RuntimeSettings.md)&gt;*

> Gets current runtime settings.
> ```js
> let settings = await scanner.getRuntimeSettings();
> settings.deblurLevel = 5;
> await scanner.updateRuntimeSettings(settings);
> ```

<br />



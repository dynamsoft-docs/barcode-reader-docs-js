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

The default built-in UI of each barcode scanner is defined in the file "dbr.scanner.html". If used directly, the UI will fit the entire page and sit on top. There are a few ways to customize it, read more on how to [Customize the UI](../user-guide/#customize-the-ui).

Although a barcode scanner is designed to scan barcodes from a video input, it also supports a special mode called [singleFrameMode](#singleFrameMode) which allows the user to select a still image or take a shot with the mobile camera for barcode scanning.

The `BarcodeScanner` is a child class of [BarcodeReader](./BarcodeReader.md) and inherits all its methods and properties which will not be covered in this article.

The following code snippet shows the basic usage of the `BarcodeScanner` class.

```js
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
scanner.onUnduplicatedRead = txt => console.log(txt);
await scanner.show();
```

<div class="doc-card-prefix"></div>

> ## Index
> 
> [**Create and Destroy Instances**](#create-and-destroy-instances)
> <hr>
> * [createInstance](#createinstance)
> * [destroy](#destroy)
> * [bDestroyed](#bdestroyed)
> 
> [**Decode Barcodes**](#decode-barcodes)
> <hr>
> * [onUnduplicatedRead](#onunduplicatedread)
> * [onFrameRead](#onframeread)
> * [decodeCurrentFrame](#decodecurrentframe)
> 
> [**UI Interaction**](#ui-interaction)
> <hr>
> * [show](#show)
> * [hide](#hide)
> * [pauseScan](#pausescan)
> * [resumeScan](#resumescan)
> 
> [**Scan Settings**](#scan-settings)
> <hr>
> * [bPlaySoundOnSuccessfulRead](#bplaysoundonsuccessfulread)
> * [soundOnSuccessfullRead](#soundonsuccessfullread)
> * [bVibrateOnSuccessfulRead](#bvibrateonsuccessfulread)
> * [vibrateDuration](#vibrateduration)
> * [singleFrameMode](#singleFrameMode)
> * [getScanSettings](#getscansettings)
> * [updateScanSettings](#updatescansettings)
> 
> [**UI Control**](#ui-control)
> <hr>
> * [getUIElement](#getuielement)
> * [setUIElement](#setuielement)
> * [defaultUIElementURL](#defaultuielementurl)
> * [barcodeFillStyle](#barcodefillstyle)
> * [barcodeLineWidth](#barcodelinewidth)
> * [barcodeStrokeStyle](#barcodestrokestyle)
> * [regionMaskFillStyle](#regionmaskfillstyle)
> * [regionMaskLineWidth](#regionmasklinewidth)
> * [regionMaskStrokeStyle](#regionmaskstrokestyle)
> 
> [**Camera Control**](#camera-control)
> <hr>
> * [getAllCameras](#getallcameras)
> * [getCurrentCamera](#getcurrentcamera)
> * [setCurrentCamera](#setcurrentcamera)
> * [getResolution](#getresolution)
> * [setResolution](#setresolution)
> * [getVideoSettings](#getvideosettings)
> * [updateVideoSettings](#updatevideosettings)
> * [openVideo](#openvideo)
> * [showVideo](#showvideo)
> * [play](#play)
> * [onPlayed](#onplayed)
> * [pause](#pause)
> * [stop](#stop)
> 
> [**Advanced Camera Control**](#advanced-camera-control)
> <hr>
> * [getCameraSettings](#getcamerasettings)
> * [getCapabilities](#getcapabilities)
> * [setFrameRate](#setframerate)
> * [setColorTemperature](#setcolortemperature)
> * [setExposureCompensation](#setexposurecompensation)
> * [setZoom](#setzoom)
> * [turnOnTorch](#turnontorch)
> * [turnOffTorch](#turnofftorch)

<div class="doc-card-prefix"></div>

> The following are inherited from the `BarcodeReader` Class.
> 
> [**Decode Barcodes**](./BarcodeReader.md#decode-barcodes)
> <hr>
> * [decode](./BarcodeReader.md#decode)
> * [decodeBase64String](./BarcodeReader.md#decodebase64string)
> * [decodeUrl](./BarcodeReader.md#decodeurl)
> * [decodeBuffer](./BarcodeReader.md#decodebuffer)
> 
> [**Change Settings**](./BarcodeReader.md#decoding-settings)
> <hr>
> * [getRuntimeSettings](./BarcodeReader.md#getruntimesettings)
> * [updateRuntimeSettings](./BarcodeReader.md#updateruntimesettings)
> * [resetRuntimeSettings](./BarcodeReader.md#resetruntimesettings)
> * [getModeArgument](./BarcodeReader.md#getmodeargument)
> * [setModeArgument](./BarcodeReader.md#setmodeargument)
> 
> [**Auxiliary**](./BarcodeReader.md#auxiliary)
> <hr>
> * [bSaveOriCanvas](./BarcodeReader.md#bsaveoricanvas)
> * [oriCanvas](./BarcodeReader.md#oricanvas)

## Create and Destroy Instances

<div class="doc-card-prefix"></div>

> ### createInstance
> <hr>
> `static` createInstance&#40;&#41;: *Promise&lt;[BarcodeScanner](#barcodescanner)&gt;*
> <hr>
> Creates a `BarcodeScanner` instance.
> #### Example
> ```js
> let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
> ```

<div class="doc-card-prefix"></div>

> ### destroy
> 
> <hr>
> destroy&#40;&#41;: *Promise&lt;void&gt;*
> <hr> 
> Destroys the `BarcodeScanner` instance. If your page needs to create a new instance from time to time, don't forget to destroy unused old instances.
> #### Example
> ```js
> let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
> // ... decode ...
> scanner.destroy();
> ```
  
<div class="doc-card-prefix"></div>

> ### bDestroyed
> <hr>
> bDestroyed: *boolean*
> <hr>
> Indicates whether the instance has been destroyed.

<div class="doc-card-prefix"></div>

## Decode Barcodes

<div class="doc-card-prefix"></div>

> ### onUnduplicatedRead
> <hr>
> `event` onUnduplicatedRead?: *&#40;txt: string, result: [TextResult](./interface/TextResult.md)&#41; => void*
> <hr>
> This event is triggered when a new, unduplicated barcode is found.
> 
> `txt` holds the barcode text string. `result` contains more detailed info.
> 
> The library keeps each barcode result (type and value) in the buffer for a period of time (can be set with [duplicateForgetTime](./interface/ScanSettings.md)) during which if a new result is an exact match, it's seen as a duplicate and will again be kept for that period of time while the old result is removed and so on.
> #### Example
> ```js
> scanner.onUnduplicatedRead = (txt, result) => {
>   alert(txt);
>   console.log(result);
> }
> ```

<div class="doc-card-prefix"></div>

> ### onFrameRead
> <hr>
> `event` onFrameRead?: *&#40;results: [TextResult](./interface/TextResult.md)&#91;&#93;&#41; => void*
> <hr>
> This event is triggered after the library finishes scanning a frame.
> 
> The `results` object contains all the barcode results in this frame.
> #### Example
> ```js
> scanner.onFrameRead = results => {
>   for(let result of results){
>     console.log(result.barcodeText);
>   }
> };
> ```

<div class="doc-card-prefix"></div>

> ### decodeCurrentFrame
> <hr>
> decodeCurrentFrame&#40;&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*
> <hr>
> Scans the current frame of the video for barcodes.
> #### Example
> ```js
> await scanner.showVideo();
> console.log(await scanner.decodeCurrentFrame());
> ```

## UI Interaction

<div class="doc-card-prefix"></div>

> ### show
> <hr>
> show&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*
> <hr>
> Binds and shows UI, opens the camera and starts decoding.
> #### Example
> ```js
> scanner.onUnduplicatedRead = (txt, result) => { 
>   alert(txt); console.log(result); };
> await scanner.show();
> ```

<div class="doc-card-prefix"></div>

> ### hide
> <hr>
> hide&#40;&#41;: *Promise&lt;void&gt;*
> <hr>
> Stops decoding, releases camera and unbinds UI.
> #### Example
> ```js
> await scanner.show();
> //...scan barcodes
> await scanner.hide();
> ```

<div class="doc-card-prefix"></div>

> ### pauseScan
> <hr>
> pauseScan&#40;&#41;: *void*
> <hr>
> Pauses the decoding process.

<div class="doc-card-prefix"></div>

> ### resumeScan
> <hr>
> resumeScan&#40;&#41;: *void*
> <hr>
> Resumes the decoding process.


## Scan Settings

<div class="doc-card-prefix"></div>

> ### bPlaySoundOnSuccessfulRead
> <hr>
> bPlaySoundOnSuccessfulRead: *(boolean &#124; string)*;
> <hr>
> Whether and when to play sound on barcode recognition (user input is required on iOS or [Chrome](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#chrome_enterprise_policies) for any sound to play). Allowed values are
> 
> - `false`: never play sound; <!--never-->
> - `true`: play sound when one or multiple barcodes are found on a frame; <!--always-->
> - `frame`: same as `true`;
> - `unduplicated`: play sound when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, play only once).
> #### Example
> ```js
> // A user gesture required. 
> startPlayButton.addEventListener('click', function() {
>   scanner.bPlaySoundOnSuccessfulRead = true;
> });
> ```

<div class="doc-card-prefix"></div>

> ### soundOnSuccessfullRead
> <hr>
> soundOnSuccessfullRead: [HTMLAudioElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLAudioElement)
> <hr>
> Specifies the sound to play on barcode recognition. If not specified, the default one is used.
> #### Example
> ```js
> scanner.soundOnSuccessfullRead = new Audio("./pi.mp3");
> ```

<div class="doc-card-prefix"></div>

> ### bVibrateOnSuccessfulRead
> <hr>
> bVibrateOnSuccessfulRead: *(boolean &#124; string) = false*
> <hr>
> Whether and when to vibrate on barcode recognition (user input is required on iOS or [Chrome](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#chrome_enterprise_policies) for the vibration). Allowed values are
> 
> - `false`: never vibrate; <!--never-->
> - `true`: vibrate when one or multiple barcodes are found on a frame; <!--always-->
> - `frame`: same as `true`;
> - `unduplicated`: vibrate when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, vibrate only once).
> #### Example
> ```js
> // Can I use? https://caniuse.com/?search=vibrate
> startVibrateButton.addEventListener('click', function() {
>   scanner.bVibrateOnSuccessfulRead = true;
> });
> ```

<div class="doc-card-prefix"></div>

> ### vibrateDuration
> <hr>
> vibrateDuration: *number = 300*
> <hr>
> Returns or sets how long (ms) the vibration lasts.
>
> *@see* [bVibrateOnSuccessfulRead](#bvibrateonsuccessfulread)

<div class="doc-card-prefix"></div>

> ### getScanSettings
> <hr>
> getScanSettings&#40;&#41;: *Promise&lt;[ScanSettings](./interface/ScanSettings.md)&gt;*
> <hr>
> Returns the current scan settings.
> #### Example
> ```js
> let scanSettings = await scanner.getScanSettings();
> scanSettings.intervalTime = 50;
> scanSettings.duplicateForgetTime = 1000;
> await scanner.updateScanSettings(scanSettings);
> ```
> *@see* [ScanSettings](./interface/ScanSettings.md)

<div class="doc-card-prefix"></div>

> ### updateScanSettings
> <hr>
> updateScanSettings&#40;settings: *[ScanSettings](./interface/ScanSettings.md)*&#41;: *Promise&lt;void&gt;*
> <hr>
> Changes scan settings with the struct passed in.
> #### Example
> ```js
> let scanSettings = await scanner.getScanSettings();
> scanSettings.intervalTime = 50;
> scanSettings.duplicateForgetTime = 1000;
> await scanner.updateScanSettings(scanSettings);
> ```

## UI Control

<div class="doc-card-prefix"></div>

> ### getUIElement
> <hr>
> getUIElement&#40;&#41;: *HTMLElement*
> <hr>
> Returns the HTML element that is used by the [BarcodeScanner](#barcodescanner) instance.

<div class="doc-card-prefix"></div>

### setUIElement
> <hr>
> setUIElement&#40;elementOrUrl: *HTMLElement &#124; string*&#41;: *Promise&lt;void&gt;*
> <hr>
> Specifies an HTML element for the [BarcodeScanner](#barcodescanner) instance to use as its UI. The structure inside the element determines the appearance of the UI. See more on [how to customize the UI](../user-guide/#customize-the-ui).
> #### Example
> ```html
> <!-- Define an element that shows only the video input -->
> <video class="dbrScanner-video" playsinline="true"></video>
> <script>
>   let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
>   await scanner.setUIElement(document.getElementsByClassName("dbrScanner-video")[0]);
>   await scanner.open();
> </script>
> ```
> 
> ```html
> <!-- Use the default official UI element definition -->
> <script>
>   let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
>   await scanner.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/dbr.scanner.html");
>   await scanner.show();
> </script>
> ```

<div class="doc-card-prefix"></div>

### defaultUIElementURL
> <hr>
> `static` defaultUIElementURL: *string*
> <hr>
> Returns or sets the URL of the *.html* file that defines the default UI Element.
>
> The URL is only effective when changed before the API [createInstance](#createinstance) is called.
> #### Example
> ```js
> Dynamsoft.DBR.BarcodeScanner.defaultUIElementURL = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/dbr.scanner.html";
> let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
> await scanner.show();
> ```

<div class="doc-card-prefix"></div>

### barcodeFillStyle
> <hr>
> barcodeFillStyle: *string*
> <hr>
> Specifies the color used inside the shape which highlights a found barcode. The default value is `rgba(254,180,32,0.3)`.

<div class="doc-card-prefix"></div>

### barcodeStrokeStyle
> <hr>
> barcodeStrokeStyle: *string*
> <hr>
> Specifies the color used to paint the outline of the shape which highlights a found barcode. The default value is `rgba(254,180,32,0.9)`.

<div class="doc-card-prefix"></div>

### barcodeLineWidth
> <hr>
> barcodeLineWidth: *number*
> <hr>
> Specifies the line width of the outline of the shape which highlights a found barcode. The default value is `1`.

<div class="doc-card-prefix"></div>

### regionMaskFillStyle
> <hr>
> regionMaskFillStyle: *string = "rgba(0,0,0,0.5)"*
> <hr>
> Sets the style used when filling the mask beyond the region.

<div class="doc-card-prefix"></div>

### regionMaskStrokeStyle
> <hr>
> regionMaskStrokeStyle: *string = "rgb(254,142,20)"*
> <hr>
> Sets the style of the region border.

<div class="doc-card-prefix"></div>

### regionMaskLineWidth
> <hr>
* regionMaskLineWidth: *number = 2*
> <hr>
  Sets the style used when filling in located barcode.


<div class="doc-card-prefix"></div>


> <hr>
> * [getUIElement](#getuielement)
> * [setUIElement](#setuielement)
> * [defaultUIElementURL](#defaultuielementurl)
> * [regionMaskFillStyle](#regionmaskfillstyle)
> * [regionMaskLineWidth](#regionmasklinewidth)
> * [regionMaskStrokeStyle](#regionmaskstrokestyle)
> * [barcodeFillStyle](#barcodefillstyle)
> * [barcodeLineWidth](#barcodelinewidth)
> * [barcodeStrokeStyle](#barcodestrokestyle)
> 


<div class="doc-card-prefix"></div>

> ### openVideo
> <hr>
> openVideo&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*
> <hr>
> Bind UI, open the camera, but not decode.
> #### Example
> ```js
> await scanner.setUIElement(document.getElementById("my-barcode-scanner"));
> await scanner.openVideo();
> console.log(await scanner.decodeCurrentFrame());
> ```

<div class="doc-card-prefix"></div>

### showVideo

* showVideo&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

  Bind UI, open the camera, but not decode.
  ```js
  await scanner.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/dbr.scanner.html");
  await scanner.showVideo();
  console.log(await scanner.decodeCurrentFrame());
  ```

<div class="doc-card-prefix"></div>

## Play and Pause

### onPlayed

* `event` onPlayed?: *&#40;info: [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&#41; => void*

  Triggered when the camera video stream is played.
  ```js
  scanner.onplayed = rsl=>{ console.log(rsl.width+'x'+rsl.height) };
  await scanner.show(); // or open, play, setCurrentCamera, like these.
  ```

<div class="doc-card-prefix"></div>

### play

* play&#40;deviceId?: *string*, width?: *number*, height?: *number*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](../interface/ScannerPlayCallbackInfo.md)&gt;*

  Continue the video.
  ```js
  scanner.pause();
  \\*** a lot of work ***
  await scanner.play();
  ```

<div class="doc-card-prefix"></div>

### pause

* pause&#40;&#41;: *void*

  Pause the video. Do not release the camera.

<div class="doc-card-prefix"></div>

### stop

* stop&#40;&#41;: *void*

  Stop the video, and release the camera.

<div class="doc-card-prefix"></div>

<div class="doc-card-prefix"></div>

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

<div class="doc-card-prefix"></div>

### getCurrentCamera

* getCurrentCamera&#40;&#41;: *Promise&lt;[VideoDeviceInfo](./interface/VideoDeviceInfo.md) &#124; null&gt;*

> Get information about the currently used camera.
> ```js
> let camera = await scanner.getCurrentCamera();
> ```

<div class="doc-card-prefix"></div>

### setCurrentCamera

* setCurrentCamera&#40;cameraInfoOrDeviceId: *any*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

> Choose the camera and play it by its information or devide id.
> ```js
> let cameras = await scanner.getAllCameras();
> if(cameras.length){
>   await scanner.setCurrentCamera(cameras[0]);
> }
> ```

<div class="doc-card-prefix"></div>

### getResolution

* getResolution&#40;&#41;: *number&#91;&#93;*

> Get current camera resolution.
> ```js
> let rsl = await scanner.getResolution();
> console.log(rsl.width + " x " + rsl.height);
> ```

<div class="doc-card-prefix"></div>

### setResolution

* setResolution&#40;width: *number &#124; number&#91;&#93;*, height: *number*&#41;

> Set current camera resolution.
> ```js
> await scanner.setResolution(width, height);
> ```

<div class="doc-card-prefix"></div>

### getVideoSettings

* getVideoSettings&#40;&#41;: *[MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints)*

> Get current video settings.

<div class="doc-card-prefix"></div>

### updateVideoSettings

* updateVideoSettings&#40;[MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints): *any*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md) &#124; void&gt;*

> Modify and update video settings.
> ```js
> await scanner.updateVideoSettings({ video: {width: {ideal: 1280}, height: {ideal: 720}, facingMode: {ideal: 'environment'}} });
> ```

<div class="doc-card-prefix"></div>

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

<div class="doc-card-prefix"></div>

### turnOnTorch

* turnOnTorch&#40;&#41;: *Promise&lt;void&gt;*

> Turn on the torch/flashlight. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.turnOnTorch();
> ```
> *@see* [turnOffTorch](#turnofftorch) [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

### turnOffTorch

* turnOffTorch&#40;&#41;: *Promise&lt;void&gt;*

> Turn off the torch. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.turnOffTorch();
> ```
> *@see* [turnOnTorch](#turnontorch) [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

### setColorTemperature

* setColorTemperature&#40;value: *number*&#41;: *Promise&lt;void&gt;*

> Adjusts the color temperature. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.setColorTemperature(5000);
> ```
> *@see* [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

### setExposureCompensation

* setExposureCompensation&#40;value: *number*&#41;: *Promise&lt;void&gt;*

> Adjusts the exposure level. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.setExposureCompensation(-0.7);
> ```
> *@see* [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

### setZoom

* setZoom&#40;value: *number*&#41;: *Promise&lt;void&gt;*

> Adjusts the zoom ratio. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.setZoom(400);
> ```
> *@see* [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

### setFrameRate

* setFrameRate&#40;value: *number*&#41;: *Promise&lt;void&gt;*

> Adjusts the frame rate. Chrome only.
> Only available when the scanner is open.
> Will reject if not support.
> ```js
> await scanner.setFrameRate(10);
> ```
> *@see* [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

## Decoding Settings

### getRuntimeSettings

* getRuntimeSettings&#40;&#41;: *Promise&lt;[RuntimeSettings](./interface/RuntimeSettings.md)&gt;*

> Gets current runtime settings.
> ```js
> let settings = await scanner.getRuntimeSettings();
> settings.deblurLevel = 5;
> await scanner.updateRuntimeSettings(settings);
> ```

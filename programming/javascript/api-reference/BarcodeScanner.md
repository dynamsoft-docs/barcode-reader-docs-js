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

## API Index

<div class="doc-card-prefix doc-card-list-prefix"></div>

> Create and Destroy Instances
> <hr>
> * [createInstance](#createinstance)
> * [destroy](#destroy)
> * [bDestroyed](#bdestroyed)
> 
> Decode Barcodes
> <hr>
> * [onUnduplicatedRead](#onunduplicatedread)
> * [onFrameRead](#onframeread)
> * [decodeCurrentFrame](#decodecurrentframe)
> 
> Basic Interaction
> <hr>
> * [show](#show)
> * [hide](#hide)
> * [pauseScan](#pausescan)
> * [resumeScan](#resumescan)
> 
> Scan Settings
> <hr>
> * [bPlaySoundOnSuccessfulRead](#bplaysoundonsuccessfulread)
> * [soundOnSuccessfullRead](#soundonsuccessfullread)
> * [bVibrateOnSuccessfulRead](#bvibrateonsuccessfulread)
> * [vibrateDuration](#vibrateduration)
> * [singleFrameMode](#singleFrameMode)
> * [getScanSettings](#getscansettings)
> * [updateScanSettings](#updatescansettings)
> 
> UI Control
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
> Camera Control
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
> Advanced Camera Control
> <hr>
> * [getCapabilities](#getcapabilities)
> * [getCameraSettings](#getcamerasettings)
> * [setFrameRate](#setframerate)
> * [setColorTemperature](#setcolortemperature)
> * [setExposureCompensation](#setexposurecompensation)
> * [setZoom](#setzoom)
> * [turnOnTorch](#turnontorch)
> * [turnOffTorch](#turnofftorch)

The following are inherited from the `BarcodeReader` Class.

<div class="doc-card-prefix doc-card-list-prefix"></div>

> Decode Barcodes
> <hr>
> * [decode](./BarcodeReader.md#decode)
> * [decodeBase64String](./BarcodeReader.md#decodebase64string)
> * [decodeUrl](./BarcodeReader.md#decodeurl)
> * [decodeBuffer](./BarcodeReader.md#decodebuffer)
> 
> Change Settings
> <hr>
> * [getRuntimeSettings](./BarcodeReader.md#getruntimesettings)
> * [updateRuntimeSettings](./BarcodeReader.md#updateruntimesettings)
> * [resetRuntimeSettings](./BarcodeReader.md#resetruntimesettings)
> * [getModeArgument](./BarcodeReader.md#getmodeargument)
> * [setModeArgument](./BarcodeReader.md#setmodeargument)
> 
> Auxiliary
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

## Basic Interaction

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
> - `false`: never play sound, the default value; <!--never-->
> - `true`: play sound when one or multiple barcodes are found on a frame; <!--always-->
> - `frame`: same as `true`;
> - `unduplicated`: play sound when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, play only once).
> 
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
> bVibrateOnSuccessfulRead: *(boolean &#124; string)*
> <hr>
> Whether and when to vibrate on barcode recognition (user input is required on iOS or [Chrome](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#chrome_enterprise_policies) for the vibration). Allowed values are
> 
> - `false`: never vibrate, the default value; <!--never-->
> - `true`: vibrate when one or multiple barcodes are found on a frame; <!--always-->
> - `frame`: same as `true`;
> - `unduplicated`: vibrate when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, vibrate only once).
> 
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
> vibrateDuration: *number*
> <hr>
> Returns or sets how long the vibration lastsin milliseconds. The default value is `300`.
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
> Changes scan settings with the object passed in.
> #### Parameters
> * **settings**: *[ScanSettings](./interface/ScanSettings.md)*
>    The object representing the new settings.
> 
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

> ### setUIElement
> <hr>
> setUIElement&#40;elementOrURL: *HTMLElement &#124; string*&#41;: *Promise&lt;void&gt;*
> <hr>
> Specifies an HTML element for the [BarcodeScanner](#barcodescanner) instance to use as its UI. The structure inside the element determines the appearance of the UI. See more on [how to customize the UI](../user-guide/#customize-the-ui).
> #### Parameters
> * **elementOrURL**: *HTMLElement &#124; string*
>    Specifies the UI Element either with an element on the page or the URL of an `.html` file which defines the element.
> 
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

> ### defaultUIElementURL
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

> ### barcodeFillStyle
> <hr>
> barcodeFillStyle: *string*
> <hr>
> Specifies the color used inside the shape which highlights a found barcode. The default value is `rgba(254,180,32,0.3)`.

<div class="doc-card-prefix"></div>

> ### barcodeStrokeStyle
> <hr>
> barcodeStrokeStyle: *string*
> <hr>
> Specifies the color used to paint the outline of the shape which highlights a found barcode. The default value is `rgba(254,180,32,0.9)`.

<div class="doc-card-prefix"></div>

> ### barcodeLineWidth
> <hr>
> barcodeLineWidth: *number*
> <hr>
> Specifies the line width of the outline of the shape which highlights a found barcode. The default value is `1`.

<div class="doc-card-prefix"></div>

> ### regionMaskFillStyle
> <hr>
> regionMaskFillStyle: *string*
> <hr>
> Specifies the color used in the square-loop shape between the actual scanning area and the boundary of the video input. This shape only appears when the barcode scanning is limited to a specified region. The default value is `rgba(0,0,0,0.5)`.
> *@see* [Read a specific area/region](../user-guide/advanced-usage.html#read-a-specific-arearegion)

<div class="doc-card-prefix"></div>

> ### regionMaskStrokeStyle
> <hr>
> regionMaskStrokeStyle: *string*
> <hr>
> Specifies the color used to paint the outline of the scanning region. This outline only appears when the barcode scanning is limited to a specified region. The default value is `rgb(254,142,20)`.
> *@see* [Read a specific area/region](../user-guide/advanced-usage.html#read-a-specific-arearegion)

<div class="doc-card-prefix"></div>

> ### regionMaskLineWidth
> <hr>
* regionMaskLineWidth: *number*
> <hr>
> Specifies the width of the outline of the scanning region. This outline only appears when the barcode scanning is limited to a specified region. The default value is `2`.
> *@see* [Read a specific area/region](../user-guide/advanced-usage.html#read-a-specific-arearegion)

## Camera Control

<div class="doc-card-prefix"></div>

> ### getAllCameras
> <hr>
> getAllCameras&#40;&#41;: *Promise&lt;[VideoDeviceInfo](./interface/VideoDeviceInfo.md)&#91;&#93;&gt;*
> <hr>
> Returns infomation of all available cameras on the device.
> #### Example
> ```js
> let cameras = await scanner.getAllCameras();
> if(cameras.length){
>   await scanner.setCurrentCamera(cameras[0]);
> }
> ```

<div class="doc-card-prefix"></div>

> ### getCurrentCamera
> <hr>
> getCurrentCamera&#40;&#41;: *Promise&lt;[VideoDeviceInfo](./interface/VideoDeviceInfo.md) &#124; null&gt;*
> <hr>
> Returns information about the current camera.
> #### Example
> ```js
> let camera = await scanner.getCurrentCamera();
> ```

<div class="doc-card-prefix"></div>

> ### setCurrentCamera
> <hr>
> setCurrentCamera&#40;deviceID: *string*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*
> <hr>
> Chooses a camera as the video source.
> #### Parameters
> * **deviceID**
>    Specifies the camera with its device ID.
> 
> #### Example
> ```js
> let cameras = await scanner.getAllCameras();
> if(cameras.length){
>   await scanner.setCurrentCamera(cameras[0]);
> }
> ```

<div class="doc-card-prefix"></div>

> ### getResolution
> <hr>
> getResolution&#40;&#41;: *number&#91;&#93;*
> <hr>
> Returns the resolution of the current video input.
> #### Example
> ```js
> let rsl = await scanner.getResolution();
> console.log(rsl.width + " x " + rsl.height);
> ```

<div class="doc-card-prefix"></div>

> ### setResolution
> <hr>
> setResolution&#40;width: *number*, height: *number*&#41;
> <hr>
> Sets the resolution of the current video input. If the specified resolution is not exactly supported, the closest resolution will be applied.
> #### Example
> ```js
> await scanner.setResolution(width, height);
> ```

<div class="doc-card-prefix"></div>

> ### getVideoSettings
> <hr>
> getVideoSettings&#40;&#41;: *[MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints)*
> <hr>
> Returns the current video settings.

<div class="doc-card-prefix"></div>

> ### updateVideoSettings
> <hr>
> updateVideoSettings&#40;constraints:*[MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints)*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md) &#124; void&gt;*
> <hr>
> Changes the video input.
> #### Parameters
> * **constraints**
>    A `MediaStreamConstraints` object specifying the requirements for the video input.
> 
> #### Example
> ```js
> await scanner.updateVideoSettings({ video: {width: {ideal: 1280}, height: {ideal: 720}, facingMode: {ideal: 'environment'}} });
> ```

<div class="doc-card-prefix"></div>

> ### openVideo
> <hr>
> openVideo&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*
> <hr>
> Binds UI and opens the camera to show the video stream.
> #### Example
> ```js
> await scanner.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/dbr.scanner.html");
> await scanner.openVideo(); // The video will start playing but it may not be visible on the page
> console.log(await scanner.decodeCurrentFrame());
> ```

<div class="doc-card-prefix"></div>

> ### showVideo
> <hr>
> showVideo&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*
> <hr>
> Similar to [openVideo](#openvideo) but will also show the UI Element if it is hidden.
> #### Example
> ```js
> await scanner.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.5/dist/dbr.scanner.html");
> await scanner.showVideo(); // The video will start playing and show up on the page
> console.log(await scanner.decodeCurrentFrame());
> ```

<div class="doc-card-prefix"></div>

> ### play
> <hr>
> play&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](../interface/ScannerPlayCallbackInfo.md)&gt;*
> <hr>
> Play the video if it is already open but paused or stopped. If the video is already playing, it will start again.
> #### Example
> ```js
> scanner.pause();
> //..doing other things without the video
> await scanner.play();
> ```

<div class="doc-card-prefix"></div>

> ### onPlayed
> <hr>
> `event` onPlayed?: *&#40;info: [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&#41; => void*
> <hr>
> This event is triggered when the video stream starts playing.
> #### Example
> ```js
> scanner.onplayed = rsl=>{ console.log(rsl.width+'x'+rsl.height) };
> await scanner.show(); // or open(), play(), setCurrentCamera(), etc.
> ```

<div class="doc-card-prefix"></div>

> ### pause
> <hr>
> pause&#40;&#41;: *void*
> <hr>
> Pauses the video without releasing the camera.

<div class="doc-card-prefix"></div>

> ### stop
> <hr>
> stop&#40;&#41;: *void*
> <hr>
> Stops the video and releases the camera.

## Advanced Camera Control

<div class="doc-card-prefix"></div>

> ### getCapabilities
> <hr>
> getCapabilities&#40;&#41;: *[MediaTrackCapabilities](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/getCapabilities)*
> <hr>
> Returns a `MediaTrackCapabilities` object which specifies the values or range of values for each constrainable property of the current camera. 
> 
> Right now, this method only works in Chrome and should be called when the scanner is open.
> #### Example
> ```js
> scanner.getCapabilities();
> /* Result sample
> {
>   aspectRatio: {max: 1280, min: 0.001388888888888889},
>   brightness: {max: 64, min: -64, step: 1},
>   colorTemperature: {max: 6500, min: 2800, step: 10},
>   contrast: {max: 95, min: 0, step: 1},
>   deviceId: "3a505c29a3312600ea0afd79f8e2b4ba4fba3e539257801ff1de8718c27f2bed",
>   exposureMode: ["continuous", "manual"],
>   exposureTime: {max: 10000, min: 39.0625, step: 39.0625},
>   facingMode: [],
>   focusDistance: {max: 1024, min: 0, step: 10},
>   focusMode: ["continuous", "manual"],
>   frameRate: {max: 30, min: 0},
>   groupId: "35a82dcb7d5b0ef5bda550718d194f04a812c976175e926ccb81fb9d235d010f",
>   height: {max: 720, min: 1},
>   resizeMode: ["none", "crop-and-scale"],
>   saturation: {max: 100, min: 0, step: 1},
>   sharpness: {max: 7, min: 1, step: 1},
>   whiteBalanceMode: ["continuous", "manual"],
>   width: {max: 1280, min: 1}
> }
> */
> ```

<div class="doc-card-prefix"></div>

> ### getCameraSettings
> <hr>
> getCameraSettings&#40;&#41;: *any*
> <hr>
> Returns the current values for each constrainable property of the current camera.
> 
> Right now, this method only works in Chrome and should be called when the scanner is open.
> #### Example
> ```js
> scanner.getCameraSettings();
> /* Result sample
> {
>   aspectRatio: 1.3333333333333333,
>   brightness: 0,
>   colorTemperature: 4600,
>   contrast: 0,
>   deviceId: "3a505c29a3312600ea0afd79f8e2b4ba4fba3e539257801ff1de8718c27f2bed",
>   exposureMode: "continuous",
>   exposureTime: 156.25,
>   focusDistance: 120,
>   focusMode: "continuous",
>   frameRate: 30,
>   groupId: "35a82dcb7d5b0ef5bda550718d194f04a812c976175e926ccb81fb9d235d010f",
>   height: 480,
>   resizeMode: "none",
>   saturation: 73,
>   sharpness: 2,
>   whiteBalanceMode: "continuous",
>   width: 640
> }
> */
> ```
> *@see* [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

> ### setFrameRate
> <hr>
> setFrameRate&#40;rate: *number*&#41;: *Promise&lt;void&gt;*
> <hr>
> Adjusts the frame rate.
> 
> Right now, this method only works in Chrome and should be called when the scanner is open.
> #### Parameters
> * rate
>    Specifies the frame rate.
> 
> #### Example
> ```js
> await scanner.setFrameRate(10);
> ```
> *@see* [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

> ### setColorTemperature
> <hr>
> setColorTemperature&#40;colorTemperatur: *number*&#41;: *Promise&lt;void&gt;*
> <hr>
> Adjusts the color temperature.
> 
> Right now, this method only works in Chrome and should be called when the scanner is open.
> #### Parameters
> * colorTemperatur
>    Specifies the color temperatur.
> 
> #### Example
> ```js
> await scanner.setColorTemperature(5000);
> ```
> *@see* [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

> ### setExposureCompensation
> <hr>
> setExposureCompensation&#40;exposureCompensation: *number*&#41;: *Promise&lt;void&gt;*
> <hr>
> Adjusts the exposure level.
> 
> Right now, this method only works in Chrome and should be called when the scanner is open.
> #### Parameters
> * exposureCompensation
>    Specifies the exposure compensation.
> 
> #### Example
> ```js
> await scanner.setExposureCompensation(-0.7);
> ```
> *@see* [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

> ### setZoom
> <hr>
> setZoom&#40;zoomLevel: *number*&#41;: *Promise&lt;void&gt;*
> <hr>
> Adjusts the video zoom.
> 
> Right now, this method only works in Chrome and should be called when the scanner is open.
> #### Parameters
> * zoomLevel
>    Specifies the zoom level.
> 
> #### Example
> ```js
> await scanner.setZoom(400);
> ```
> *@see* [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

> ### turnOnTorch
> <hr>
> turnOnTorch&#40;&#41;: *Promise&lt;void&gt;*
> <hr>
> Turns on the torch/flashlight.
>
> Right now, this method only works in Chrome and should be called when the scanner is open.
> #### Example
> ```js
> await scanner.turnOnTorch();
> ```
> *@see* [turnOffTorch](#turnofftorch), [getCapabilities](#getcapabilities)

<div class="doc-card-prefix"></div>

> ### turnOffTorch
> <hr>
> turnOffTorch&#40;&#41;: *Promise&lt;void&gt;*
> <hr>
> Turns off the torch/flashlight.
>
> Right now, this method only works in Chrome and should be called when the scanner is open.
> #### Example
> ```js
> await scanner.turnOffTorch();
> ```
> *@see* [turnOnTorch](#turnontorch) [getCapabilities](#getcapabilities)

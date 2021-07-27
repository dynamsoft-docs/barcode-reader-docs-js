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

# BarcodeScanner for Video

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

<br /><br />

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

<br /><br />

## Create and Destroy Instances

<br />  

### createInstance

Creates a `BarcodeScanner` instance.

**Syntax**

`static` createInstance&#40;&#41;: *Promise&lt;[BarcodeScanner](#barcodescanner)&gt;*

**Parameters**

None.

**Return value**

A promise resolving to the created `BarcodeScanner` object.

**Code Snippet**

```js
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
```

<br /><br />

### destroy

Destroys the `BarcodeScanner` instance. If your page needs to create a new instance from time to time, don't forget to destroy unused old instances.

**Syntax**

destroy&#40;&#41;: *Promise&lt;void&gt;*

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
// ... decode ...
scanner.destroy();
```
  
<br /><br />

### bDestroyed

Indicates whether the instance has been destroyed.

**Syntax**

bDestroyed: *boolean*

<br /><br />

## Decode Barcodes

<br />

### onUnduplicatedRead

This event is triggered when a new, unduplicated barcode is found.

The library keeps each barcode result (type and value) in the buffer for a period of time (can be set with [duplicateForgetTime](./interface/ScanSettings.md)) during which if a new result is an exact match, it's seen as a duplicate and will again be kept for that period of time while the old result is removed and so on.

**Syntax**

`event` onUnduplicatedRead?: *&#40;txt: string, result: [TextResult](./interface/TextResult.md)&#41; => void*

**Arguments**

`txt`: a string that holds the barcode text. 

`result`: a `TextResult` object that contains more detailed info.

**Code Snippet**

```js
scanner.onUnduplicatedRead = (txt, result) ={
  alert(txt);
  console.log(result);
}
```

<br /><br />

### onFrameRead

This event is triggered after the library finishes scanning a frame.

**Syntax**

`event` onFrameRead?: *&#40;results: [TextResult](./interface/TextResult.md)&#91;&#93;&#41; =void*

**Arguments**

`results`: a `TextResult` object that contains all the barcode results in this frame.

**Code Snippet**

```js
scanner.onFrameRead = results => {
  for(let result of results){
    console.log(result.barcodeText);
  }
};
```

<br /><br />

### decodeCurrentFrame

Scans the current frame of the video for barcodes.

**Syntax**

decodeCurrentFrame&#40;&#41;: *Promise&lt;[TextResult](./interface/TextResult.md)&#91;&#93;&gt;*

**Parameters**

None.

**Return value**

A promise resolving to a `TextResult` object that contains all the barcode results found in this frame.

**Code Snippet**
```js
await scanner.showVideo();
console.log(await scanner.decodeCurrentFrame());
```

## Basic Interaction

<br />

### show

Binds and shows UI, opens the camera and starts decoding.

**Syntax**

show&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

**Parameters**

None.

**Return value**

A promise resolving to a `ScannerPlayCallbackInfo` object.

**Code Snippet**
```js
scanner.onUnduplicatedRead = (txt, result) => { 
  alert(txt); console.log(result); };
await scanner.show();
```

<br /><br />

### hide

Stops decoding, releases camera and unbinds UI.

**Syntax**

hide&#40;&#41;: *Promise&lt;void&gt;*

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**
```js
await scanner.show();
//...scan barcodes
await scanner.hide();
```

<br /><br />

### pauseScan

Pauses the decoding process.

**Syntax**

pauseScan&#40;&#41;: *void*

**Parameters**

None.

**Return value**

None.


<br /><br />

### resumeScan

Resumes the decoding process.

**Syntax**

resumeScan&#40;&#41;: *void*

**Parameters**

None.

**Return value**

None.

## Scan Settings

<br />

### bPlaySoundOnSuccessfulRead

Whether and when to play sound on barcode recognition (user input is required on iOS or [Chrome](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#chrome_enterprise_policies) for any sound to play). Allowed values are

- `false`: never play sound, the default value; <!--never-->
- `true`: play sound when one or multiple barcodes are found on a frame; <!--always-->
- `frame`: same as `true`;
- `unduplicated`: play sound when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, play only once).

**Syntax**

bPlaySoundOnSuccessfulRead: *(boolean &#124; string)*;

**Code Snippet**
```js
// A user gesture required. 
startPlayButton.addEventListener('click', function() {
  scanner.bPlaySoundOnSuccessfulRead = true;
});
```

<br /><br />

### soundOnSuccessfullRead

Specifies the sound to play on barcode recognition. If not specified, the default one is used.

**Syntax**

soundOnSuccessfullRead: [HTMLAudioElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLAudioElement)

**Code Snippet**
```js
scanner.soundOnSuccessfullRead = new Audio("./pi.mp3");
```

<br /><br />

### bVibrateOnSuccessfulRead

Whether and when to vibrate on barcode recognition (user input is required on iOS or [Chrome](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#chrome_enterprise_policies) for the vibration). Allowed values are

- `false`: never vibrate, the default value; <!--never-->
- `true`: vibrate when one or multiple barcodes are found on a frame; <!--always-->
- `frame`: same as `true`;
- `unduplicated`: vibrate when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, vibrate only once).

**Syntax**

bVibrateOnSuccessfulRead: *(boolean &#124; string)*

**Code Snippet**
```js
// Can I use? https://caniuse.com/?search=vibrate
startVibrateButton.addEventListener('click', function() {
  scanner.bVibrateOnSuccessfulRead = true;
});
```

<br /><br />

### vibrateDuration

Returns or sets how long the vibration lastsin milliseconds. The default value is `300`.

**Syntax**

vibrateDuration: *number*
<hr>

**See also** 

[bVibrateOnSuccessfulRead](#bvibrateonsuccessfulread)

<br /><br />

### getScanSettings

Returns the current scan settings.

**Syntax**

getScanSettings&#40;&#41;: *Promise&lt;[ScanSettings](./interface/ScanSettings.md)&gt;*

**Parameters**

None.

**Return value**

A promise resolving to a `ScanSettings`.

**Code Snippet**

```js
let scanSettings = await scanner.getScanSettings();
scanSettings.intervalTime = 50;
scanSettings.duplicateForgetTime = 1000;
await scanner.updateScanSettings(scanSettings);
```

**See also**

[ScanSettings](./interface/ScanSettings.md)

<br /><br />

### updateScanSettings

Changes scan settings with the object passed in.

**Syntax**

updateScanSettings&#40;settings: *[ScanSettings](./interface/ScanSettings.md)*&#41;: *Promise&lt;void&gt;*

**Parameters**

`settings`: specifies the new scan settings.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
let scanSettings = await scanner.getScanSettings();
scanSettings.intervalTime = 50;
scanSettings.duplicateForgetTime = 1000;
await scanner.updateScanSettings(scanSettings);
```

## UI Control

<br />

### getUIElement

Returns the HTML element that is used by the [BarcodeScanner](#barcodescanner) instance.

**Syntax**

getUIElement&#40;&#41;: *HTMLElement*

<br /><br />

### setUIElement

Specifies an HTML element for the [BarcodeScanner](#barcodescanner) instance to use as its UI. The structure inside the element determines the appearance of the UI. See more on [how to customize the UI](../user-guide/#customize-the-ui).

**Syntax**

setUIElement&#40;elementOrURL: *HTMLElement &#124; string*&#41;: *Promise&lt;void&gt;*

**Parameters**

`elementOrURL`: specifies the element.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**
```html
<!-- Define an element that shows only the video input -->
<video class="dbrScanner-video" playsinline="true"></video>
<script>
  let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
  await scanner.setUIElement(document.getElementsByClassName("dbrScanner-video")[0]);
  await scanner.open();
</script>
```

```html
<!-- Use the default official UI element definition -->
<script>
  let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
  await scanner.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.4.0/dist/dbr.scanner.html");
  await scanner.show();
</script>
```

<br /><br />

### defaultUIElementURL

Returns or sets the URL of the *.html* file that defines the default UI Element. The URL can only be set before the API [createInstance](#createinstance) is called.

**Syntax**

`static` defaultUIElementURL: *string*

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeScanner.defaultUIElementURL = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.4.0/dist/dbr.scanner.html";
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
await scanner.show();
```

<br /><br />

### barcodeFillStyle

Specifies the color used inside the shape which highlights a found barcode. The default value is `rgba(254,180,32,0.3)`.

**Syntax**

barcodeFillStyle: *string*

<br /><br />

### barcodeStrokeStyle

Specifies the color used to paint the outline of the shape which highlights a found barcode. The default value is `rgba(254,180,32,0.9)`.

**Syntax**

barcodeStrokeStyle: *string*

<br /><br />

### barcodeLineWidth

Specifies the line width of the outline of the shape which highlights a found barcode. The default value is `1`.

**Syntax**

barcodeLineWidth: *number*

<br /><br />

### regionMaskFillStyle

Specifies the color used in the square-loop shape between the actual scanning area and the boundary of the video input. This shape only appears when the barcode scanning is limited to a specified region. The default value is `rgba(0,0,0,0.5)`.

**Syntax**

regionMaskFillStyle: *string*

**See also**

[Read a specific area/region](../user-guide/advanced-usage.html#read-a-specific-arearegion)

<br /><br />

### regionMaskStrokeStyle

Specifies the color used to paint the outline of the scanning region. This outline only appears when the barcode scanning is limited to a specified region. The default value is `rgb(254,142,20)`.

**Syntax**

regionMaskStrokeStyle: *string*

**See also**

[Read a specific area/region](../user-guide/advanced-usage.html#read-a-specific-arearegion)

<br /><br />

### regionMaskLineWidth

Specifies the width of the outline of the scanning region. This outline only appears when the barcode scanning is limited to a specified region. The default value is `2`.

**Syntax**

* regionMaskLineWidth: *number*

**See also**

[Read a specific area/region](../user-guide/advanced-usage.html#read-a-specific-arearegion)

## Camera Control

<br />

### getAllCameras

Returns infomation of all available cameras on the device.

**Syntax**

getAllCameras&#40;&#41;: *Promise&lt;[VideoDeviceInfo](./interface/VideoDeviceInfo.md)&#91;&#93;&gt;*

**Parameters**

None.

**Return value**

A promise resolving to an array of `VideoDeviceInfo` objects.

**Code Snippet**

```js
let cameras = await scanner.getAllCameras();
if(cameras.length){
  await scanner.setCurrentCamera(cameras[0]);
}
```

<br /><br />

### getCurrentCamera

Returns information about the current camera.

**Syntax**

getCurrentCamera&#40;&#41;: *Promise&lt;[VideoDeviceInfo](./interface/VideoDeviceInfo.md) &#124; null&gt;*

**Parameters**

None.

**Return value**

A promise resolving to a `VideoDeviceInfo` object.

**Code Snippet**

```js
let camera = await scanner.getCurrentCamera();
```

<br /><br />

### setCurrentCamera

Chooses a camera as the video source.

**Syntax**

setCurrentCamera&#40;deviceID: *string*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

**Parameters**

`deviceID`: specifies the camera.

**Return value**

A promise resolving to a `ScannerPlayCallbackInfo` object.

**Code Snippet**

```js
let cameras = await scanner.getAllCameras();
if(cameras.length){
  await scanner.setCurrentCamera(cameras[0]);
}
```

<br /><br />

### getResolution

Returns the resolution of the current video input.

**Syntax**

getResolution&#40;&#41;: *number&#91;&#93;*

**Parameters**

None.

**Return value**

An array of two numbers representing the resolution.

**Code Snippet**

```js
let rsl = await scanner.getResolution();
console.log(rsl.width + " x " + rsl.height);
```

<br /><br />

### setResolution

Sets the resolution of the current video input. If the specified resolution is not exactly supported, the closest resolution will be applied.

**Syntax**

setResolution&#40;width: *number*, height: *number*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

**Parameters**

`width`: specifies the horizontal resolution.
`height`: specifies the vertical resolution.

**Return value**

A promise resolving to a `ScannerPlayCallbackInfo` object.

**Code Snippet**

```js
await scanner.setResolution(width, height);
```

<br /><br />

### getVideoSettings

Returns the current video settings.

**Syntax**

getVideoSettings&#40;&#41;: *[MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints)*

**Parameters**

None.

**Return value**

A `MediaStreamConstraints` object.

<br /><br />

### updateVideoSettings

Changes the video input.

**Syntax**

updateVideoSettings&#40;constraints:*[MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints)*&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md) &#124; void&gt;*

**Parameters**

`constraints`: specifies the new video settings.

**Return value**

A promise resolving to a `ScannerPlayCallbackInfo` object.

**Code Snippet**

```js
await scanner.updateVideoSettings({ video: {width: {ideal: 1280}, height: {ideal: 720}, facingMode: {ideal: 'environment'}} });
```

<br /><br />

### openVideo

Binds UI and opens the camera to show the video stream.

**Syntax**

openVideo&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

**Parameters**

None.

**Return value**

A promise resolving to a `ScannerPlayCallbackInfo` object.

**Code Snippet**

```js
await scanner.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.4.0/dist/dbr.scanner.html");
await scanner.openVideo(); // The video will start playing but it may not be visible on the page
console.log(await scanner.decodeCurrentFrame());
```

<br /><br />

### showVideo

Similar to [openVideo](#openvideo) but will also show the UI Element if it is hidden.

**Syntax**

showVideo&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&gt;*

**Parameters**

None.

**Return value**

A promise resolving to a `ScannerPlayCallbackInfo` object.

**Code Snippet**

```js
await scanner.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.4.0/dist/dbr.scanner.html");
await scanner.showVideo(); // The video will start playing and show up on the page
console.log(await scanner.decodeCurrentFrame());
```

<br /><br />

### play

Play the video if it is already open but paused or stopped. If the video is already playing, it will start again.

**Syntax**

play&#40;&#41;: *Promise&lt;[ScannerPlayCallbackInfo](../interface/ScannerPlayCallbackInfo.md)&gt;*

**Parameters**

None.

**Return value**

A promise resolving to a `ScannerPlayCallbackInfo` object.

**Code Snippet**

```js
scanner.pause();
//..doing other things without the video
await scanner.play();
```

<br /><br />

### onPlayed

This event is triggered when the video stream starts playing.

**Syntax**

`event` onPlayed?: *&#40;info: [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)&#41; => void*

**Arguments**

info: a `ScannerPlayCallbackInfo` object which describes the resolution of the video input.


**Code Snippet**

```js
scanner.onplayed = rsl=>{ console.log(rsl.width+'x'+rsl.height) };
await scanner.show(); // or open(), play(), setCurrentCamera(), etc.
```

<br /><br />

### pause

Pauses the video without releasing the camera.

**Syntax**

pause&#40;&#41;: *void*

**Parameters**

None.

**Return value**

None.

<br /><br />

### stop

Stops the video and releases the camera.

**Syntax**

stop&#40;&#41;: *void*

**Parameters**

None.

**Return value**

None.

## Advanced Camera Control

<br />

### getCapabilities

Inspects and returns the capabilities of the current camera.

Right now, this method only works in Chrome and should be called when the scanner is open.

**Syntax**

getCapabilities&#40;&#41;: *[MediaTrackCapabilities](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/getCapabilities)*

**Parameters**

None.

**Return value**

A `MediaTrackCapabilities` object which specifies the values or range of values for each constrainable property of the current camera.

**Code Snippet**

```js
scanner.getCapabilities();
/* Result sample
{
  aspectRatio: {max: 1280, min: 0.001388888888888889},
  brightness: {max: 64, min: -64, step: 1},
  colorTemperature: {max: 6500, min: 2800, step: 10},
  contrast: {max: 95, min: 0, step: 1},
  deviceId: "3a505c29a3312600ea0afd79f8e2b4ba4fba3e539257801ff1de8718c27f2bed",
  exposureMode: ["continuous", "manual"],
  exposureTime: {max: 10000, min: 39.0625, step: 39.0625},
  facingMode: [],
  focusDistance: {max: 1024, min: 0, step: 10},
  focusMode: ["continuous", "manual"],
  frameRate: {max: 30, min: 0},
  groupId: "35a82dcb7d5b0ef5bda550718d194f04a812c976175e926ccb81fb9d235d010f",
  height: {max: 720, min: 1},
  resizeMode: ["none", "crop-and-scale"],
  saturation: {max: 100, min: 0, step: 1},
  sharpness: {max: 7, min: 1, step: 1},
  whiteBalanceMode: ["continuous", "manual"],
  width: {max: 1280, min: 1}
}
*/
```

<br /><br />

### getCameraSettings

Returns the current values for each constrainable property of the current camera.

Right now, this method only works in Chrome and should be called when the scanner is open.

**Syntax**

getCameraSettings&#40;&#41;: *any*

**Parameters**

None.

**Return value**

The current values for each constrainable property of the current camera

**Code Snippet**

```js
scanner.getCameraSettings();
/* Result sample
{
  aspectRatio: 1.3333333333333333,
  brightness: 0,
  colorTemperature: 4600,
  contrast: 0,
  deviceId: "3a505c29a3312600ea0afd79f8e2b4ba4fba3e539257801ff1de8718c27f2bed",
  exposureMode: "continuous",
  exposureTime: 156.25,
  focusDistance: 120,
  focusMode: "continuous",
  frameRate: 30,
  groupId: "35a82dcb7d5b0ef5bda550718d194f04a812c976175e926ccb81fb9d235d010f",
  height: 480,
  resizeMode: "none",
  saturation: 73,
  sharpness: 2,
  whiteBalanceMode: "continuous",
  width: 640
}
*/
```

**See also**

[getCapabilities](#getcapabilities)

<br /><br />

### setFrameRate

Adjusts the frame rate.

Right now, this method only works in Chrome and should be called when the scanner is open.

**Syntax**

setFrameRate&#40;rate: *number*&#41;: *Promise&lt;void&gt;*

**Parameters**

`rate`: specifies the new frame rate.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.setFrameRate(10);
```

**See also**

[getCapabilities](#getcapabilities)

<br /><br />

### setColorTemperature

Adjusts the color temperature.

Right now, this method only works in Chrome and should be called when the scanner is open.

**Syntax**

setColorTemperature&#40;colorTemperatur: *number*&#41;: *Promise&lt;void&gt;*

**Parameters**

`colorTemperatur`: specifies the new color temperature.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.setColorTemperature(5000);
```

**See also**

[getCapabilities](#getcapabilities)

<br /><br />

### setExposureCompensation

Sets the exposure compensation index.

Right now, this method only works in Chrome and should be called when the scanner is open.

**Syntax**

setExposureCompensation&#40;exposureCompensation: *number*&#41;: *Promise&lt;void&gt;*

**Parameters**

`exposureCompensation`: specifies the new exposure compensation index.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.setExposureCompensation(-0.7);
```

**See also**

[getCapabilities](#getcapabilities)

<br /><br />

### setZoom

Sets current zoom value. 

**Syntax**

setZoom&#40;zoomValue: *number*&#41;: *Promise&lt;void&gt;*

**Parameters**

`zoomValue`: specifies the new zoom value.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.setZoom(400);
```

**See also**

[getCapabilities](#getcapabilities)

<br /><br />

### turnOnTorch

Turns on the torch/flashlight.

Right now, this method only works in Chrome and should be called when the scanner is open.

**Syntax**

turnOnTorch&#40;&#41;: *Promise&lt;void&gt;*

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.turnOnTorch();
```

**See also**

[turnOffTorch](#turnofftorch)
[getCapabilities](#getcapabilities)

<br /><br />

### turnOffTorch

Turns off the torch/flashlight.

Right now, this method only works in Chrome and should be called when the scanner is open.

**Syntax**

turnOffTorch&#40;&#41;: *Promise&lt;void&gt;*

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.turnOffTorch();
```

**See also**

[turnOnTorch](#turnontorch)
[getCapabilities](#getcapabilities)

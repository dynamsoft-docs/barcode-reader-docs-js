---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - v8.4.0 BarcodeScanner
description: This page shows the BarcodeScanner class of Dynamsoft Barcode Reader JavaScript SDK.
keywords: BarcodeScanner, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: BarcodeScanner
permalink: /programming/javascript/api-reference/BarcodeScanner-v8.4.0.html
---

# BarcodeScanner for Video

A barcode scanner object gets access to a camera via the [MediaDevices](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices) interface, then uses its built-in UI to show the camera input and perform continuous barcode scanning on the incoming frames.

The default built-in UI of each barcode scanner is defined in the file "dbr.scanner.html". If used directly, the UI will fit the entire page and sit on top. There are a few ways to customize it, read more on how to [Customize the UI](../user-guide/#customize-the-ui).

Although a barcode scanner is designed to scan barcodes from a video input, it also supports a special mode called [singleFrameMode](#singleframemode) which allows the user to select a still image or take a shot with the mobile camera for barcode scanning.

The `BarcodeScanner` is a child class of [BarcodeReader](./BarcodeReader.md) and inherits all its methods and properties which will not be covered in this article.

The following code snippet shows the basic usage of the `BarcodeScanner` class.

```js
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
scanner.onUnduplicatedRead = txt => console.log(txt);
await scanner.show();
```



## API Index

### Create and Destroy Instances

| API Name | Description |
|---|---|
| [createInstance](#createinstance) | Creates a `BarcodeScanner` instance. |
| [destroy](#destroy) | Destroys the `BarcodeScanner` instance. |
| [bDestroyed](#bdestroyed) | Indicates whether the instance has been destroyed. |

### Decode Barcodes

| API Name | Description |
|---|---|
| [onUnduplicatedRead](#onunduplicatedread) | This event is triggered when a new, unduplicated barcode is found. |
| [onFrameRead](#onframeread) | This event is triggered after the library finishes scanning a frame. |
| [decodeCurrentFrame](#decodecurrentframe) | Scans the current frame of the video for barcodes. |

### Basic Interaction

| API Name | Description |
|---|---|
| [show](#show) | Binds and shows UI, opens the camera and starts decoding. |
| [hide](#hide) | Stops decoding, releases camera and unbinds UI. |
| [pauseScan](#pausescan) | Pauses the decoding process. |
| [resumeScan](#resumescan) | Resumes the decoding process. |

### Scan Settings

| API Name | Description |
|---|---|
| [bPlaySoundOnSuccessfulRead](#bplaysoundonsuccessfulread) | Whether and when to play sound on barcode recognition. |
| [soundOnSuccessfullRead](#soundonsuccessfullread) | Specifies the sound to play on barcode recognition. |
| [bVibrateOnSuccessfulRead](#bvibrateonsuccessfulread) | Whether and when to vibrate on barcode recognition. |
| [vibrateDuration](#vibrateduration) | Returns or sets how long the vibration lastsin milliseconds.  |
| [singleFrameMode](#singleframemode) | Returns or sets whether to enable the singe-frame mode. | |
| [getScanSettings](#getscansettings) | Returns the current scan settings. |
| [updateScanSettings](#updatescansettings) | Changes scan settings with the object passed in. |

### UI Control

| API Name | Description |
|---|---|
| [getUIElement](#getuielement) | Returns the HTML element that is used by the `BarcodeScanner` instance. |
| [setUIElement](#setuielement) | Specifies an HTML element for the `BarcodeScanner` instance to use as its UI. |
| [defaultUIElementURL](#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [barcodeFillStyle](#barcodefillstyle) | Specifies the color used inside the shape which highlights a found barcode.  |
| [barcodeStrokeStyle](#barcodestrokestyle) | Specifies the color used to paint the outline of the shape which highlights a found barcode. |
| [barcodeLineWidth](#barcodelinewidth) | Specifies the line width of the outline of the shape which highlights a found barcode. |
| [regionMaskFillStyle](#regionmaskfillstyle) | Specifies the color used in the square-loop shape between the actual scanning area and the boundary of the video input. |
| [regionMaskStrokeStyle](#regionmaskstrokestyle) | Specifies the color used to paint the outline of the scanning region. |
| [regionMaskLineWidth](#regionmasklinewidth) | Specifies the width of the outline of the scanning region. |

### Camera Control

| API Name | Description |
|---|---|
| [getAllCameras](#getallcameras) | Returns infomation of all available cameras on the device. |
| [getCurrentCamera](#getcurrentcamera) | Returns information about the current camera. |
| [setCurrentCamera](#setcurrentcamera) | Chooses a camera as the video source. |
| [getResolution](#getresolution) | Returns the resolution of the current video input. |
| [setResolution](#setresolution) | Sets the resolution of the current video input. |
| [getVideoSettings](#getvideosettings) | Returns the current video settings. |
| [updateVideoSettings](#updatevideosettings) | Changes the video input. |
| [openVideo](#openvideo) | Binds UI and opens the camera to show the video stream. |
| [showVideo](#showvideo) | Similar to openVideo but will also show the UI Element if it is hidden. |
| [play](#play) | Play the video if it is already open but paused or stopped. |
| [onPlayed](#onplayed) | This event is triggered when the video stream starts playing. |
| [pause](#pause) | Pauses the video without releasing the camera. |
| [stop](#stop) | Stops the video and releases the camera. |

### Advanced Camera Control

| API Name | Description |
|---|---|
| [getCapabilities](#getcapabilities) | Inspects and returns the capabilities of the current camera. |
| [getCameraSettings](#getcamerasettings) | Returns the current values for each constrainable property of the current camera. |
| [setFrameRate](#setframerate) | Adjusts the frame rate. |
| [setColorTemperature](#setcolortemperature) | Adjusts the color temperature. |
| [setExposureCompensation](#setexposurecompensation) | Sets the exposure compensation index. |
| [setZoom](#setzoom) | Sets the exposure compensation index. |
| [turnOnTorch](#turnontorch) | Turns on the torch/flashlight. |
| [turnOffTorch](#turnofftorch) | Turns off the torch/flashlight. |

The following are inherited from the `BarcodeReader` Class.

### Change Settings

| API Name | Description |
|---|---|
| [getRuntimeSettings](./BarcodeReader.md#getruntimesettings) | Returns the current runtime settings. |
| [updateRuntimeSettings](./BarcodeReader.md#updateruntimesettings) | Updates runtime settings with a given struct or a preset template. |
| [resetRuntimeSettings](./BarcodeReader.md#resetruntimesettings) | Resets all parameters to default values. |
| [getModeArgument](./BarcodeReader.md#getmodeargument) | Returns the argument value for the specified mode parameter. |
| [setModeArgument](./BarcodeReader.md#setmodeargument) | Sets the argument value for the specified mode parameter. |

### Auxiliary

| API Name | Description |
|---|---|
| [bSaveOriCanvas](./BarcodeReader.md#bsaveoricanvas) | Whether to save the original image into a &lt; canvas&gt; element. |
| [oriCanvas](./BarcodeReader.md#oricanvas) | An `HTMLCanvasElement` that holds the original image. |



## createInstance

Creates a `BarcodeScanner` instance.

```typescript
static createInstance(): Promise<BarcodeScanner>
```

**Parameters**

None.

**Return value**

A promise resolving to the created `BarcodeScanner` object.

**Code Snippet**

```js
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
```



## destroy

Destroys the `BarcodeScanner` instance. If your page needs to create a new instance from time to time, don't forget to destroy unused old instances.

```typescript
destroy(): Promise<void>
```

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

  


## bDestroyed

Indicates whether the instance has been destroyed.

```typescript
readonly bDestroyed: boolean
```



## onUnduplicatedRead

This event is triggered when a new, unduplicated barcode is found.

The library keeps each barcode result (type and value) in the buffer for a period of time (can be set with [duplicateForgetTime](./interface/ScanSettings.md)) during which if a new result is an exact match, it's seen as a duplicate and will again be kept for that period of time while the old result is removed and so on.

```typescript
onUnduplicatedRead: (txt: string, result: TextResult) => void
```

**Arguments**

`txt` : a string that holds the barcode text. 

`result` : a `TextResult` object that contains more detailed info.

**Code Snippet**

```js
scanner.onUnduplicatedRead = (txt, result) = {
    alert(txt);
    console.log(result);
}
```

**See also**

* [TextResult](./interface/TextResult.md)



## onFrameRead

This event is triggered after the library finishes scanning a frame.

```typescript
onFrameRead: (results: TextResult[]) => void
```

**Arguments**

`results` : a `TextResult` object that contains all the barcode results in this frame.

**Code Snippet**

```js
scanner.onFrameRead = results => {
    for (let result of results) {
        console.log(result.barcodeText);
    }
};
```

**See also**

* [TextResult](./interface/TextResult.md)



## decodeCurrentFrame

Scans the current frame of the video for barcodes.

```typescript
decodeCurrentFrame(): Promise<TextResult[]>
```

**Parameters**

None.

**Return value**

A promise resolving to a `TextResult` object that contains all the barcode results found in this frame.

**Code Snippet**

```js
await scanner.showVideo();
console.log(await scanner.decodeCurrentFrame());
```

**See also**

* [TextResult](./interface/TextResult.md)



## show

Binds and shows UI, opens the camera and starts decoding.

```typescript
show(): Promise<ScannerPlayCallbackInfo>
```

**Parameters**

None.

**Return value**

A promise resolving to a `ScannerPlayCallbackInfo` object.

**Code Snippet**

```js
scanner.onUnduplicatedRead = (txt, result) => {
    alert(txt);
    console.log(result);
};
await scanner.show();
```

**See also**

* [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)



## hide

Stops decoding, releases camera and unbinds UI.

```typescript
hide(): Promise<void>
```

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



## pauseScan

Pauses the decoding process.

```typescript
pauseScan(): void
```

**Parameters**

None.

**Return value**

None.



## resumeScan

Resumes the decoding process.

```typescript
resumeScan(): void
```

**Parameters**

None.

**Return value**

None.



## bPlaySoundOnSuccessfulRead

Whether and when to play sound on barcode recognition (user input is required on iOS or [Chrome](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#chrome_enterprise_policies) for any sound to play). Allowed values are

* `false`: never play sound, the default value; <!--never-->
* `true`: play sound when one or multiple barcodes are found on a frame; <!--always-->
* `frame`: same as `true`; 
* `unduplicated`: play sound when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, play only once).

```typescript
bPlaySoundOnSuccessfulRead: (boolean | string)
```

**Default value**

 `false`

**Code Snippet**

```js
// A user gesture required. 
startPlayButton.addEventListener('click', function() {
    scanner.bPlaySoundOnSuccessfulRead = true;
});
```



## soundOnSuccessfullRead

Specifies the sound to play on barcode recognition. If not specified, the default one is used.

```typescript
soundOnSuccessfullRead: HTMLAudioElement
```

**Code Snippet**

```js
scanner.soundOnSuccessfullRead = new Audio("./pi.mp3");
```

**See also**

* [HTMLAudioElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLAudioElement)
* [bPlaySoundOnSuccessfulRead](#bplaysoundonsuccessfulread)

## bVibrateOnSuccessfulRead

Whether and when to vibrate on barcode recognition (user input is required in [Chrome](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#chrome_enterprise_policies) for the vibration). It only supports Android Devices with a vibrating system. Allowed values are

* `false`: never vibrate, the default value; <!--never-->
* `true`: vibrate when one or multiple barcodes are found on a frame; <!--always-->
* `frame`: same as `true`; 
* `unduplicated`: vibrate when a unique/unduplicated barcode is found (if multiple unique barcodes are found on the same frame, vibrate only once).

```typescript
bVibrateOnSuccessfulRead: (boolean | string)
```

**Default value**

 `false`

**Code Snippet**

```js
// Can I use? https://caniuse.com/?search=vibrate
startVibrateButton.addEventListener('click', function() {
    scanner.bVibrateOnSuccessfulRead = true;
});
```



## vibrateDuration

Returns or sets how long the vibration lasts in milliseconds. It only supports Android Devices with a vibrating system. The default value is `300` .

```typescript
vibrateDuration: number
```

**See also** 

* [bVibrateOnSuccessfulRead](#bvibrateonsuccessfulread)



## singleFrameMode

Returns or sets the status of the single-frame mode. If enabled, the video input will not be played and the user can choose to take a picture with the system camera or select an existing image for barcode reading.

The single-frame mode can only be enabled or disabled before the video input starts playing.

```typescript
singleFrameMode: boolean
```



## getScanSettings

Returns the current scan settings.

```typescript
getScanSettings(): Promise<ScanSettings>
```

**Parameters**

None.

**Return value**

A promise resolving to a `ScanSettings` .

**Code Snippet**

```js
let scanSettings = await scanner.getScanSettings();
scanSettings.intervalTime = 50;
scanSettings.duplicateForgetTime = 1000;
await scanner.updateScanSettings(scanSettings);
```

**See also**

* [ScanSettings](./interface/ScanSettings.md)



## updateScanSettings

Changes scan settings with the object passed in.

```typescript
updateScanSettings(settings: ScanSettings): Promise<void>
```

**Parameters**

`settings` : specifies the new scan settings.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
let scanSettings = await scanner.getScanSettings();
scanSettings.intervalTime = 50;
scanSettings.duplicateForgetTime = 1000;
await scanner.updateScanSettings(scanSettings);
```

**See also**

* [ScanSettings](./interface/ScanSettings.md)



## getUIElement

Returns the HTML element that is used by the [BarcodeScanner](#barcodescanner) instance.

```typescript
getUIElement(): HTMLElement
```



## setUIElement

Specifies an HTML element for the [BarcodeScanner](#barcodescanner) instance to use as its UI. The structure inside the element determines the appearance of the UI. See more on [how to customize the UI](../user-guide/#customize-the-ui).

```typescript
setUIElement(elementOrURL: HTMLElement | string): Promise<void>
```

**Parameters**

`elementOrURL` : specifies the element.

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



## defaultUIElementURL

Returns or sets the URL of the *.html* file that defines the default UI Element. The URL can only be set before the API [createInstance](#createinstance) is called.

```typescript
static defaultUIElementURL: string
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeScanner.defaultUIElementURL = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.4.0/dist/dbr.scanner.html";
let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
await scanner.show();
```



## barcodeFillStyle

Specifies the color used inside the shape which highlights a found barcode. The default value is `rgba(254, 180, 32, 0.3)` .

```typescript
barcodeFillStyle: string
```



## barcodeStrokeStyle

Specifies the color used to paint the outline of the shape which highlights a found barcode. The default value is `rgba(254,180,32,0.9)`.

```typescript
barcodeStrokeStyle: string
```



## barcodeLineWidth

Specifies the line width of the outline of the shape which highlights a found barcode. The default value is `1`.

```typescript
barcodeLineWidth: number
```



## regionMaskFillStyle

Specifies the color used in the square-loop shape between the actual scanning area and the boundary of the video input. This shape only appears when the barcode scanning is limited to a specified region. The default value is `rgba(0,0,0,0.5)`.

```typescript
regionMaskFillStyle: string
```

**See also**

* [Read a specific area/region](../user-guide/advanced-usage.html#read-a-specific-arearegion)



## regionMaskStrokeStyle

Specifies the color used to paint the outline of the scanning region. This outline only appears when the barcode scanning is limited to a specified region. The default value is `rgb(254,142,20)`.

```typescript
regionMaskStrokeStyle: string
```

**See also**

* [Read a specific area/region](../user-guide/advanced-usage.html#read-a-specific-arearegion)



## regionMaskLineWidth

Specifies the width of the outline of the scanning region. This outline only appears when the barcode scanning is limited to a specified region. The default value is `2`.

```typescript
regionMaskLineWidth: number
```

**See also**

* [Read a specific area/region](../user-guide/advanced-usage.html#read-a-specific-arearegion)



## getAllCameras

Returns infomation of all available cameras on the device.

```typescript
getAllCameras(): Promise<VideoDeviceInfo[]>
```

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

**See also**

* [VideoDeviceInfo](./interface/VideoDeviceInfo.md)



## getCurrentCamera

Returns information about the current camera.

```typescript
getCurrentCamera(): Promise<VideoDeviceInfo | null>
```

**Parameters**

None.

**Return value**

A promise resolving to a `VideoDeviceInfo` object.

**Code Snippet**

```js
let camera = await scanner.getCurrentCamera();
```

**See also**

* [VideoDeviceInfo](./interface/VideoDeviceInfo.md)



## setCurrentCamera

Chooses a camera as the video source.

```typescript
setCurrentCamera(deviceID: string): Promise<ScannerPlayCallbackInfo>
```

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

**See also**

* [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)



## getResolution

Returns the resolution of the current video input.

```typescript
getResolution(): number[]
```

**Parameters**

None.

**Return value**

An array of two numbers representing the resolution.

**Code Snippet**

```js
let rsl = await scanner.getResolution();
console.log(rsl.width + " x " + rsl.height);
```



## setResolution

Sets the resolution of the current video input. If the specified resolution is not exactly supported, the closest resolution will be applied.

```typescript
setResolution(width: number, height: number): Promise<ScannerPlayCallbackInfo>
```

**Parameters**

`width`: specifies the horizontal resolution.
`height`: specifies the vertical resolution.

**Return value**

A promise resolving to a `ScannerPlayCallbackInfo` object.

**Code Snippet**

```js
await scanner.setResolution(width, height);
```

**See also**

* [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)



## getVideoSettings

Returns the current video settings.

```typescript
getVideoSettings(): MediaStreamConstraints
```

**Parameters**

None.

**Return value**

A `MediaStreamConstraints` object.

**See also**

* [MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints)



## updateVideoSettings

Changes the video input.

```typescript
updateVideoSettings(constraints: MediaStreamConstraints): Promise<ScannerPlayCallbackInfo | void>
```

**Parameters**

`constraints`: specifies the new video settings.

**Return value**

A promise resolving to a `ScannerPlayCallbackInfo` object.

**Code Snippet**

```js
await scanner.updateVideoSettings({ video: {width: {ideal: 1280}, height: {ideal: 720}, facingMode: {ideal: 'environment'}} });
```

**See also**

* [MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints)
* [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)



## openVideo

Binds UI and opens the camera to show the video stream.

```typescript
openVideo(): Promise<ScannerPlayCallbackInfo>
```

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

**See also**

* [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)



## showVideo

Similar to [openVideo](#openvideo) but will also show the UI Element if it is hidden.

```typescript
showVideo(): Promise<ScannerPlayCallbackInfo>
```

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

**See also**

* [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)



## play

Play the video if it is already open but paused or stopped. If the video is already playing, it will start again.

```typescript
play(): Promise<ScannerPlayCallbackInfo>
```

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

**See also**

* [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)



## onPlayed

This event is triggered when the video stream starts playing.

```typescript
event onPlayed: (info: ScannerPlayCallbackInfo) => void
```

**Arguments**

info: a `ScannerPlayCallbackInfo` object which describes the resolution of the video input.

**Code Snippet**

```js
scanner.onplayed = rsl=>{ console.log(rsl.width+'x'+rsl.height) };
await scanner.show(); // or open(), play(), setCurrentCamera(), etc.
```

**See also**

* [ScannerPlayCallbackInfo](./interface/ScannerPlayCallbackInfo.md)



## pause

Pauses the video without releasing the camera.

```typescript
pause(): void
```

**Parameters**

None.

**Return value**

None.



## stop

Stops the video and releases the camera.

```typescript
stop(): void
```

**Parameters**

None.

**Return value**

None.



## getCapabilities

Inspects and returns the capabilities of the current camera.

Right now, this method only works in Chrome and should be called when the scanner is open.

```typescript
getCapabilities(): MediaTrackCapabilities
```

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

**See also**

* [MediaTrackCapabilities](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/getCapabilities)



## getCameraSettings

Returns the current values for each constrainable property of the current camera.

Right now, this method only works in Chrome and should be called when the scanner is open.

```typescript
getCameraSettings(): any
```

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

* [getCapabilities](#getcapabilities)



## setFrameRate

Adjusts the frame rate.

Right now, this method only works in Chrome and should be called when the scanner is open.

```typescript
setFrameRate(rate: number): Promise<void>
```

**Parameters**

`rate`: specifies the new frame rate.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.setFrameRate(10);
```

**See also**

* [getCapabilities](#getcapabilities)



## setColorTemperature

Adjusts the color temperature.

Right now, this method only works in Chrome and should be called when the scanner is open.

```typescript
setColorTemperature(colorTemperatur: number): Promise<void>
```

**Parameters**

`colorTemperatur`: specifies the new color temperature.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.setColorTemperature(5000);
```

**See also**

* [getCapabilities](#getcapabilities)



## setExposureCompensation

Sets the exposure compensation index.

Right now, this method only works in Chrome and should be called when the scanner is open.

```typescript
setExposureCompensation(exposureCompensation: number): Promise<void>
```

**Parameters**

`exposureCompensation`: specifies the new exposure compensation index.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.setExposureCompensation(-0.7);
```

**See also**

* [getCapabilities](#getcapabilities)



## setZoom

Sets current zoom value. 

```typescript
setZoom(zoomValue: number): Promise<void>
```

**Parameters**

`zoomValue`: specifies the new zoom value.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.setZoom(400);
```

**See also**

* [getCapabilities](#getcapabilities)



## turnOnTorch

Turns on the torch/flashlight.

Right now, this method only works in Chrome and should be called when the scanner is open.

```typescript
turnOnTorch(): Promise<void>
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.turnOnTorch();
```

**See also**

* [turnOffTorch](#turnofftorch)
* [getCapabilities](#getcapabilities)



## turnOffTorch

Turns off the torch/flashlight.

Right now, this method only works in Chrome and should be called when the scanner is open.

```typescript
turnOffTorch(): Promise<void>
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```js
await scanner.turnOffTorch();
```

**See also**

* [turnOnTorch](#turnontorch)
* [getCapabilities](#getcapabilities)

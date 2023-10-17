---
layout: default-layout
title: v10.0.20 User Guide - Dynamsoft Barcode Reader JavaScript Edition
description: This is the user guide of Dynamsoft Barcode Reader JavaScript SDK.
keywords: user guide, javascript, js
breadcrumbText: User Guide
noTitleIndex: true
needGenerateH3Content: true
needAutoGenerateSidebar: true
permalink: /programming/javascript/user-guide/index.html
schema: schemas/dynamsoft-facilitates-mit-research-schema.json
---

<!--The original doc is hosted here => https://github.com/dynamsoft-docs/barcode-reader-docs-js/blob/main/programming/javascript/user-guide/index.md -->

# Barcode Reader for Your Website - User Guide

[Dynamsoft Barcode Reader JavaScript Edition](https://www.dynamsoft.com/barcode-reader/sdk-javascript/) (DBR-JS) is equipped with industry-leading algorithms for exceptional speed, accuracy and read rates in barcode reading. Using its well-designed API, you can turn your web page into a barcode scanner with just a few lines of code.

![version](https://img.shields.io/npm/v/dynamsoft-barcode-reader.svg)
![downloads](https://img.shields.io/npm/dm/dynamsoft-barcode-reader.svg)
![jsdelivr](https://img.shields.io/jsdelivr/npm/hm/dynamsoft-barcode-reader.svg)
![vulnerabilities](https://img.shields.io/snyk/vulnerabilities/npm/dynamsoft-barcode-reader.svg)

Once the DBR-JS SDK gets integrated into your web page, your users can access a camera via the browser and read barcodes directly from its video input.

In this guide, you will learn step by step on how to integrate the DBR-JS SDK into your website.

<span style="font-size:20px">Table of Contents</span>

- [Barcode Reader for Your Website - User Guide](#barcode-reader-for-your-website---user-guide)
  - [Hello World - Simplest Implementation](#hello-world---simplest-implementation)
    - [Understand the code](#understand-the-code)
      - [About the code](#about-the-code)
    - [Run the example](#run-the-example)
  - [Building your own page](#building-your-own-page)
    - [Include the SDK](#include-the-sdk)
      - [Use a public CDN](#use-a-public-cdn)
    - [Prepare the SDK](#prepare-the-sdk)
      - [Specify the license](#specify-the-license)
      - [Specify the location of the "engine" files (optional)](#specify-the-location-of-the-engine-files-optional)
    - [Set up and start image processing](#set-up-and-start-image-processing)
      - [Preload the module](#preload-the-module)
      - [Create a CaptureVisionRouter object](#create-a-capturevisionrouter-object)
      - [Connect an image source](#connect-an-image-source)
      - [Register a result receiver](#register-a-result-receiver)
      - [Start the process](#start-the-process)
    - [Customize the process](#customize-the-process)
      - [Adjust the preset template settings](#adjust-the-preset-template-settings)
      - [Edit the preset templates directly](#edit-the-preset-templates-directly)
      - [Filter the results](#filter-the-results)
        - [Option 1: Verify results across multiple frames](#option-1-verify-results-across-multiple-frames)
        - [Option 2: Remove duplicate results found close in time](#option-2-remove-duplicate-results-found-close-in-time)
      - [Add feedback](#add-feedback)
    - [Customize the UI](#customize-the-ui)
  - [API Documentation](#api-documentation)
  - [System Requirements](#system-requirements)
  - [How to Upgrade](#how-to-upgrade)
  - [Release Notes](#release-notes)
  - [Next Steps](#next-steps)

**Popular Examples**

<!--TODO: update the sample links-->
- Hello World - [Guide](#hello-world---simplest-implementation) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v10.0.20/1.hello-world/1.hello-world.html) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/1.hello-world.html?ver=10.0.20&utm_source=guide)
- Angular App - [Guide](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/samples-demos/helloworld-angular.html?ver=10.0.20&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v10.0.20/1.hello-world/3.read-video-angular) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/3.read-video-angular/dist/hello-world/?ver=10.0.20&utm_source=guide)
- React App - [Guide](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/samples-demos/helloworld-reactjs.html?ver=10.0.20&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v10.0.20/1.hello-world/4.read-video-react) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/4.read-video-react/build/?ver=10.0.20&utm_source=guide)
- Vue App - [Guide](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/samples-demos/helloworld-vuejsv3.html?ver=10.0.20&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v10.0.20/1.hello-world/6.read-video-vue3) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/6.read-video-vue3/dist/?ver=10.0.20&utm_source=guide)
- PWA App - [Guide](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/samples-demos/helloworld-pwa.html?ver=10.0.20&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v10.0.20/1.hello-world/10.read-video-pwa) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/10.read-video-pwa/helloworld-pwa.html?ver=10.0.20&utm_source=guide)
- WebView in Android and iOS - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/v10.0.20/1.hello-world/14.read-video-webview)
- Read Driver Licenses - [Guide](https://www.dynamsoft.com/barcode-reader/docs/core/programming/usecases/scan-and-parse-AAMVA.html?ver=10.0.20&utm_source=guide&&lang=js) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v10.0.20/4.use-case/2.read-a-drivers-license.html) \| [Run](https://demo.dynamsoft.com/samples/dbr/js/4.use-case/2.read-a-drivers-license.html?ver=10.0.20&utm_source=guide)
- Fill A Form - [Guide](https://www.dynamsoft.com/barcode-reader/docs/core/programming/usecases/scan-barcodes-as-input.html?lang=js&&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v10.0.20/4.use-case/1.fill-a-form-with-barcode-reading.html) \| [Run](https://demo.dynamsoft.com/samples/dbr/js/4.use-case/1.fill-a-form-with-barcode-reading.html?ver=10.0.20&utm_source=guide)
- Show result information on the video - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/main/4.use-case/3.show-result-texts-on-the-video.html) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/4.use-case/3.show-result-texts-on-the-video.html?ver=10.0.20&utm_source=guide)
- Debug Camera and Collect Video Frame - [Guide](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/samples-demos/debug.html?lang=js&&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v10.0.20/5.others/debug)

You can also:

- Try the Official Demo - [Run](https://demo.dynamsoft.com/barcode-reader-js/?ver=10.0.20&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-demo/)
- Try Online Examples - [Run](https://demo.dynamsoft.com/Samples/DBR/JS/index.html?ver=10.0.20&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/v10.0.20/)

## Hello World - Simplest Implementation

Let's start with the "Hello World" example of the DBR-JS SDK which demonstrates how to use the minimum code to enable a web page to read barcodes from a live video stream.  

- Basic Requirements
  - Internet connection
  - [A supported browser](#system-requirements)
  - Camera access

### Understand the code

The complete code of the "Hello World" example is shown below

```html
<!DOCTYPE html>
<html lang="en">
  <body>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-core@3.0.20/dist/core.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-utility@1.0.20/dist/utility.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader@10.0.20/dist/dbr.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.0.20/dist/cvr.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.1/dist/dce.js"></script>
    <div id="cameraViewContainer" style="width: 100vw; height: 100vh"></div>
    <script>
      (async function () {
        Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");

        let router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
        
        let view = await Dynamsoft.DCE.CameraView.createInstance();
        let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
        document.querySelector("#cameraViewContainer").append(view.getUIElement());
        router.setInput(cameraEnhancer);

        const resultReceiver = new Dynamsoft.CVR.CapturedResultReceiver();
        resultReceiver.onDecodedBarcodesReceived = (result) => {
          if (result.barcodesResultItems.length > 0) {
            alert(result.barcodesResultItems[0].text);
          }
        };
        if (resultReceiver) router.addResultReceiver(resultReceiver);

        await cameraEnhancer.open();
        await router.startCapturing("ReadSingleBarcode");
      })();
    </script>
  </body>
</html>
```

<!--TOM: Update the code links-->

<p align="center" style="text-align:center; white-space: normal; ">
  <a target="_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v10.0.20/1.hello-world/1.hello-world.html" title="Code in Github" style="text-decoration:none;">
    <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/github.svg" alt="Code in Github" width="20" height="20" style="width:20px;height:20px;">
  </a>
  &nbsp;
  <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/pL4e7yrd/" title="Run via JSFiddle" style="text-decoration:none;">
    <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/jsfiddle.svg" alt="Run via JSFiddle" width="20" height="20" style="width:20px;height:20px;" >
  </a>
  &nbsp;
  <a target="_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/1.hello-world.html?ver=10.0.20&utm_source=guide" title="Run in Dynamsoft" style="text-decoration:none;">
    <img src="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/svgs/solid/circle-play.svg" alt="Run in Dynamsoft" width="20" height="20" style="width:20px;height:20px;">
  </a>
</p>

-----

#### About the code

- `Dynamsoft.License.LicenseManager.initLicense()`: This method initializes the license for using the SDK in the application. Note that the string "**DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9**" used in this example points to an online license that requires a network connection to work. Read more on [Specify the license](#specify-the-license).

- `Dynamsoft.CVR.CaptureVisionRouter.createInstance()`: This method creates a `CaptureVisionRouter` object `router` which controls the entire process in three steps:
  - **Retrieve Images from the Image Source**
    - `router` connects to the image source through the [`Image Source Adapter`](https://www.dynamsoft.com/capture-vision/docs/core/architecture/input.html#image-source-adapter?lang=js) interface with the method `setInput()`.
      ```js
      router.setInput(cameraEnhancer)
      ```
    > The image source in our case is a CameraEnhancer object created with `Dynamsoft.DCE.CameraEnhancer.createInstance(view)`
  - **Coordinate Image-Processing Tasks**
    - The coordination happens behind the scenes. `router` starts the process by specifying a preset template "ReadSingleBarcode" with the method `startCapturing()`.
      ```js
      router.startCapturing("ReadSingleBarcode")
      ```
  - **Dispatch Results to Listening Objects**
    - The processing results are returned through the [`CapturedResultReceiver`](https://www.dynamsoft.com/capture-vision/docs/core/architecture/output.html#captured-result-receiver?lang=js) interface. The `CapturedResultReceiver` object `resultReceiver` is registered to `router` via the method `addResultReceiver()`.
      ```js
      router.addResultReceiver(resultReceiver);
      ```
> Read more on [Capture Vision Router](https://www.dynamsoft.com/capture-vision/docs/core/architecture/#capture-vision-router).

### Run the example

<!--TODO: change links-->

You can run the example deployed to <a target="_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/1.hello-world.html?ver=10.0.20&utm_source=guide" title="Run in Dynamsoft">the Dynamsoft Demo Server</a> or test it with <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/pL4e7yrd/" title="Run in JSFiddle">JSFiddle code editor</a>. 

You will be asked to allow access to your camera, after which the video will be displayed on the page. After that, you can point the camera at a barcode to read it.

When a barcode is decoded, you will see the result text pop up and the barcode location will be highlighted in the video feed.

Alternatively, you can test locally by copying and pasting the code shown above into a file called "hello-world.html" and opening it in your browser.

*Note*:

If you open the web page as `file:///` or `http://` , the camera may not work correctly because the API <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia" title="getUserMedia">getUserMedia</a> usually requires HTTPS to access the camera.

To make sure your web application can access the camera, please configure your web server to support HTTPS. The following links may help.

1. NGINX: <a target="_blank" href="https://nginx.org/en/docs/http/configuring_https_servers.html" title="Configuring HTTPS servers">Configuring HTTPS servers</a>
2. IIS: <a target="_blank" href="https://aboutssl.org/how-to-create-a-self-signed-certificate-in-iis/" title="How to create a Self Signed Certificate in IIS">How to create a Self Signed Certificate in IIS</a>
3. Tomcat: <a target="_blank" href="https://dzone.com/articles/setting-ssl-tomcat-5-minutes" title="Setting Up SSL on Tomcat in 5 minutes">Setting Up SSL on Tomcat in 5 minutes</a>
4. Node.js: <a target="_blank" href="https://nodejs.org/docs/v0.4.1/api/tls.html" title="npm tls">npm tls</a>

If the test doesn't go as expected, you can [contact us](https://www.dynamsoft.com/company/contact/?ver=10.0.20&utm_source=guide).

## Building your own page

### Include the SDK

<!--TODO: add mising info-->
To use the SDK, we first include the related resource files:
  - `core.js` provides the definitions for the basic objects;
  - `utility.js` provides auxiliary classes shared between all Dynamsoft SDKs;
  - `dbr.js` provides basic information about the barcode reader library;
  - `cvr.js` provides the fundamental features including license control, process control, etc.;
  - `dce.js` provides camera support.

#### Use a public CDN

The simplest way to include the SDK is to use either the [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/) CDN. The "hello world" example above uses **jsDelivr**.

- jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-core@3.0.20/dist/core.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-utility@1.0.20/dist/utility.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader@10.0.20/dist/dbr.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.0.20/dist/cvr.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.1/dist/dce.js"></script>
  ```

- UNPKG  

  ```html
  <script src="https://unpkg.com/dynamsoft-core@3.0.20/dist/core.js"></script>
  <script src="https://unpkg.com/dynamsoft-utility@1.0.20/dist/utility.js"></script>
  <script src="https://unpkg.com/dynamsoft-barcode-reader@10.0.20/dist/dbr.js"></script>
  <script src="https://unpkg.com/dynamsoft-capture-vision-router@2.0.20/dist/cvr.js"></script>
  <script src="https://unpkg.com/dynamsoft-camera-enhancer@4.0.1/dist/dce.js"></script>  ```

In some rare cases, you might not be able to access the CDN. If this happens, you can use the following files for the test. 

- [dynamsoft-core@3.0.20]()
- [dynamsoft-utility@1.0.20]()
- [dynamsoft-barcode-reader@10.0.20]()
- [dynamsoft-capture-vision-router@2.0.20]()
- [dynamsoft-camera-enhancer@4.0.1]()

However, please **DO NOT** use the above files in a production application as they are for temporary testing purposes only.

#### Host the SDK yourself

Besides using the public CDN, you can also download the SDK and host its files on your own server or a commercial CDN before including it in your application.

Options to download the SDK:

- From the website

  <a target="_blank" href="https://www.dynamsoft.com/barcode-reader/downloads/?ver=10.0.20&utm_source=guide" title="Download the JavaScript Package">Download the JavaScript Package</a>

- yarn

  ```cmd
  yarn add dynamsoft-core@3.0.20 --save
  yarn add dynamsoft-utility@1.0.20 --save
  yarn add dynamsoft-barcode-reader@10.0.20 --save
  yarn add dynamsoft-capture-vision-router@2.0.20 --save
  yarn add dynamsoft-camera-enhancer@4.0.1 --save
  ```

- npm

  ```cmd
  npm install dynamsoft-core@3.0.20 --save
  npm install dynamsoft-utility@1.0.20 --save
  npm install dynamsoft-barcode-reader@10.0.20 --save
  npm install dynamsoft-capture-vision-router@2.0.20 --save
  npm install dynamsoft-camera-enhancer@4.0.1 --save
  ```

Depending on how you downloaded the SDK and how you intend to use it, you can typically include it like this:

```html
<script src="./dynamsoft/distributables/dynamsoft-core@3.0.20/dist/core.js"></script>
<script src="./dynamsoft/distributables/dynamsoft-utility@1.0.20/dist/utility.js"></script>
<script src="./dynamsoft/distributables/dynamsoft-barcode-reader@10.0.20/dist/dbr.js"></script>
<script src="./dynamsoft/distributables/dynamsoft-capture-vision-router@2.0.20/dist/cvr.js"></script>
<script src="./dynamsoft/distributables/dynamsoft-camera-enhancer@4.0.1/dist/dce.js"></script>
```

or

```html
<script src="/node_modules/dynamsoft-core/dist/core.js">
<script src="/node_modules/dynamsoft-utility/dist/utility.js"></script>
<script src="/node_modules/dynamsoft-barcode-reader/dist/dbr.js"></script>
<script src="/node_modules/dynamsoft-capture-vision-router/dist/cvr.js"></script>
<script src="/node_modules/dynamsoft-camera-enhancer/dist/dce.js"></script>
```

or

```ts
import { EnumCapturedResultItemType, type DSImageData } from "dynamsoft-core";
import { type BarcodeResultItem } from "dynamsoft-barcode-reader";
import { CapturedResultReceiver, CaptureVisionRouter, type SimplifiedCaptureVisionSettings } from "dynamsoft-capture-vision-router";
import { CameraEnhancer, CameraView } from "dynamsoft-camera-enhancer";
```

*Note*:

* Some older web application servers do not set `.wasm` mimetype as `application/wasm`. Upgrade your web application servers, or define the mimetype yourselves:
  * [Apache](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Apache_Configuration_htaccess#media_types_and_character_encodings)
  * [IIS](https://docs.microsoft.com/en-us/iis/configuration/system.webserver/staticcontent/mimemap)
  * [Nginx](https://www.nginx.com/resources/wiki/start/topics/examples/full/#mime-types)

* To work properly, the SDK requires a few engine files, which are relatively large and may take quite a few seconds to download. We recommend that you set a longer cache time for these engine files, to maximize the performance of your web application.

  ```cmd
  Cache-Control: max-age=31536000
  ```

  Reference: [Cache-Control](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control).

### Prepare the SDK

Before using the SDK, you need to configure a few things.

#### Specify the license

The SDK requires a license to work, use the API `initLicense` and specify a license key.

```javascript
Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");
```

As mentioned previously, the key `DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9` is a test license good for 24 hours. To test the SDK further, you can request a 30-day free trial license via the [customer portal](https://www.dynamsoft.com/customer/license/trialLicense?ver=10.0.20&utm_source=guide&product=dbr&package=js).

> If you have registerred a Dynamsoft account and downloaded the SDK from the official website, Dynamsoft will automatically generate a 30-day free trial license and put the license key into all the samples that come with the SDK.

#### Specify the location of the "engine" files (optional)

This is usually only required with frameworks like Angular or React, etc. where the referenced JavaScript files such as `cvr.js`, `dbr.js` are compiled into another file.

The purpose is to tell the SDK where to find the engine files (\*.worker.js, \*.wasm.js and \*.wasm, etc.). The API is called `engineResourcePath`:

```javascript
//The following code uses the jsDelivr CDN, feel free to change it to your own location of these files
CameraView.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.1/dist/";
CaptureVisionRouter.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.0.20/dist/";
BarcodeReaderModule.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader@10.0.20/dist/";
```

### Set up and start image processing

#### Preload the module

The image processing logic is built into .wasm libraries which usually take a bit of time to download. We recommend calling the following method to preload the libraries to speed things up.

```js
// Preload the DBR library
Dynamsoft.CVR.CaptureVisionRouter.preloadModule(["DBR"]);
```

#### Create a CaptureVisionRouter object

To use the SDK, we first create a `CaptureVisionRouter` object.

```javascript
Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");

let router = null;
try {
    router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
} catch (ex) {
    console.error(ex);
}
```

*Tip*:

When creating a `CaptureVisionRouter` object within a function which may be called more than once, it's best to use a "helper" variable to avoid double creation such as `pRouter` in the following code

```javascript
Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");

let pRouter = null;
let router = null;

document.getElementById('btn-scan').addEventListener('click', async () => {
    try {
        router = await (pRouter = pRouter || Dynamsoft.CVR.CaptureVisionRouter.createInstance());
    } catch (ex) {
        console.error(ex);
    }
});
```

#### Connect an image source

The `CaptureVisionRouter` object, `router`, processes images which are supplied by an image source. In our case, we want to find barcodes directly from the live video stream. Therefore, we create a `CameraEnhancer` object, `cameraEnhancer`, which is able to capture image frames from the video and pass them to `router`.

A `CameraView` object, `view`, is also created and passed to `cameraEnhancer` to help stream the video on the web page.

```html
<div id="cameraViewContainer" style="width: 100vw; height: 100vh"></div>
```

```javascript
let view = await Dynamsoft.DCE.CameraView.createInstance();
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
document.querySelector("#cameraViewContainer").append(view.getUIElement());
router.setInput(cameraEnhancer);
```

#### Register a result receiver

After images are processed, the results are dispatched to all registered `CapturedResultReceiver` objects. Each `CapturedResultReceiver` object may contain one or more callback functions corresponding to different types of results. In our case, we are interested in the barcodes found on the images, so we only need to define the callback function `onDecodedBarcodesReceived`:

```javascript
const resultReceiver = new Dynamsoft.CVR.CapturedResultReceiver();
resultReceiver.onDecodedBarcodesReceived = (result) => {
  // In this example, we are simply showing the barcode text in an alert box.
  if (result.barcodesResultItems.length > 0) {
    alert(result.barcodesResultItems[0].text);
  }
};
if (resultReceiver) router.addResultReceiver(resultReceiver);
```

Check out [CapturedResultReceiver](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/captured-result-receiver.html) for more information.

#### Start the process

Now that we have completed the set-up, we can go ahead and start processing the images in two simple steps:

1. Activate the image source to start collecting images. In our case, we call `open()` on `cameraEnhancer` to start streaming video and simultaneously start collecting images which will be sent to `router` upon its request.
2. Specify a preset template to start processing the images, in our case, we use the template "ReadSingleBarcode" which is designed to process images that have only one barcode on them.

```javascript
await cameraEnhancer.open();
await router.startCapturing("ReadSingleBarcode");
```

*Note*:

* `router` is designed to continuously request images from the image source.
* There are several different preset templates available for reading barcodes:

| Template Name                  | Function                                               |
| ------------------------------ | ------------------------------------------------------ |
| **ReadBarcodes_Default**       | Try to find barcodes without priority.                 |
| **ReadSingleBarcode**          | Try to find one barcode as fast as possible.           |
| **ReadBarcodes_SpeedFirst**    | Try to find barcodes as fast as possible.              |
| **ReadBarcodes_ReadRateFirst** | Try to find as many barcodes as possible.              |
| **ReadBarcodes_Balance**       | Try to find as many barcodes and as fast as possible.  |
| **ReadDenseBarcodes**          | Try to read barcodes that contain lots of information. |
| **ReadDistantBarcodes**        | Try to find barcodes from a distance.                  |

### Customize the process

#### Adjust the preset template settings

* Change barcode settings

The preset templates can be updated to meet different requirements. For example, the following code limits the barcode format to QR code.

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.barcodeSettings.barcodeFormatIds =
  Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

<!-- TODO: add link to barcodeSettings -->
For a list of adjustable barcode settings, check out [SimplifiedBarcodeReaderSettings](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/simplified-barcode-reader-settings.html);

* Change result types

We can also update the template to return more results. For example, with the following code, we can get the original image from which the barcode is found:

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.capturedResultItemTypes += Dynamsoft.Core.EnumCapturedResultItemType.CRIT_ORIGINAL_IMAGE;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

However, we do need to update the `CapturedResultReceiver` object to get the results. For example:

```javascript
resultReceiver.onCapturedResultReceived = (result) => {
  let barcodes = result.items.filter(
    (item) =>
      item.type === Dynamsoft.Core.EnumCapturedResultItemType.CRIT_BARCODE
  );
  if (barcodes.length > 0) {
    let image = result.items.filter(
      (item) =>
        item.type ===
        Dynamsoft.Core.EnumCapturedResultItemType.CRIT_ORIGINAL_IMAGE
    )[0].imageData;
    // The image that we found the barcode(s) on.
  }
};
```

* Change reading frequency

By default, the SDK is designed to process one image after another without interruption. While this ensures optimal performance, it also means high power consumption, which can cause the device to overheat. Often, we can slow down our reading speed and still meet business needs. The following code shows how to configure the SDK to process an image every 500 milliseconds.

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.minImageCaptureInterval = 500;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

* Specify a scan region

You can use the parameter `roi` (region of interest) together with the parameter `roiMeasuredInPercentage` to configure the SDK to only read a specific region on the image frames. For example, the following code limits the reading in the center 25% of the image frames:

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.roiMeasuredInPercentage = true;
settings.roi.points = [
  { x: 25, y: 25 },
  { x: 75, y: 25 },
  { x: 75, y: 75 },
  { x: 25, y: 75 },
];
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

Although the above does the job, a better way is to limit the scan region at the image source as shown in the code snippet below.

> When the region is set at the image source, the images are cropped directly before they are collected for processing, so there is no need to change the processing settings any more.

```javascript
cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(
  view
);
cameraEnhancer.setScanRegion({
  x: 25,
  y: 25,
  width: 50,
  height: 50,
  isMeasuredInPercentage: true,
});
```

* Specify the maximum time allowed for processing each image

You can set the maximum time allowed for processing a single image with the property `timeout` like this:

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.timeout = 500;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

#### Edit the preset templates directly

The preset templates have a lot more settings that can be customized to best suit your use case. If you [download the SDK from Dynamsoft website](https://www.dynamsoft.com/barcode-reader/downloads/1000003-confirmation/), you can find the templates under

* "/dynamsoft-barcode-reader-js-10.0.20/dynamsoft/resources/barcode-reader/templates/"

Once you have finished editing the template, you can use it by specifying its path with the method `initsettings`.

```javascript
await router.initSettings("PATH-TO-THE-FILE"); //e.g. "https://your-website/ReadSingleBarcode.json")
await router.startCapturing("ReadSingleBarcode");
```

#### Filter the results

When processing video frames, the same barcode is usually read multiple times. We can filter these results for better user experience. At present, there are two options available:

##### Option 1: Verify results across multiple frames

```js
let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
filter.enableResultCrossVerification(
  Dynamsoft.Core.EnumCapturedResultItemType.CRIT_BARCODE,
  true
);
await router.addResultFilter(filter);
```

##### Option 2: Remove duplicate results found close in time         

```js
let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
filter.enableResultDeduplication(
  Dynamsoft.Core.EnumCapturedResultItemType.CRIT_BARCODE,
  true
);
await router.addResultFilter(filter);
```

Note that you can also enable both options at the same time.

```js
let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
filter.enableResultCrossVerification(
  Dynamsoft.Core.EnumCapturedResultItemType.CRIT_BARCODE,
  true
);
filter.enableResultDeduplication(
  Dynamsoft.Core.EnumCapturedResultItemType.CRIT_BARCODE,
  true
);
await router.addResultFilter(filter);
```

#### Add feedback

When a barcode is found in the video stream, its location shows up directly in the video. Besides that, with the help of the SDK "Dynamsoft Camera Enhancer", we can add feedback such as a "beep" sound or a "vibration".

The following code snippet adds both for when a barcode is found:

```js
const resultReceiver = new Dynamsoft.CVR.CapturedResultReceiver();
resultReceiver.onDecodedBarcodesReceived = (result) => {
  if (result.barcodesResultItems.length > 0) {
    Dynamsoft.DCE.Feedback.beep();
    Dynamsoft.DCE.Feedback.vibrate();
  }
};
router.addResultReceiver(resultReceiver);
```

### Customize the UI

The UI is part of the auxiliary SDK "Dynamsoft Camera Enhancer", read more on how to [customize the UI](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/user-guide/index.html#customize-the-ui).

## API Documentation

You can check out the detailed documentation about the APIs of the SDK at
[https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/?ver=10.0.20](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/?ver=10.0.20).

## System Requirements

DBR requires the following features to work:

- Secure context (HTTPS deployment)

  When deploying your application / website for production, make sure to serve it via a secure HTTPS connection. This is required for two reasons
  
  - Access to the camera video stream is only granted in a security context. Most browsers impose this restriction.
  > Some browsers like Chrome may grant the access for `http://127.0.0.1` and `http://localhost` or even for pages opened directly from the local disk (`file:///...`). This can be helpful for temporary development and test.
  
  - Dynamsoft License requires a secure context to work.

- `WebAssembly`, `Blob`, `URL`/`createObjectURL`, `Web Workers`

  The above four features are required for the SDK to work.

- `MediaDevices`/`getUserMedia`

  This API is only required for in-browser video streaming. If a browser does not support this API, the [Single Frame Mode](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/BarcodeScanner.html?ver=10.0.20&utm_source=guide#singleframemode) will be used automatically. If the API exists but doesn't work correctly, the Single Frame Mode can be used as an alternative way to access the camera.

- `getSettings`

  This API inspects the video input which is a `MediaStreamTrack` object about its constrainable properties.

The following table is a list of supported browsers based on the above requirements:

  |    Browser Name    |                Version                 |
  | :----------------: | :------------------------------------: |
  |       Chrome       |            v59+<sup>1</sup>            |
  |      Firefox       | v52+ (v55+ on Android/iOS<sup>1</sup>) |
  |  Edge<sup>2</sup>  |                  v16+                  |
  | Safari<sup>3</sup> |                  v11+                  |

  <sup>1</sup> iOS 14.3+ is required for camera video streaming in Chrome and Firefox or Apps using webviews.

  <sup>2</sup> On Edge, due to strict Same-origin policy, you must host the SDK files on the same domain as your web page.
  
  <sup>3</sup> Safari v11.x already has the required features, but it has many other issues, so we recommend v12+.

Apart from the browsers, the operating systems may impose some limitations of their own that could restrict the use of the SDK. Browser compatibility ultimately depends on whether the browser on that particular operating system supports the features listed above.

## How to Upgrade

If you want to upgrade the SDK from an old version to a newer one, please see [how to upgrade](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/upgrade-guide/?ver=10.0.20&utm_source=guide).

## Release Notes

Learn about what are included in each release at [https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/release-notes/?ver=latest](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/release-notes/?ver=latest).

## Next Steps

Now that you have got the SDK integrated, you can choose to move forward in the following directions

1. Check out the [Official Samples and Demo](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/samples-demos/index.html?ver=latest)
2. Learn how to make use of the [SDK features](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/user-guide/explore-features/index.html?ver=latest)
3. See how the SDK works in [Popular Use Cases](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/user-guide/use-cases/index.html?ver=latest)

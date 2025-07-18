---
layout: default-layout
title: v11.0.3000 User Guide - Dynamsoft Barcode Reader JavaScript Edition
description: This is the user guide of Dynamsoft Barcode Reader JavaScript SDK.
keywords: user guide, javascript, js
breadcrumbText: User Guide
noTitleIndex: true
needGenerateH3Content: true
needAutoGenerateSidebar: true
schema: schemas/dynamsoft-facilitates-mit-research-schema.json
---

<!--The original doc is hosted here => https://github.com/dynamsoft-docs/barcode-reader-docs-js/blob/main/programming/javascript/user-guide/index.md -->

# Barcode Reader for Your Website - User Guide

[Dynamsoft Barcode Reader JavaScript Edition](https://www.dynamsoft.com/barcode-reader/sdk-javascript/) (DBR-JS) is equipped with industry-leading algorithms for exceptional speed, accuracy and read rates in barcode reading. Using its well-designed API, you can turn your web page into a barcode scanner with just a few lines of code. Once the DBR-JS SDK gets integrated into your web page, your users can access a camera via the browser and read barcodes directly from its video input.

<!-- ![version](https://img.shields.io/npm/v/dynamsoft-barcode-reader.svg)
![downloads](https://img.shields.io/npm/dm/dynamsoft-barcode-reader.svg)
![jsdelivr](https://img.shields.io/jsdelivr/npm/hm/dynamsoft-barcode-reader.svg)

![version](https://img.shields.io/npm/v/dynamsoft-javascript-barcode.svg)
![downloads](https://img.shields.io/npm/dm/dynamsoft-javascript-barcode.svg)
![jsdelivr](https://img.shields.io/jsdelivr/npm/hm/dynamsoft-javascript-barcode.svg) -->

In this guide, you will learn step by step on how to integrate the DBR-JS SDK into your website.

<span style="font-size:20px">Table of Contents</span>

- [Barcode Reader for Your Website - User Guide](#barcode-reader-for-your-website---user-guide)
  - [Hello World - Simplest Implementation](#hello-world---simplest-implementation)
    - [Understand the code](#understand-the-code)
      - [About the code](#about-the-code)
    - [Run the example](#run-the-example)
  - [Preparing the SDK](#preparing-the-sdk)
    - [Step 1: Include the SDK](#step-1-include-the-sdk)
    - [Step 2: Prepare the SDK](#step-2-prepare-the-sdk)
      - [1. Specify the license](#1-specify-the-license)
      - [2. \[Optional\] Specify the location of the "engine" files](#2-optional-specify-the-location-of-the-engine-files)
  - [Using the SDK](#using-the-sdk)
    - [Step 1: Preload the module](#step-1-preload-the-module)
    - [Step 2: Create a CaptureVisionRouter object](#step-2-create-a-capturevisionrouter-object)
    - [Step 3: Connect an image source](#step-3-connect-an-image-source)
    - [Step 4: Register a result receiver](#step-4-register-a-result-receiver)
    - [Step 5: Start process video frames](#step-5-start-process-video-frames)
  - [Customizing the process](#customizing-the-process)
    - [1. Adjust the preset template settings](#1-adjust-the-preset-template-settings)
      - [1.1. Change barcode settings](#11-change-barcode-settings)
      - [1.2. Retrieve the original image](#12-retrieve-the-original-image)
      - [1.3. Change reading frequency to save power](#13-change-reading-frequency-to-save-power)
      - [1.4. Specify a scan region](#14-specify-a-scan-region)
    - [2. Edit the preset templates directly](#2-edit-the-preset-templates-directly)
    - [3. \[Important\] Filter the results](#3-important-filter-the-results)
      - [Method 1: Verify results across multiple frames](#method-1-verify-results-across-multiple-frames)
      - [Method 2: Eliminate redundant results detected within a short time frame](#method-2-eliminate-redundant-results-detected-within-a-short-time-frame)
    - [4. Add feedback](#4-add-feedback)
  - [Customizing the UI](#customizing-the-ui)
  - [Documentation](#documentation)
    - [API Reference](#api-reference)
    - [How to Upgrade](#how-to-upgrade)
    - [Release Notes](#release-notes)
  - [Next Steps](#next-steps)

**Popular Examples**

- Hello World - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v11.0.30/foundational-api-samples/hello-world/hello-world.html) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/foundational-api-samples/hello-world/hello-world.html?ver=11.0.30&utm_source=guide)
- Angular App - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v11.0.30/foundational-api-samples/hello-world/angular)
- React App - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v11.0.30/foundational-api-samples/hello-world/react)
- Vue App - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v11.0.30/foundational-api-samples/hello-world/vue)
- PWA App - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v11.0.30/foundational-api-samples/hello-world/pwa) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/foundational-api-samples/hello-world/pwa/helloworld-pwa.html?ver=11.0.30&utm_source=guide)
- WebView in Android and iOS - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/v11.0.30/foundational-api-samples/hello-world/webview)
- Read Driver Licenses - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v11.0.30/foundational-api-samples/use-case/read-a-drivers-license/index.html) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/foundational-api-samples/use-case/read-a-drivers-license/index.html?ver=11.0.30&utm_source=guide)
- Fill A Form - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v11.0.30/foundational-api-samples/use-case/fill-a-form-with-barcode-reading.html) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/foundational-api-samples/use-case/fill-a-form-with-barcode-reading.html?ver=11.0.30&utm_source=guide)
- Show result information on the video - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v11.0.30/foundational-api-samples/use-case/show-result-texts-on-the-video.html) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/foundational-api-samples/use-case/show-result-texts-on-the-video.html?ver=11.0.30&utm_source=guide)
- Debug Camera and Collect Video Frame - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v11.0.30/foundational-api-samples/others/debug)

You can also:

- Try the Official Demo - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-demo/) \| [Run](https://demo.dynamsoft.com/barcode-reader-js/?ver=11.0.30&utm_source=guide)
- Try Online Examples - [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/v11.0.30/)

## Hello World - Simplest Implementation

Let's start with the "Hello World" example of the DBR-JS SDK which demonstrates how to use the minimum code to enable a web page to read barcodes from a live video stream.  

**Basic Requirements**

  - Internet connection
  - A supported browser
  - Camera access

> Please refer to [system requirements](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/faq/system-requirement.html) for more details.

### Understand the code

The complete code of the "Hello World" example is shown below

```html
<!DOCTYPE html>
<html>
<body>
<div id="camera-view-container" style="width: 100%; height: 60vh"></div>
<textarea id="results" style="width: 100%; min-height: 10vh; font-size: 3vmin; overflow: auto" disabled></textarea>
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader-bundle@11.0.3000/dist/dbr.bundle.js"></script>
<script>
  Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");
  Dynamsoft.Core.CoreModule.loadWasm();
  (async () => {
    let cvRouter = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();

    let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
    let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView);
    document.querySelector("#camera-view-container").append(cameraView.getUIElement());
    cvRouter.setInput(cameraEnhancer);

    const resultsContainer = document.querySelector("#results");
    cvRouter.addResultReceiver({ onCapturedResultReceived: (result) => {
      if (result.barcodeResultItems?.length) {
        resultsContainer.textContent = '';
        for (let item of result.barcodeResultItems) {
          resultsContainer.textContent += `${item.formatString}: ${item.text}\n\n`;
        }
      }
    }});

    let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
    filter.enableResultCrossVerification("barcode", true);
    filter.enableResultDeduplication("barcode", true);
    await cvRouter.addResultFilter(filter);

    await cameraEnhancer.open();
    await cvRouter.startCapturing("ReadSingleBarcode");
  })();
</script>
</body>
</html>
```

<!--TOM: Update the code links-->

<p align="center" style="text-align:center; white-space: normal; ">
  <a target="_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/v11.0.30/foundational-api-samples/hello-world/hello-world.html" title="Code in Github" style="text-decoration:none;">
    <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/github.svg" alt="Code in Github" width="20" height="20" style="width:20px;height:20px;">
  </a>
  &nbsp;
  <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/csm2f9wb/" title="Run via JSFiddle" style="text-decoration:none;">
    <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/jsfiddle.svg" alt="Run via JSFiddle" width="20" height="20" style="width:20px;height:20px;" >
  </a>
  &nbsp;
  <a target="_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/foundational-api-samples/hello-world/hello-world.html?ver=11.0.30&utm_source=guide" title="Run in Dynamsoft" style="text-decoration:none;">
    <img src="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/svgs/solid/circle-play.svg" alt="Run in Dynamsoft" width="20" height="20" style="width:20px;height:20px;">
  </a>
</p>

> Don't want to deal with too many details? You can get a quick start with the [BarcodeScanner >>](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/user-guide/barcode-scanner.html)
> ```js
> // Scan instantly with a single line of code!
> new Dynamsoft.BarcodeScanner().launch().then(result=>alert(result.barcodeResults[0].text));
> ```

-----

#### About the code

- `Dynamsoft.License.LicenseManager.initLicense()`: This method initializes the license for using the SDK in the application. Note that the string "**DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9**" used in this example points to an online license that requires a network connection to work. Read more on [Specify the license](#1-specify-the-license).

- `Dynamsoft.Core.CoreModule.loadWasm(["dbr"])`: This is an optional code. Used to load wasm resources in advance, reducing latency between video playing and barcode decoding.

- `Dynamsoft.CVR.CaptureVisionRouter.createInstance()`: This method creates a `CaptureVisionRouter` object `cvRouter` which controls the entire process in three steps:
  - **Retrieve Images from the Image Source**
    - `cvRouter` connects to the image source through the [ImageSourceAdapter](https://www.dynamsoft.com/capture-vision/docs/core/architecture/input.html#image-source-adapter?lang=js) interface with the method `setInput()`.
      ```js
      cvRouter.setInput(cameraEnhancer);
      ```
    > The image source in our case is a [CameraEnhancer](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/user-guide/index.html) object created with `Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView)`
  - **Coordinate Image-Processing Tasks**
    - The coordination happens behind the scenes. `cvRouter` starts the process by specifying a preset template "ReadSingleBarcode" in the method `startCapturing()`.
      ```js
      cvRouter.startCapturing("ReadSingleBarcode");
      ```
  - **Dispatch Results to Listening Objects**
    - The processing results are returned through the [CapturedResultReceiver](https://www.dynamsoft.com/capture-vision/docs/core/architecture/output.html#captured-result-receiver?lang=js) interface. The `CapturedResultReceiver` object is registered to `cvRouter` via the method `addResultReceiver()`. For more information, please check out [Register a result receiver](#step-4-register-a-result-receiver).
      ```js
      cvRouter.addResultReceiver({/*The-CapturedResultReceiver-Object"*/});
      ```
    - Also note that reading from video is extremely fast and there could be many duplicate results. We can use a [filter](#3-important-filter-the-results) with result deduplication enabled to filter out the duplicate results. The object is registered to `cvRouter` via the method `addResultFilter()`.
      ```js
      cvRouter.addResultFilter(filter);
      ```

> Read more on [Capture Vision Router](https://www.dynamsoft.com/capture-vision/docs/core/architecture/#capture-vision-router).

### Run the example

You can run the example deployed to [the Dynamsoft Demo Server](https://demo.dynamsoft.com/Samples/DBR/JS/hello-world/hello-world.html?ver=11.0.30&utm_source=guide) or test it with [JSFiddle code editor](https://jsfiddle.net/DynamsoftTeam/csm2f9wb/). 

You will be asked to allow access to your camera, after which the video will be displayed on the page. After that, you can point the camera at a barcode to read it.

When a barcode is decoded, you will see the result text show up under the video and the barcode location will be highlighted in the video feed.

Alternatively, you can test locally by copying and pasting the code shown above into a local file (e.g. "hello-world.html") and opening it in your browser.

> *Secure Contexts*:
>
> If you open the web page as `http://` , our SDK may not work correctly because the [MediaDevices: getUserMedia()](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia) and other methods only work in [secure contexts](https://developer.mozilla.org/en-US/docs/Web/Security/Secure_Contexts) (HTTPS, `localhost`, `127.0.0.1`, `file://`), in some or all supporting browsers.
>
> Regarding configuring https on your server, these guides for [nginx](https://nginx.org/en/docs/http/configuring_https_servers.html) / [IIS](https://aboutssl.org/how-to-create-a-self-signed-certificate-in-iis/) / [tomcat](https://dzone.com/articles/setting-ssl-tomcat-5-minutes) / [nodejs](https://nodejs.org/docs/v0.4.1/api/tls.html) might help.
>
> If the test doesn't go as expected, you can [contact us](https://www.dynamsoft.com/company/contact/?ver=11.0.30&utm_source=guide&product=dbr&package=js).

## Preparing the SDK

### Step 1: Include the SDK

<div class="multi-panel-switching-prefix"></div>
<!-- 
- [Use a public CDN](#useapubliccdn)
- [Host the SDK yourself](#hostthesdkyourself) -->

<div class="multi-panel-start"></div>
<div class="multi-panel-title">Use a public CDN</div>

The simplest way to include the SDK is to use either the [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/) CDN. The "hello world" example above uses **jsDelivr**.

- jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader-bundle@11.0.3000/dist/dbr.bundle.js"></script>
  ```

- UNPKG

  ```html
  <script src="https://unpkg.com/dynamsoft-barcode-reader-bundle@11.0.3000/dist/dbr.bundle.js"></script>
  ```

<!-- - In some rare cases (such as some restricted areas), you might not be able to access the CDN. If this happens, you can use the following files for the test.

  ```html
  <script src="https://download2.dynamsoft.com/packages/dynamsoft-barcode-reader-bundle@11.0.3000/dist/dbr.bundle.js"></script>
  ```

  However, please **DO NOT** use `download2.dynamsoft.com` resources in a production application as they are for temporary testing purposes only. Instead, you can try hosting the SDK yourself. -->

- In frameworks like React, Vue and Angular, you may want to add the package as a dependency.

  ```sh
  npm i dynamsoft-barcode-reader-bundle@11.0.3000 -E
  # or
  yarn add dynamsoft-barcode-reader-bundle@11.0.3000 -E
  ```

  NOTE that in frameworks, you need to [specify the location of the engine files](#2-optional-specify-the-location-of-the-engine-files).
<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>
<div class="multi-panel-title">Host the SDK yourself</div>

Besides using the public CDN, you can also download the SDK and host its files on your own server or a commercial CDN before including it in your application.

- From the website

  [Download Dynamsoft Barcode Reader JavaScript Package](https://www.dynamsoft.com/barcode-reader/downloads/?ver=11.0.30&utm_source=guide&product=dbr&package=js)

  The resources are located at path `dynamsoft/distributables/<pkg>@<version>`.

- From npm

  ```sh
  npm i dynamsoft-barcode-reader-bundle@11.0.3000 -E
  # Compared with using CDN, you need to set up more resources.
  npm i dynamsoft-capture-vision-std@1.4.21 -E
  npm i dynamsoft-image-processing@2.4.31 -E
  ```

  The resources are located at the path `node_modules/<pkg>`, without `@<version>`. You must copy "dynamsoft-xxx" packages elsewhere and add `@<version>`. The `<version>` can be obtained from `package.json` of each package. Another thing to do is to [specify the engineResourcePaths](#2-optional-specify-the-location-of-the-engine-files) so that the SDK can correctly locate the resources.
  > Since "node_modules" is reserved for Node.js dependencies, and in our case the package is used only as static resources, we recommend either renaming the "node_modules" folder or moving the "dynamsoft-" packages to a dedicated folder for static resources in your project to facilitate self-hosting.

You can typically include SDK like this:

```html
<script src="path/to/dynamsoft-barcode-reader-bundle@11.0.3000/dist/dbr.bundle.js"></script>
```
<div class="multi-panel-end"></div>

<div class="multi-panel-switching-end"></div>

*Note*:

* Certain legacy web application servers may lack support for the `application/wasm` mimetype for .wasm files. To address this, you have two options:
  1. Upgrade your web application server to one that supports the `application/wasm` mimetype.
  2. Manually define the mimetype on your server. You can refer to the guides for [apache](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Apache_Configuration_htaccess#media_types_and_character_encodings) / [IIS](https://docs.microsoft.com/en-us/iis/configuration/system.webserver/staticcontent/mimemap) / [nginx](https://www.nginx.com/resources/wiki/start/topics/examples/full/#mime-types).

* To work properly, the SDK requires a few engine files, which are relatively large and may take quite a few seconds to download. We recommend that you set a longer cache time for these engine files, to maximize the performance of your web application.

  ```
  Cache-Control: max-age=31536000
  ```

  Reference: [Cache-Control](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control).

### Step 2: Prepare the SDK

Before using the SDK, you need to configure a few things.

#### 1. Specify the license

To enable the SDK's functionality, you must provide a valid license. Utilize the API function initLicense to set your license key.

```javascript
Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");
```

As previously stated, the key "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" serves as a test license valid for 24 hours, applicable to any newly authorized browser. To test the SDK further, you can request a 30-day free trial license via the <a href="https://www.dynamsoft.com/customer/license/trialLicense?ver=11.0.30&utm_source=guide&product=dbr&package=js" target="_blank">Request a Trial License</a> link.

> Upon registering a Dynamsoft account and obtaining the SDK package from the official website, Dynamsoft will automatically create a 30-day free trial license and embed the corresponding license key into all the provided SDK samples.

#### 2. [Optional] Specify the location of the "engine" files

This step is generally necessary when utilizing frameworks such as Angular, React, Vue, or when managing the hosting of resource files yourself.

The purpose is to tell the SDK where to find the engine files (\*.worker.js, \*.wasm.js and \*.wasm, etc.).

```ts
// in framework
import { CoreModule } from "dynamsoft-barcode-reader-bundle";
CoreModule.engineResourcePaths.rootDirectory = "https://cdn.jsdelivr.net/npm/";
```
```js
// in pure js
Dynamsoft.Core.CoreModule.engineResourcePaths.rootDirectory = "https://cdn.jsdelivr.net/npm/";
```
These code uses the jsDelivr CDN as an example, feel free to change it to your own location.

## Using the SDK

### Step 1: Preload the module

The image processing logic is encapsulated within .wasm library files, and these files may require some time for downloading. To enhance the speed, we advise utilizing the following method to preload the libraries.

```js
// Preload the .wasm files
await Dynamsoft.Core.CoreModule.loadWasm(["dbr"]);
```

### Step 2: Create a CaptureVisionRouter object

To use the SDK, we first create a `CaptureVisionRouter` object.

```javascript
Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");

let cvRouter = null;
try {
    cvRouter = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
} catch (ex) {
    console.error(ex);
}
```

*Tip*:

When creating a `CaptureVisionRouter` object within a function which may be called more than once, it's best to use a "helper" variable to avoid double creation such as `pCvRouter` in the following code:

```javascript
Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");

let pCvRouter = null; // The helper variable which is a promise of cvRouter
let cvRouter = null;

document.getElementById('btn-scan').addEventListener('click', async () => {
    try {
        cvRouter = await (pCvRouter = pCvRouter || Dynamsoft.CVR.CaptureVisionRouter.createInstance());
    } catch (ex) {
        console.error(ex);
    }
});
```

### Step 3: Connect an image source

The `CaptureVisionRouter` object, denoted as `cvRouter`, is responsible for handling images provided by an image source. In our scenario, we aim to detect barcodes directly from a live video stream. To facilitate this, we initialize a `CameraEnhancer` object, identified as `cameraEnhancer`, which is specifically designed to capture image frames from the video feed and subsequently forward them to `cvRouter`.

To enable video streaming on the webpage, we create a `CameraView` object referred to as `cameraView`, which is then passed to `cameraEnhancer`, and its content is displayed on the webpage.

```html
<div id="camera-view-container" style="width: 100%; height: 100vh"></div>
```

```javascript
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView);
document.querySelector("#camera-view-container").append(cameraView.getUIElement());
cvRouter.setInput(cameraEnhancer);
```

### Step 4: Register a result receiver

Once the image processing is complete, the results are sent to all the registered `CapturedResultReceiver` objects. Each `CapturedResultReceiver` object may encompass one or multiple callback functions associated with various result types. This time we use `onCapturedResultReceived`:
<!--In our particular case, our focus is on identifying barcodes within the images, so it's sufficient to define the callback function `onDecodedBarcodesReceived`:-->

```javascript
const resultsContainer = document.querySelector("#results");
const resultReceiver = new Dynamsoft.CVR.CapturedResultReceiver();
resultReceiver.onCapturedResultReceived = (result) => {
  if (result.barcodeResultItems?.length) {
    resultsContainer.textContent = '';
    for (let item of result.barcodeResultItems) {
      // In this example, the barcode results are displayed on the page below the video.
      resultsContainer.textContent += `${item.formatString}: ${item.text}\n\n`;
    }
  }
};
cvRouter.addResultReceiver(resultReceiver);
```

You can also write code like this. It is the same.

```javascript
const resultsContainer = document.querySelector("#results");
cvRouter.addResultReceiver({ onCapturedResultReceived: (result) => {
  if (result.barcodeResultItems?.length) {
    resultsContainer.textContent = '';
    for (let item of result.barcodeResultItems) {
      // In this example, the barcode results are displayed on the page below the video.
      resultsContainer.textContent += `${item.formatString}: ${item.text}\n\n`;
    }
  }
}});
```

Check out [CapturedResultReceiver](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/captured-result-receiver.html) for more information.

### Step 5: Start process video frames

With the setup now complete, we can proceed to process the images in two straightforward steps:

1. Initiate the image source to commence image acquisition. In our scenario, we invoke the `open()` method on `cameraEnhancer` to initiate video streaming and simultaneously initiate the collection of images. These collected images will be dispatched to `cvRouter` as per its request.
2. Define a preset template to commence image processing. In our case, we utilize the "ReadSingleBarcode" template, specifically tailored for processing images containing a single barcode.

```javascript
await cameraEnhancer.open();
await cvRouter.startCapturing("ReadSingleBarcode");
```

*Note*:

* `cvRouter` is engineered to consistently request images from the image source.
* Various preset templates are at your disposal for barcode reading:

| Template Name                  | Function Description                                           |
| ------------------------------ | -------------------------------------------------------------- |
| **ReadBarcodes_Default**       | Scans multiple barcodes by default setting.                    |
| **ReadSingleBarcode**          | Quickly scans a single barcode.                                |
| **ReadBarcodes_SpeedFirst**    | Prioritizes speed in scanning multiple barcodes.               |
| **ReadBarcodes_ReadRateFirst** | Maximizes the number of barcodes read.                         |
| **ReadBarcodes_Balance**       | Balances speed and quantity in reading multiple barcodes.      |
| **ReadDenseBarcodes**          | Specialized in reading barcodes with high information density. |
| **ReadDistantBarcodes**        | Capable of reading barcodes from extended distances.           |

Read more on the [preset CaptureVisionTemplates](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/preset-templates.html).

## Customizing the process

### 1. Adjust the preset template settings

When making adjustments to some basic tasks, we often only need to modify [SimplifiedCaptureVisionSettings](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/interfaces/simplified-capture-vision-settings.html).

#### 1.1. Change barcode settings

The preset templates can be updated to meet different requirements. For example, the following code limits the barcode format to QR code.

```javascript
let settings = await cvRouter.getSimplifiedSettings("ReadSingleBarcode");
settings.barcodeSettings.barcodeFormatIds =
  Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE;
await cvRouter.updateSettings("ReadSingleBarcode", settings);
await cvRouter.startCapturing("ReadSingleBarcode");
```

For a list of adjustable barcode settings, check out [SimplifiedBarcodeReaderSettings](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/interfaces/simplified-barcode-reader-settings.html) and [EnumBarcodeFormat](https://www.dynamsoft.com/capture-vision/docs/core/enums/barcode-reader/barcode-format.html?lang=js&product=dbr).

#### 1.2. Retrieve the original image

Additionally, we have the option to modify the template to retrieve the original image containing the barcode.

```javascript
let settings = await cvRouter.getSimplifiedSettings("ReadSingleBarcode");
settings.capturedResultItemTypes |= 
  Dynamsoft.Core.EnumCapturedResultItemType.CRIT_ORIGINAL_IMAGE;
await cvRouter.updateSettings("ReadSingleBarcode", settings);
await cvRouter.startCapturing("ReadSingleBarcode");
```

Limit the barcode format to QR code, and retrieve the original image containing the barcode, at the same time.

```javascript
let settings = await cvRouter.getSimplifiedSettings("ReadSingleBarcode");
settings.capturedResultItemTypes = 
  Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE |
  Dynamsoft.Core.EnumCapturedResultItemType.CRIT_ORIGINAL_IMAGE;
await cvRouter.updateSettings("ReadSingleBarcode", settings);
await cvRouter.startCapturing("ReadSingleBarcode");
```

Please be aware that it is necessary to update the `CapturedResultReceiver` object to obtain the original image. For instance:

```javascript
const EnumCRIT = Dynamsoft.Core.EnumCapturedResultItemType;
resultReceiver.onCapturedResultReceived = (result) => {
  if (result.barcodeResultItems?.length) {
    // Use a filter to get the image on which barcodes are found.
    let image = result.items.filter(
      item => item.type === EnumCRIT.CRIT_ORIGINAL_IMAGE
    )[0].imageData;
  }
};
```

#### 1.3. Change reading frequency to save power

The SDK is initially configured to process images sequentially without any breaks. Although this setup maximizes performance, it can lead to elevated power consumption, potentially causing the device to overheat. In many cases, it's possible to reduce the reading speed while still satisfying business requirements. The following code snippet illustrates how to adjust the SDK to process an image every 500 milliseconds:

> Please bear in mind that in the following code, if an image's processing time is shorter than 500 milliseconds, the SDK will wait for the full 500 milliseconds before proceeding to process the next image. Conversely, if an image's processing time exceeds 500 milliseconds, the subsequent image will be processed immediately upon completion.

```javascript
let settings = await cvRouter.getSimplifiedSettings("ReadSingleBarcode");
settings.minImageCaptureInterval = 500;
await cvRouter.updateSettings("ReadSingleBarcode", settings);
await cvRouter.startCapturing("ReadSingleBarcode");
```

#### 1.4. Specify a scan region

We can specify a scan region to allow the SDK to process only part of the image, improving processing speed. The code snippet below demonstrates how to do this using the `cameraEnhancer` image source.

```javascript
cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView);
// In this example, we set the scan region to cover the central 25% of the image.
cameraEnhancer.setScanRegion({
  x: 25,
  y: 25,
  width: 50,
  height: 50,
  isMeasuredInPercentage: true,
});
```

*Note*:

1. By configuring the region at the image source, images are cropped before processing, removing the need to adjust any further processing settings.
2. `cameraEnhancer` enhances interactivity by overlaying a mask on the video, clearly marking the scanning region.

*See Also*:

[CameraEnhancer::setScanRegion](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/acquisition.html#setscanregion)

<!-- Since DCE is always used, no need to use this approach


You can use the parameter `roi` (region of interest) together with the parameter `roiMeasuredInPercentage` to configure the SDK to only read a specific region on the image frames. For example, the following code limits the reading in the center 25%( = 50% * 50%) of the image frames:

```javascript
let settings = await cvRouter.getSimplifiedSettings("ReadSingleBarcode");
settings.roiMeasuredInPercentage = true;
settings.roi.points = [
  { x: 25, y: 25 },
  { x: 75, y: 25 },
  { x: 75, y: 75 },
  { x: 25, y: 75 },
];
await cvRouter.updateSettings("ReadSingleBarcode", settings);
await cvRouter.startCapturing("ReadSingleBarcode");
``` -->


<!--
* Specify the maximum time allowed for processing each image

You can set the maximum time allowed for processing a single image with the property `timeout`.

> Please be aware that the SDK will cease processing an image if its processing time exceeds the duration specified by the `timeout` parameter. It should not be confused with the previously discussed parameter, `minImageCaptureInterval`.

```javascript
let settings = await cvRouter.getSimplifiedSettings("ReadSingleBarcode");
settings.timeout = 500;
await cvRouter.updateSettings("ReadSingleBarcode", settings);
await cvRouter.startCapturing("ReadSingleBarcode");
```
-->

### 2. Edit the preset templates directly

The preset templates have many more settings that can be customized to suit your use case best. If you [download the SDK from Dynamsoft website](https://www.dynamsoft.com/barcode-reader/downloads/1000003-confirmation/), you can find the templates under

* "/dynamsoft-barcode-reader-js-11.0.3000/dynamsoft/templates/"

Upon completing the template editing, you can invoke the `initSettings` method and provide it with the template path as an argument.

```javascript
await cvRouter.initSettings("PATH-TO-THE-FILE"); // E.g. "https://your-website/ReadSingleBarcode.json")
await cvRouter.startCapturing("ReadSingleBarcode"); // Make sure the name matches one of the CaptureVisionTemplates in the template JSON file.
```

### 3. [Important] Filter the results

When processing video frames, the same barcode is often detected multiple times. To improve the user experience, we can use the [MultiFrameResultCrossFilter](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/utility/multi-frame-result-cross-filter.html) object. This object provides two methods for handling duplicate detections, which can be used independently or together, depending on what best suits your application needs:

#### Method 1: Verify results across multiple frames

```js
let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
filter.enableResultCrossVerification("barcode", true);
await cvRouter.addResultFilter(filter);
```

*Note*:

* `enableResultCrossVerification` was designed to cross-validate the outcomes across various frames in a video streaming scenario, enhancing the reliability of the final results. This validation is particularly crucial for barcodes with limited error correction capabilities, such as 1D codes.

#### Method 2: Eliminate redundant results detected within a short time frame

```js
let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
filter.enableResultDeduplication("barcode", true);
await cvRouter.addResultFilter(filter);
```

*Note*:

* `enableResultDeduplication` was designed to prevent high usage in video streaming scenarios, addressing the repetitive processing of the same code within a short period of time.

Initially, the filter is set to forget a result 3 seconds after it is first received. During this time frame, if an identical result appears, it is ignored.

> It's important to know that in version 9.x or earlier, the occurrence of an identical result would reset the timer, thus reinitiating the 3-second count at that point. However, in version 10.2.10 and later, an identical result no longer resets the timer but is instead disregarded, and the duration count continues uninterrupted.

Under certain circumstances, this duration can be extended with the method `setDuplicateForgetTime()`.

```js
let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
filter.setDuplicateForgetTime(5000); // Extend the duration to 5 seconds.
await cvRouter.addResultFilter(filter);
```

You can also enable both options at the same time:

```js
let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
filter.enableResultCrossVerification("barcode", true);
filter.enableResultDeduplication("barcode", true);
filter.setDuplicateForgetTime(5000);
await cvRouter.addResultFilter(filter);
```

### 4. Add feedback

When a barcode is detected within the video stream, its position is immediately displayed within the video. Furthermore, utilizing the "Dynamsoft Camera Enhancer" SDK, we can introduce feedback mechanisms, such as emitting a "beep" sound or triggering a "vibration".

The following code snippet adds a "beep" sound for when a barcode is found:

```js
const resultReceiver = new Dynamsoft.CVR.CapturedResultReceiver();
resultReceiver.onDecodedBarcodesReceived = (result) => {
  if (result.barcodeResultItems.length > 0) {
    Dynamsoft.DCE.Feedback.beep();
  }
};
cvRouter.addResultReceiver(resultReceiver);
```

## Customizing the UI

```javascript
// Create a CameraView instance with default settings
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
// Create a CameraView instance with a specified HTML file path, typically a local or remote URL
let cameraView1 = await Dynamsoft.DCE.CameraView.createInstance('@engineResourcePath/dce.mobile-native.ui.html');
// Create a CameraView instance within a specified DOM element
let cameraView2 = await Dynamsoft.DCE.CameraView.createInstance(document.getElementById('my-ui'));
// Create a CameraView instance using a custom UI file path
let cameraView3 = await Dynamsoft.DCE.CameraView.createInstance('url/to/my/ui.html');

// Get the UI element associated with the cameraView instance
let uiElement = cameraView.getUIElement();
// Remove the camera selection dropdown from the CameraView's UI element
uiElement.shadowRoot.querySelector('.dce-sel-camera').remove();
// Remove the resolution selection dropdown from the CameraView's UI element
uiElement.shadowRoot.querySelector('.dce-sel-resolution').remove();
```

The UI is part of the auxiliary SDK "Dynamsoft Camera Enhancer", read more on how to [customize the UI](https://www.dynamsoft.com/barcode-reader/docs/core/programming/features/ui-customization-js.html?lang=js).

## Documentation

### API Reference

You can check out the detailed documentation about the APIs of the SDK at
[https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/?ver=11.0.3000](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/?ver=11.0.3000).

<!--  Compatibility is basically not an issue. Pls remove to another place

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

  This API is required for in-browser video streaming.

- `getSettings`

  This API inspects the video input which is a `MediaStreamTrack` object about its constrainable properties.

The following table is a list of supported browsers based on the above requirements:

  | Browser Name |     Version      |
  | :----------: | :--------------: |
  |    Chrome    | v78+<sup>1</sup> |
  |   Firefox    | v68+<sup>1</sup> |
  |     Edge     |       v79+       |
  |    Safari    |       v14+       |

  <sup>1</sup> devices running iOS needs to be on iOS 14.3+ for camera video streaming to work in Chrome, Firefox or other Apps using webviews.

Apart from the browsers, the operating systems may impose some limitations of their own that could restrict the use of the SDK. Browser compatibility ultimately depends on whether the browser on that particular operating system supports the features listed above.

-->

### How to Upgrade

If you want to upgrade the SDK from an old version to a newer one, please see [how to upgrade](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/upgrade-guide/index.html?ver=11.0.3000&utm_source=guide).

### Release Notes

Learn about what are included in each release at [https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/release-notes/index.html](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/release-notes/index.html?ver=11.0.30&utm_source=guide).

## Next Steps

Now that you have got the SDK integrated, you can choose to move forward in the following directions

1. Learn how to [Use in Framework](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/user-guide/use-in-framework.html)
2. Check out the [Official Samples and Demo](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/samples-demos/index.html?ver=11.0.30)
3. Learn about the [APIs of the SDK](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/index.html?ver=11.0.3000)

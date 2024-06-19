---
layout: default-layout
title: v10.2.10 User Guide - Dynamsoft Barcode Reader JavaScript Edition
description: This is the user guide of Dynamsoft Barcode Reader JavaScript SDK.
keywords: user guide, javascript, js
breadcrumbText: User Guide
noTitleIndex: true
needGenerateH3Content: true
needAutoGenerateSidebar: true
schema: schemas/dynamsoft-facilitates-mit-research-schema.json
---

# Use in Framework - User Guide

Using it in a framework like Angular, React, and Vue is a little different from using it natively. Here we quickly explain the common practices of integrating [Dynamsoft Barcode Reader JavaScript Edition](https://www.dynamsoft.com/barcode-reader/sdk-javascript/){:target="_blank"} (DBR-JS) into the framework.

## Install

We assume here that you already have a project using framework. You can find `package.json` in your project root directory.

Please open terminal from your project root directory. Then we can install the DBR-JS SDK.

```sh
npm i dynamsoft-barcode-reader-bundle@10.2.1000 -E
```

Check package.json and you can find these.

```json
{
  ...
  "dependencies": {
    ...
    "dynamsoft-barcode-reader-bundle": "10.2.1000"
  }
}
```

Notice there is no `^` before `10.2.1000`. No `^` means exact version, it will not automatically upgrade, even when there is no `package-lock.json`.

Although we will keep the SDK's external interface relatively stable, the SDK's internal communication often changes due to version changes, which may cause incompatibility issues with `engineResourcePaths` settings. Therefore, to avoid surprises, we need the exact version.

## Config

Next, we write the common settings related to DBR-JS into a file. Many developers use typescript, we can name it `dynamsoft.config.ts`. The `dynamsoft.config.ts` is not a component, I considered putting it in a directory like `lib`, or just root directory of `src`.

```ts
import { CoreModule } from "dynamsoft-core";
import { LicenseManager } from "dynamsoft-license";
import "dynamsoft-barcode-reader";

// Configures the paths where the .wasm files and other necessary resources for modules are located.
CoreModule.engineResourcePaths = {
  std: "https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-std@1.2.10/dist/",
  dip: "https://cdn.jsdelivr.net/npm/dynamsoft-image-processing@2.2.30/dist/",
  core: "https://cdn.jsdelivr.net/npm/dynamsoft-core@3.2.30/dist/",
  license: "https://cdn.jsdelivr.net/npm/dynamsoft-license@3.2.21/dist/",
  cvr: "https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.2.30/dist/",
  dbr: "https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader@10.2.10/dist/",
  dce: "https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.3/dist/"
};

/** LICENSE ALERT - README
 * To use the library, you need to first specify a license key using the API "initLicense()" as shown below.
 */

LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");

/**
 * You can visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=github&product=dbr&package=js to get your own trial license good for 30 days.
 * Note that if you downloaded this sample from Dynamsoft while logged in, the above license key may already be your own 30-day trial license.
 * For more information, see https://www.dynamsoft.com/barcode-reader/programming/javascript/user-guide/?ver=10.2.10&utm_source=github#specify-the-license or contact support@dynamsoft.com.
 * LICENSE ALERT - THE END
 */

// Optional. Preload "BarcodeReader" module for reading barcodes. It will save time on the initial decoding by skipping the module loading.
CoreModule.loadWasm(["DBR"]);
```

In order for these settings to take effect, `dynamsoft.config.ts` need to be imported before using the barcode reader. You can import `dynamsoft.config.ts` at the entry point of the page, like `main.ts` or app root component. Importing `dynamsoft.config.ts` in a specific subcomponent may help you achieve lazy loading component, which can save bandwidth when you don't need barcode feature.

Next we will introduce `dynamsoft.config.ts` in the specific component. Don't skip [Component Read Image](#component-read-image) even if you only need video barcode decoding.

## Component Read Image

A component's life cycle includes creation and destruction. It's hard to ensure that a component won't rebuild. Since the object of [CaptureVisionRouter](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/capture-vision-router-module.html?product=dbr&lang=javascript#capturevisionrouter-class) is associated with another [Worker](https://developer.mozilla.org/en-US/docs/Web/API/Worker), it cannot be automatically garbage collected, we need [dispose](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/instantiate.html?product=dbr&lang=javascript#dispose) it manually.

```ts
import "../../dynamsoft.config";
import { CaptureVisionRouter } from "dynamsoft-capture-vision-router";

let cvRouter;

// create before you need it
// for example, after mounting
async mounted(){
  cvRouter = await CaptureVisionRouter.createInstance();
}

// dispose when you don't need it
beforeUnmount(){
  cvRouter?.dispose();
  cvRouter = null;
}
```

In some cases, the user may click the button quickly, and your component may be destroyed quickly, even `cvRouter` haven't be created completely. We need some tricks to deal with this problem.

```ts
let pCvRouter; // promise of cvRouter

// create before you need it
// for example, after mounting
async mounted(){
  cvRouter = await (pCvRouter = CaptureVisionRouter.createInstance());
}

// dispose when you don't need it
async beforeUnmount(){
  await pCvRouter;
  cvRouter?.dispose();
  cvRouter = null;
}
```

You might read the barcode from the uploaded file.

```tsx
import { EnumCapturedResultItemType } from "dynamsoft-core";

async captureImage(e: Event){
  // Some frameworks will wrap the event. For how use wrapped event, refer to the DBR-JS samples of each framework.
  let file = e.target.files[0];
  e.target.value = '';

  let result = await cvRouter.capture(file, "ReadBarcodes_SpeedFirst");
  for (let item of result.items) {
    if(item.type !== EnumCapturedResultItemType.CRIT_BARCODE) { continue; }
    console.log(item.text); // barcode text
  }
}

// tsx as example
<input type="file" onChange={captureImage}>
```

You may want to lazy load `cvRouter` after the client uploads the file.

```ts
async captureImage(e: Event){
  cvRouter = await (pCvRouter = CaptureVisionRouter.createInstance());
  // ...
}
```

Users may upload files many times. Duplicate creation may lead to memory leaks.

```ts
async captureImage(e: Event){
  // ...
  cvRouter = await (pCvRouter = pCvRouter || CaptureVisionRouter.createInstance());
  // ...
}
```

While you are decoding, the user may switche functionality to another component. If you often write network requests, you know that this situation is very common. So the processing method is similar. Sometimes you can just ignore it, and sometimes you need to do some checks to avoid program errors.

Let's do some checks.

```ts
let bDestoried = false;

async captureImage(e: Event){
  // ...
  cvRouter = await (pCvRouter = pCvRouter || CaptureVisionRouter.createInstance());
  if(bDestoried){ return; }
  let result = await cvRouter.capture(file, "ReadBarcodes_SpeedFirst");
  if(bDestoried){ return; }
  // ...
}

// dispose when you don't need it
async beforeUnmount(){
  this.bDestoried = true;
  await pCvRouter;
  cvRouter?.dispose();
  cvRouter = null;
}
```

We add check after every `await`.

Complete code:

```tsx
import "../../dynamsoft.config";
import { CaptureVisionRouter } from "dynamsoft-capture-vision-router";

let cvRouter;
let pCvRouter; // promise of cvRouter
let bDestoried = false;

async captureImage(e: Event){
  // Some frameworks will wrap the event. For how use wrapped event, refer to the DBR-JS samples of each framework.
  let file = e.target.files[0];
  e.target.value = '';

  cvRouter = await (pCvRouter = pCvRouter || CaptureVisionRouter.createInstance());
  if(bDestoried){ return; }
  let result = await cvRouter.capture(file, "ReadBarcodes_SpeedFirst");
  if(bDestoried){ return; }
  for (let item of result.items) {
    if(item.type !== EnumCapturedResultItemType.CRIT_BARCODE) { continue; }
    console.log(item.text); // barcode text
  }
}

// dispose when you don't need it
async beforeUnmount(){
  bDestoried = true;
  await pCvRouter;
  cvRouter?.dispose();
  cvRouter = null;
}

// tsx as example
<input type="file" onChange={captureImage}>
```

> If you find it difficult to think about these, don't worry, just go to [DBR-JS samples for framework](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main/hello-world), copy these components into your project.

## Component decode video

Use the framework's methods (like #/ref/bind:this) to get the component's `HTMLDivElement`. We will render the video in it.

```tsx
let uiContainer;

<div ref={uiContainer}></div>
```

Render video UI. `cameraEnhancer`, which associated with hardware camera, also need to be [dispose](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/instantiate.html#dispose) manually.

```ts
import "../dynamsoft.config";
import { CameraEnhancer, CameraView } from "dynamsoft-camera-enhancer";

let cameraEnhancer;
let pCameraEnhancer; // promise of cameraEnhancer
let bDestoried = false;

async mount(){
    // Create a `CameraEnhancer` instance for camera control and a `CameraView` instance for UI control.
    const cameraView = await CameraView.createInstance();
    if(bDestoryed){ return; } // Check if component is destroyed after every async
    cameraEnhancer = await (pCameraEnhancer || CameraEnhancer.createInstance(cameraView));
    if(bDestoryed){ return; }

    // Get default UI and append it to DOM.
    uiContainer.append(cameraView.getUIElement());
}

async beforeUnmount(){
    bDestoried = true;
    await pCameraEnhancer;
    cameraEnhancer?.dispose();
    cameraEnhancer = null;
}
```

Add `CaptureVisionRouter`, Complete code:

```tsx
import "../dynamsoft.config";
import { CameraEnhancer, CameraView } from "dynamsoft-camera-enhancer";
import { CaptureVisionRouter } from "dynamsoft-capture-vision-router";

let uiContainer;
let cameraEnhancer;
let pCameraEnhancer; // promise of cameraEnhancer
let cvRouter;
let pCvRouter; // promise of cvRouter
let bDestoried = false;

async mount(){
  // Create a `CameraEnhancer` instance for camera control and a `CameraView` instance for UI control.
  const cameraView = await CameraView.createInstance();
  if(bDestoryed){ return; } // Check if component is destroyed after every async
  cameraEnhancer = await (pCameraEnhancer || CameraEnhancer.createInstance(cameraView));
  if(bDestoryed){ return; }

  // Get default UI and append it to DOM.
  uiContainer.append(cameraView.getUIElement());

  // Create a `CaptureVisionRouter` instance and set `CameraEnhancer` instance as its image source.
  cvRouter = await (pCvRouter || CaptureVisionRouter.createInstance());
  if(bDestoryed){ return; }
  cvRouter.setInput(cameraEnhancer);

  // Define a callback for results.
  cvRouter.addResultReceiver({ onDecodedBarcodesReceived: (result) => {
    if (!result.barcodeResultItems.length) return;
    for (let item of result.barcodeResultItems) {
      console.log(item.text)
    }
  }});

  // Filter out unchecked and duplicate results.
  const filter = new MultiFrameResultCrossFilter();
  // Filter out unchecked barcodes.
  filter.enableResultCrossVerification("barcode", true);
  // Filter out duplicate barcodes within 3 seconds.
  filter.enableResultDeduplication("barcode", true);
  await cvRouter.addResultFilter(filter);
  if(bDestoryed){ return; }

  // Open camera and start scanning single barcode.
  await cameraEnhancer.open();
  if(bDestoryed){ return; }
  await cvRouter.startCapturing("ReadSingleBarcode");
}

async beforeUnmount(){
    bDestoried = true;
    await pCvRouter;
    cvRouter?.dispose();
    cvRouter = null;
    await pCameraEnhancer;
    cameraEnhancer?.dispose();
    cameraEnhancer = null;
}

<div ref={uiContainer}></div>
```

Note that since we have taken over native rendering, do not change the UI through the framework in this component, you can change its parent component instead.

Once this component is rendered, it means that decoding will start. You can control when decoding occurs by not rendering this component at the beginning.

> Component decode video is just a little more troublesome than read image. Again, if you don't want to go into detail, please refer to the [DBR-JS samples for framework](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main/hello-world) directly.

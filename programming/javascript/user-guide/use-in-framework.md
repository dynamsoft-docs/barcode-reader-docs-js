---
layout: default-layout
title: v11.2.4000 User Guide - Use Dynamsoft Barcode Reader JavaScript Edition In Framework
description: This is the user guide to integrate Dynamsoft Barcode Reader JavaScript SDK in framework.
keywords: user guide, javascript, js, barcodes, camera, images, framework, react, angular, vue
breadcrumbText: User Guide
noTitleIndex: true
needGenerateH3Content: true
needAutoGenerateSidebar: true
schema: schemas/dynamsoft-facilitates-mit-research-schema.json
---

# Use in Framework - User Guide

Integrating [Dynamsoft Barcode Reader JavaScript Edition](https://www.dynamsoft.com/barcode-reader/sdk-javascript/) (DBR-JS) into frameworks like Angular, React, and Vue is a little different compared to native usage. This guide will quickly explain the common practices of integrating DBR-JS into these frameworks.

You can also refer to [the ready-made samples for popular frameworks](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main/frameworks) directly without reading this guide.

## Installation

Assuming you have an existing project using a framework, you should have a `package.json` file in your project's root directory.

1. Open the terminal from your project root directory.
2. Install DBR-JS SDK with the following command:

    ```sh
    npm install dynamsoft-barcode-reader-bundle@11.2.4000 -E
    ```

3. Confirm the installation by checking the `package.json`. You should see:

    ```json
    {
      ...
      "dependencies": {
        ...
        "dynamsoft-barcode-reader-bundle": "11.2.4000"
      }
    }
    ```

Notice that there is no `^` before `11.2.4000`. No `^` indicates an exact version, ensuring stability and avoids automatic upgrades even without `package-lock.json`.

While we keep the SDK's external interface relatively stable, the SDK's internal communication often change with each new version. These changes can potentially lead to compatibility issues with `engineResourcePaths` settings. To prevent any unexpected difficulties and surprises, it's essential to use the exact version of the SDK.

## Configuration

Next, we'll create a Configuration file for the common settings related to DBR-JS. If you use TypeScript, we can name the file `dynamsoft.config.ts`. This file is not a component, so you can place it under the `lib` directory or the root directory of `src`.

```ts
import { CoreModule } from "dynamsoft-core";
import { LicenseManager } from "dynamsoft-license";
import "dynamsoft-barcode-reader";

// Configures the root path where the .wasm files and other necessary resources for modules are located.
CoreModule.engineResourcePaths.rootDirectory = "https://cdn.jsdelivr.net/npm/";

/** LICENSE ALERT - README
 * To use the library, you need to first specify a license key using the API "initLicense()" as shown below.
 */

LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");

/**
 * You can visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=github&product=dbr&package=js to get your own trial license good for 30 days.
 * Note that if you downloaded this sample from Dynamsoft while logged in, the above license key may already be your own 30-day trial license.
 * For more information, see https://www.dynamsoft.com/barcode-reader/programming/javascript/user-guide/?ver=10.5.30&utm_source=github#specify-the-license or contact support@dynamsoft.com.
 * LICENSE ALERT - THE END
 */

// Optional. Preload "BarcodeReader" module for reading barcodes. It will save time on the initial decoding by skipping the module loading.
CoreModule.loadWasm();
```

In order for these settings to take effect, `dynamsoft.config.ts` must be imported before using the barcode reader. One approach is to import this file at the entry point of the application, such as in `main.ts` or the root component. If you import `dynamsoft.config.ts` within a specific subcomponent, you can achieve lazy loading, which can save bandwidth by only loading the barcode feature when needed.

### Offline usage

In some cases, you may need to use DBR-JS in an offline environment. You can download the [DBR-JS zip](https://www.dynamsoft.com/barcode-reader/downloads/1000003-confirmation/#js) package through the link, which contains all the necessary offline resources in the `./dist` directory.

**Step 1:** Copy the `./dist` folder to your project.

**Step 2:** In `dynamsoft.config.ts`, define the `engineResourcePaths`:

```javascript
// Configures the root path where the .wasm files and other necessary resources for modules are located. Feel free to change it to your own location of these files
CoreModule.engineResourcePaths.rootDirectory = '../assets/dist';
```

> Note:
> 
> We recommend not renaming any module files within the `./dist` directory, as this may cause the rootDirectory configuration to not work properly. In such cases, you would need to define resource paths for each module individually.
> In our case the packages are used only as static resources, we recommend moving the `./dist` to a dedicated folder for static resources in your project to facilitate self-hosting.

Next, we will demonstrate how to introduce `dynamsoft.config.ts` into a specific component. Don't skip the [Component for Reading Image](#component-for-reading-image) section even if you only need video barcode decoding.

## Component for Reading Image

A component's lifecycle includes creation and destruction, making it difficult to ensure that a component won't be rebuilt. Since the [CaptureVisionRouter](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/capture-vision-router-module.html?product=dbr&lang=javascript#capturevisionrouter-class) object is associated with a [Worker](https://developer.mozilla.org/en-US/docs/Web/API/Worker), it cannot be automatically garbage collected. Therefore, we need to manually [dispose](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/instantiate.html?product=dbr&lang=javascript#dispose) of it.

```ts
import "../../dynamsoft.config";
import { CaptureVisionRouter } from "dynamsoft-capture-vision-router";

let cvRouter;

// create cvRouter before it's needed
// for example, after the component is mounted
async mounted(){
  cvRouter = await CaptureVisionRouter.createInstance();
}

// dispose cvRouter when it's no longer needed
beforeUnmount(){
  cvRouter?.dispose(); // dispose cvRouter if it exists
  cvRouter = null; // reset cvRouter to null
}
```

In scenarios where users may click the button quickly, the component might be destroyed before `cvRouter` is fully created. To handle this situation, we'll need to implement some techniques to ensure proper resource management.

Here's an improved version of the code to address this issue:

```ts
let pCvRouter; // promise of cvRouter

// create cvRouter before it's needed
// for example, after the component is mounted
async mounted(){
  cvRouter = await (pCvRouter = CaptureVisionRouter.createInstance());
}

// dispose cvRouter when it's no longer needed
async beforeUnmount(){
  await pCvRouter; // ensure cvrouter creation is complete
  cvRouter?.dispose(); // dispose cvRouter if it exists
  cvRouter = null; // reset cvRouter to null
}
```

### Reading Barcode from an Uploaded File

In some cases, you might need to read barcode from an uploaded file. Here's how to handle that in your component.

```tsx
import { EnumCapturedResultItemType } from "dynamsoft-core";

async function captureImage(e: Event){
  // Some frameworks will wrap the event. Refer to DBRJS samples of each frameworks for details
  let file = e.target.files[0];
  e.target.value = ''; // reset input

  let result = await cvRouter.capture(file, "ReadBarcodes_SpeedFirst");
  for (let item of result.items) {
    // check if captured result item is a barcode
    if(item.type !== EnumCapturedResultItemType.CRIT_BARCODE) { 
      continue; // Skip processing if the result is not a barcode
    } 
    console.log(item.text); // output the decoded barcode text
  }
}

// usage example in a tsx/jsx component
<input type="file" onChange={captureImage}>
```

### Lazy Loading `cvRouter`

To optimize resource usage, you might want to lazy load `cvRouter` only after the client uploads a file.

```ts
async captureImage(e: Event){
  // ...
  cvRouter = await (pCvRouter = CaptureVisionRouter.createInstance());
  // ...
}
```

Additionally, users may repeatedly upload files which can result in multiple instances being created, potentially causing memory leaks. Here's how we could handle this.

```ts
async captureImage(e: Event){
  // ...
  cvRouter = await (pCvRouter = pCvRouter || CaptureVisionRouter.createInstance());
  // ...
}
```

### Handling Component Destruction During Decoding

When decoding barcodes, it's common for users to switch to another component. If you're familiar with handling network requests, you know that this situation is very common.

Here's how we could handle with proper checks to avoid program errors:

```ts
let isDestroyed = false;

async captureImage(e: Event){
  // ensure cvRouter is created only once
  cvRouter = await (pCvRouter = pCvRouter || CaptureVisionRouter.createInstance());
  if(isDestroyed){ return; }
  // ...
  let result = await cvRouter.capture(file, "ReadBarcodes_SpeedFirst");
  if(isDestroyed){ return; }

}

// dispose cvRouter when it's no longer needed
async beforeUnmount(){
  isDestroyed = true;
  await pCvRouter;
  cvRouter?.dispose();
  cvRouter = null;
}
```

By adding a check for `isDestroyed` after each `await`, we can ensure that the code handles the component's potential destruction properly, avoiding errors and resource leaks.

### Complete Code Example

```tsx
import "../../dynamsoft.config";
import { CaptureVisionRouter } from "dynamsoft-capture-vision-router";

let cvRouter;
let pCvRouter; // promise of cvRouter
let isDestroyed = false;

async captureImage(e: Event){
  // Some frameworks will wrap the event. Refer to DBRJS samples of each frameworks for details
  let file = e.target.files[0];
  e.target.value = ''; // reset input

  // ensure cvRouter is created only once
  cvRouter = await (pCvRouter = pCvRouter || CaptureVisionRouter.createInstance());
  if(isDestroyed){ return; }

  let result = await cvRouter.capture(file, "ReadBarcodes_SpeedFirst");
  if(isDestroyed){ return; }

  for (let item of result.items) {
    // check if captured result item is a barcode
    if(item.type !== EnumCapturedResultItemType.CRIT_BARCODE) { 
      continue; // Skip processing if the result is not a barcode
    } 
    console.log(item.text); // output the decoded barcode text
  }
}

// dispose cvRouter when it's no longer needed
async beforeUnmount(){
  isDestroyed = true;
  await pCvRouter; // ensure cvrouter creation is complete
  cvRouter?.dispose(); // dispose cvRouter if it exists
  cvRouter = null; // reset cvRouter to null
}

// usage example in a tsx/jsx component
<input type="file" onChange={captureImage}>
```

> If you find it difficult to think about these, don't worry, just go to [DBRJS samples for framework](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main/frameworks), copy these components into your project.

## Component for Decoding Video

### Set up the video ([CameraView](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/cameraview.html)) container

To render video within a component and handle its lifecycle properly, we can use framework's methods (such as `#` or `ref` or `bind:this`) to get the component's `HTMLDivElement`. This is where the video will be rendered.

```tsx
let cameraviewContainer;

<div ref={cameraViewContainer}></div>
```

### Render the Video UI

The [`CameraEnhancer`](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/index.html) instance needs to be properly created and [disposed](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/instantiate.html#dispose) of to manage resources.

```ts
import "../dynamsoft.config";
import { CameraEnhancer, CameraView } from "dynamsoft-camera-enhancer";

let cameraEnhancer;
let pCameraEnhancer; // promise of cameraEnhancer
let isDestroyed = false;

async mount(){
  // create a `CameraEnhancer` instance for camera control and a `CameraView` instance for UI control.
  const cameraView = await CameraView.createInstance();
  if(isDestroyed){ return; } // Check if component is destroyed after every async

  cameraEnhancer = await (pCameraEnhancer || CameraEnhancer.createInstance(cameraView));
  if(isDestroyed){ return; }

  // Get default UI and append it to DOM.
  cameraViewContainer.append(cameraView.getUIElement());
}

async beforeUnmount(){
  isDestroyed = true;
  await pCameraEnhancer;
  cameraEnhancer?.dispose();
  cameraEnhancer = null;
}

// usage example in a tsx/jsx component
<div ref={cameraViewContainer}></div>
```

### Add [`CaptureVisionRouter`](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/capture-vision-router-module.html)

To complete the code, we'll include the [`CaptureVisionRouter`](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/capture-vision-router/capture-vision-router-module.html) and handle it's life cycle similarly.

```ts
import "../dynamsoft.config";
import { CameraEnhancer, CameraView } from "dynamsoft-camera-enhancer";
import { CaptureVisionRouter } from "dynamsoft-capture-vision-router";

let cameraEnhancer;
let pCameraEnhancer; // promise of cameraEnhancer
let cvRouter;
let pCvRouter; // promise of cvRouter
let isDestroyed = false;

async mount(){
  // Create a `CameraEnhancer` instance for camera control and a `CameraView` instance for UI control.
  const cameraView = await CameraView.createInstance();
  if(isDestroyed){ return; } // Check if component is destroyed after every async
  
  cameraEnhancer = await (pCameraEnhancer || CameraEnhancer.createInstance(cameraView));
  if(isDestroyed){ return; }

  // Get default UI and append it to DOM.
  cameraViewContainer.append(cameraView.getUIElement());

  // Create a `CaptureVisionRouter` instance and set `CameraEnhancer` instance as its image source.
  cvRouter = await (pCvRouter || CaptureVisionRouter.createInstance());
  if(isDestroyed){ return; }

  cvRouter.setInput(cameraEnhancer);

  // Define a callback for results.
  cvRouter.addResultReceiver({ onDecodedBarcodesReceived: (result) => {
    if (!result.barcodeResultItems.length) return;
    for (let item of result.barcodeResultItems) {
      console.log(item.text); // output the decoded barcode text
    }
  }});

  // Filter out unchecked and duplicate results.
  const filter = new MultiFrameResultCrossFilter();
  // Filter out unchecked barcodes.
  filter.enableResultCrossVerification("barcode", true);
  // Filter out duplicate barcodes within 3 seconds.
  filter.enableResultDeduplication("barcode", true);
  await cvRouter.addResultFilter(filter);
  if(isDestroyed){ return; }

  // Open camera and start scanning single barcode.
  await cameraEnhancer.open();
  if(isDestroyed){ return; }

  await cvRouter.startCapturing("ReadSingleBarcode");
}

async beforeUnmount(){
  isDestroyed = true;

  await pCvRouter;
  cvRouter?.dispose();
  cvRouter = null;

  await pCameraEnhancer;
  cameraEnhancer?.dispose();
  cameraEnhancer = null;
}

// usage example in a tsx/jsx component
<div ref={cameraViewContainer}></div>
```

### Final Notes

Decoding video is slightly more complex than reading image, but by following the steps above, you can manage resources effectively and ensure your component runs smoothly.

Again, if you don't want to go into detail, please refer to the [DBRJS sample](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main) directly.

Note that since we have taken over native rendering, avoid changing the UI through the framework within decoding video component; instead, make changes in its parent component.

Once this component is rendered, decoding will start. You can control when decoding occurs by not rendering this component until needed.

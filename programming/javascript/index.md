---
layout: default-layout
title: Introduction - Dynamsoft Barcode Reader JavaScript Edition
description: This is introduction page of Dynamsoft Barcode Reader JavaScript SDK version 10.0.20.
keywords: javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: false
breadcrumbText: JavaScript
permalink: /programming/javascript/index.html
---

# Introduction to Dynamsoft Barcode Reader JavaScript Edition version 10.x

Dynamsoft Barcode Reader (DBR) can be used in JavaScript to add barcode reading capabilities to websites running in modern browsers. It is ideal for

* Organizations who already have sophisticated websites and do not intend to develop mobile applications for the same purposes;
* Organizations whose customers have no desire to install applications for temporary usage of their services.

To get a fast start, you can

* Read the [User Guide](user-guide/)
* Try the [Samples and Demos](samples-demos/)

The following describes the highlights of DBR when used in JavaScript.

## Fast Integration

The following lines of code is all that is required to integrate DBR in JavaScript:

``` html
<!DOCTYPE html>
<html lang="en">
  <body>
    <script src="core-09281709/dist/core.js"></script>
    <script src="dynamsoft-utility@1.0.10/dist/utility.js"></script>
    <script src="dbr-0928/dist/dbr.js"></script>
    <script src="cvr-0928/dist/cvr.js"></script>
    <script src="dce-09281103/dist/dce.js"></script>
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
          alert(result.barcodesResultItems[0].text);
        };
        if (resultReceiver) router.addResultReceiver(resultReceiver);

        await cameraEnhancer.open();
        await router.startCapturing("ReadSingleBarcode");
      })();
    </script>
  </body>
</html>
```

After the integration, end users of the web page can open it in a browser, access their cameras and read barcodes directly from the video input.

### Camera Control

Customers generally need to scan a barcode on the fly at which time there is no better input than the camera hooked to or built into the device itself. As shown in the code snippet above, the product [Dynamsoft Camera Enhancer (DCE)](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/user-guide/index.html) is used to provide camera support. It makes use of the powerful **MediaDevices** interface (provided by the browser itself) to instantly access the video input of the camera, capture image frames and connect them with the back-end decoding engine.

> DBR and DCE communicate through the interface called [Image Source Adapter](https://www.dynamsoft.com/capture-vision/docs/core/architecture/input.html#image-source-adapter?lang=js).

### Interactive UI

Good interaction design is essential for a website. With the help of DCE, the barcode reading process is made interactive as shown in the screenshot below.

![Interactive UI](assets/interactive-ui.png)

## High Performance

Barcode reading is usually just an auxiliary way to assist a small step in a complex workflow. Customers like the convenience, but if it takes too long or is error-prone, their patience will quickly run out. Therefore, high performance is crucial.

### Unparalleled Speed

DBR showcases Dynamsoft's cutting-edge technology in light-speed recognition of barcodes. In most cases, an image gets deblurred, binarized and read under 100 milliseconds.

### Proficiency in Handling Difficult Environments

The actual use environment is unpredictable. The barcode may appear distorted, inverted, or partially damaged; the background may be textured or spotted; the light may be very low, and there may be shadows and glare. DBR handles all these cases with its rich image processing algorithms through various adjustable settings.

### Exceptional Accuracy

DBR does a lot of preparation work to make sure the barcode is as legible as possible for the decoding engine to read. This ensures a very high accuracy. In addition, DBR achieves even higher accuracy through the following ways:

* DBR has a confidence score for each recognition which can be used to filter unwanted results;
* In the case of continuous scanning, DBR can verify results by comparing the results of multiple consecutive recognitions.

Through many experiences, DBR has also cultivated its error correction ability to handle

* Non-standard barcodes which do not strictly abide by the specification;
* Deformed barcodes which are usually caused by improper printing.

## Next Step

Read the [User Guide](user-guide/) to start building your own websites with barcode reading capabilities.

## See Also

### API Reference

For a overview of the APIs, see the [API Reference](api-reference/).

### Release Notes

For a peek of DBR history, check the [Release Notes](release-notes/).

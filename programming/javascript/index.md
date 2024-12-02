---
layout: default-layout
title: Introduction - Dynamsoft Barcode Reader JavaScript Edition
description: This is introduction page of Dynamsoft Barcode Reader JavaScript SDK version 10.0.21.
keywords: javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: false
breadcrumbText: JavaScript
permalink: /programming/javascript/index.html
---

# Introduction to Dynamsoft Barcode Reader JavaScript Edition version 10.x

Dynamsoft Barcode Reader (DBR) can be used in JavaScript to add barcode reading capabilities to websites running in modern browsers. It is ideal for

* organizations who already have sophisticated websites and do not intend to develop mobile applications for the same purposes; or
* organizations whose customers have no desire to install applications for temporary usage of their services.

To get a fast start, you can

* read the [User Guide](user-guide/), or
* try the [Samples and Demos](samples-demos/)

The following describes the highlights of DBR JavaScript edition (DBR-JS) version 10.x.

## Fast Integration

The following lines of code is all that is required to create a web page that scans barcodes with DBR.

```html
<!DOCTYPE html>
<html>
<body>
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader-bundle@10.4.2002/dist/dbr.bundle.js"></script>
<div id="camera-view-container" style="width: 100%; height: 60vh"></div>
<textarea id="results" style="width: 100%; min-height: 10vh; font-size: 3vmin; overflow: auto" disabled></textarea>
<script>
  Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");
  Dynamsoft.Core.CoreModule.loadWasm(["dbr"]);
  (async () => {
    let cvRouter = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();

    let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
    let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView);
    document.querySelector("#camera-view-container").append(cameraView.getUIElement());
    cvRouter.setInput(cameraEnhancer);

    const resultsContainer = document.querySelector("#results");
    cvRouter.addResultReceiver({ onDecodedBarcodesReceived: (result) => {
      if (result.barcodeResultItems.length > 0) {
        resultsContainer.textContent = '';
        for (let item of result.barcodeResultItems) {
          resultsContainer.textContent += `${item.formatString}: ${item.text}\n\n`;
        }
      }
    }});

    let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
    filter.enableResultCrossVerification('barcode', true);
    filter.enableResultDeduplication('barcode', true);
    await cvRouter.addResultFilter(filter);

    await cameraEnhancer.open();
    await cvRouter.startCapturing("ReadSingleBarcode");
  })();
</script>
</body>
</html>
```

> Don't want to deal with too many details? We also have an **out-of-the-box** version:
> 
> [Easy Barcode Scanner >>](https://github.com/Dynamsoft/easy-barcode-scanner) available for your reference.
> ```js
> // Scan instantly with a single function!
> let txt = await EasyBarcodeScanner.scan();
> ```

After the integration, end users of the web page can open it in a browser, access their cameras and read barcodes directly from the video input.

### Camera Control

Customers generally need to scan a barcode on the fly at which time there is no better input than the camera hooked to or built into the device itself. As shown in the code snippet above, the product **Dynamsoft Camera Enhancer (DCE)** is used to provide camera support. It makes use of the powerful [**MediaDevices**](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices) interface (provided by the browser itself) to instantly access the video input of the camera, capture image frames and supply them to the back-end decoding engine.

> DBR and DCE communicate through the interface called [Image Source Adapter]({{ site.dcvb_architecture }}input.html#image-source-adapter?lang=js).

### Interactive UI

Good interaction design is essential for a website. With the help of DCE, the barcode reading process is made interactive as shown in the screenshot below.

![Interactive UI](assets/interactive-ui.png)

## High Performance

Barcode reading is usually just an auxiliary way to assist a small step in a complex workflow. Customers like the convenience, but if it takes too long or is error-prone, their patience will quickly run out. Therefore, high performance is crucial.

### Unparalleled Speed

DBR showcases Dynamsoft's cutting-edge technology in light-speed recognition of barcodes. In most cases, an image gets deblurred, binarized and read under 100 milliseconds.

With the help of DCE JS, DBR no longer wastes time on image capture and often gets high-quality images for processing, which further increases its speed.

### Proficiency in Handling Difficult Environments

The actual use environment is unpredictable. The barcode may appear distorted, inverted, or partially damaged; the background may be textured or spotted; the light may be very low, and there may be shadows and glare. DBR handles all these cases with its rich image processing algorithms through various adjustable settings.

### Exceptional Accuracy

DBR does a lot of preparation work to make sure the barcode is as legible as possible for the decoding engine to read. This ensures a very high accuracy. In addition, DBR achieves even higher accuracy through the following ways:

* DBR can verify results by comparing the results of multiple consecutive recognitions;
* DBR has a confidence score for each recognition which can be used to filter unwanted results;
* DBR is also able to verify the barcode result with printed text that accompanies the barcode with the help of the product **Dynamsoft Label Recognizer (DLR)**.

Through many experiences, DBR has also cultivated its error correction ability to handle

* Non-standard barcodes which do not strictly abide by the specification;
* Deformed barcodes which are usually caused by improper printing.

## Effortless Expansion

DBR-JS v10.x is based on [Dynamsoft Capture Vision]({{site.dcvb_architecture}}) which is a modular architecture. This architecture makes it easy to add new functionality or custom behavior with very little change to the code. Two examples are:

* Add **Dynamsoft Document Normalizer (DDN)** to do perspective correction before pass an image frame to read barcodes;
* Add **Dynamsoft Code Parser (DCP)** to parse the text embedded in the PDF417 on driver's licenses.

## Next Step

Read the [User Guide](user-guide/) to start building your own websites with barcode reading capabilities.

## See Also

### API Reference

For an overview of the APIs, see the [API Reference](api-reference/).

### Release Notes

For a peek of DBR-JS history, check the [Release Notes](release-notes/).

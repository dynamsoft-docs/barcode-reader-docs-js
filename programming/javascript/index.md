---
layout: default-layout
title: Introduction - Dynamsoft Barcode Reader JavaScript Edition
description: This is the main page of Dynamsoft Barcode Reader JavaScript SDK.
keywords: javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: false
breadcrumbText: JavaScript
permalink: /programming/javascript/
---

# Dynamsoft Barcode Reader JavaScript Edition

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
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode/dist/dbr.js"></script>
<script>
  // specify a license, you can visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=intro&product=dbr&package=js to get your own trial license good for 30 days. 
  Dynamsoft.DBR.BarcodeScanner.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
  (async()=>{
    let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
    scanner.onUniqueRead = (txt, result) => {
      // Do something with the "txt" found in the barcode
    };
    await scanner.show();
  })();
</script>
```

After the integration, end users of the web page can open it in a browser, access their cameras and read barcodes directly from the video input.

### Built-in Camera Control

Customers generally need to scan a barcode on the fly at which time there is no better input than the camera hooked to or built into the device itself. DBR uses the powerful **MediaDevices** interface (provided by the browser itself) to instantly connect the video input of the camera with the back-end decoding engine.

### Interactive UI

Good interaction design is essential for a website, the same is true for SDKs such as DBR. As shown in the screenshot below, DBR streams the video on the page, guides the user where to aim and highlights the areas where barcodes are found.

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
* In the case of continuous scanning, DBR compares the results of multiple consecutive recognitions and return only the results confirmed by at least two efforts.

Through many experiences, DBR has also cultivated its error correction ability against barcodes which do not strictly abide by the specification as well as deformed barcodes caused by improper printing.

## Next Step

Read the [User Guide](user-guide/) to start buidling your own websites with barcode reading capabilities.

## See Also

### API Reference

For a overview of the APIs, see the [API Reference](api-reference/).

### Release Notes

For a peek of DBR history, check the [Release Notes](release-notes/).

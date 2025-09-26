---
layout: default-layout
title: Introduction - Dynamsoft Barcode Reader JavaScript Edition
description: This is introduction page of Dynamsoft Barcode Reader JavaScript SDK version 11.
keywords: javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: JavaScript
---

# Introduction to Dynamsoft Barcode Reader JavaScript Edition version 11.x

Dynamsoft Barcode Reader (DBR) can be used in JavaScript to add barcode reading capabilities to websites running in modern browsers. It is ideal for

* organizations who already have sophisticated websites and do not intend to develop mobile applications for the same purposes; or
* organizations whose customers have no desire to install applications for temporary usage of their services.

To get a fast start, you can

* read the [User Guide](user-guide/barcode-scanner.html), or
* try the [Samples and Demos](samples-demos/)

The following describes the highlights of DBR JavaScript edition (DBR-JS) version 11.x.

# ✨BarcodeScanner – Simplified API and Built-in UI

The `BarcodeScanner` class offering a streamlined API and a prebuilt interactive UI, making barcode scanning integration easier than ever. This is now the recommended way to use DBR-JS, especially for developers who want a quick, clean, and robust scanning experience with minimal setup.

With `BarcodeScanner`, you can:

- Instantiate and configure the scanner with just a few lines of code;

- Select your scanning mode and present a ready-to-use scanning interface;

- Focus on your application logic without worrying about camera setup, UI rendering, or lifecycle management.

> [!TIP]
> You can either get a [quick start with the BarcodeScanner APIs](user-guide/barcode-scanner.html) or experience a highly customizable [development with the foundational APIs](user-guide/index.html). If you're just starting out, we highly recommend using the `BarcodeScanner` class for the best balance of simplicity, performance, and user experience.

---

## Fast Integration

This [JSFiddle example](https://jsfiddle.net/DynamsoftTeam/gcqjf5r7/) demonstrates all the code needed to build a web application using `BarcodeScanner`, end users of the web page can open it in a browser, access their cameras and read barcodes directly from the video input.

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

DBR-JS v11.x is based on [Dynamsoft Capture Vision]({{site.dcvb_architecture}}) which is a modular architecture. This architecture makes it easy to add new functionality or custom behavior with very little change to the code. Two examples are:

* Add **Dynamsoft Document Normalizer (DDN)** to do perspective correction before pass an image frame to read barcodes;
* Add **Dynamsoft Code Parser (DCP)** to parse the text embedded in the PDF417 on driver's licenses.

## Next Step

Read the [User Guide](user-guide/barcode-scanner.html) to start building your own websites with barcode reading capabilities.

## See Also

### API Reference

For an overview of the APIs, see the [API Reference](api-reference/barcode-scanner.html).

### Release Notes

For a peek of DBR-JS history, check the [Release Notes](release-notes/).

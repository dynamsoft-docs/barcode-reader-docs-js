---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - Main Page
description: This is the main page of Dynamsoft Barcode Reader JavaScript SDK.
keywords: javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: JavaScript
---

# Dynamsoft Barcode Reader for JavaScript - Introduction

This edition of the Dynamsoft Barcode Reader (hereafter called “the library”) is designed for adding barcode reading capabilities to websites. Based on JavaScript and WebAssembly, the library supports all major modern browsers including Chrome, Firefox, Safari, etc. across all mainstream desktop and mobile operating systems such as Windows, macOS, Linux, Android, iOS, etc.

Dynamsoft carefully designed the APIs of the library so that a novice developer can integrate it into a website with just a few lines of code. The seamless integration of the library means that end users feel little difference when using a page that has incorporated it.

With the library integrated, end users can open the web page in a browser, access their cameras and read barcodes directly from the video input.

## Shortcuts

* For a fast start, read the [User Guide](user-guide/).
* For a overview of the APIs, see the [API Reference](api-reference/).
* For a peek of the library history, check the [Release Notes](release-notes/).
* Interested to acquire a license? Visit our <a href="https://www.dynamsoft.com/store/dynamsoft-barcode-reader/#JavaScript" target="_blank">Online Store</a>.

## Key Features

### Scan Barcodes in the Browser

The library is based on JavaScript & WebAssembly. Both technologies are natively supported by modern browsers across all mainstream platforms. Therefore, to enable your users to scan barcodes, you only need to integrate the library onto one of your web pages and they can just open the page in a browser on a device they usually use to do it. No installation is required and no hassle.

### Built-in Camera Control

In the workflow of your application, your users normally need to scan a barcode on the fly at which time there is no better input than the camera hooked to or built into the device itself. The library uses the powerful **MediaDevices** interface (provided by the browser itself) to instantly connect the video input of the camera with the back-end decoding engine. Easy-peasy!

What if you do not have a camera? No worries! The library also covers this and has built-in support for static image decoding.

### Interactive UI

Dynamsoft understands that good interaction design is essential for a website, therefore, we built interaction into the genes of the library. Apart from showing the video input on the page, the library can also show a dedicated region in the video to guide users where to aim. Then once a barcode is found, the library lets the user know by highlighting that area as well as giving out a beep sound or vibration.

### Unparalleled Speed

The library showcases Dynamsoft’s cutting-edge technology in light-speed locating of barcodes. An image gets deblurred, binarized and scanned in milliseconds and the found region(s) of interest enters the next phase to get decoded. With its rich image processing algorithms, the library optimizes the image greatly so that the decoding process only needs to handle already-legible barcodes which can be done in no time.

### Exceptional Accuracy

Since the barcodes are already legible when they are decoded, accuracy is assured. Of course, a barcode may not strictly abide by the specification and some barcodes become deformed with improper printing. When this happens, the library’s error correction ability cultivated through many experiences can step in and save the situation.

The library also has a confidence score for each recognition which can be used to filter unwanted results and in turn further improves accuracy.
Last but not least, in the case of continuous scanning, the library can compare the results of multiple consecutive recognitions and return only the results that have been confirmed by at least two efforts.

### Proficiency in Handling Difficult Environments

The actual use environment is unpredictable. The barcode may appear distorted, inverted, or partially damaged; the background may be textured or spotted; the light may be very low, and there may be shadows and glare. But no problem! The library covers all these cases with various adjustable settings. One way or another, it gets the job done.

## Usage Scenarios

The library is designed for websites. When end users of your website browse to a page that requires the data encoded in a barcode as an input, they can open the camera on the device to stream the video on the page, locate the barcode and get the data right away.

### Retail

Most if not all products on the market now have barcodes on their packaging. The barcode can be used as a simple way to uniquely identify the product. With barcode reading capability integrated into your website, your customers (who probably prefer just opening a website temporarily instead of having to install an app) can scan a product to place an order, register a product for post-sales service or just trace the product to its origin.

### ID Scanning

All driver’s licenses issued in the USA and Canada by the American Association of Motor Vehicle Administrators (AAMVA) have a PDF417 Barcode on the back of card. The information encoded in the Barcode follows the DL/ID Card Design Standard (CDS) and can be easily parsed to meaningful form fields.

Other ID cards that come with barcodes include the Permanent Account Number (PAN) Card in India, Driver’s license in South Africa, etc.

### VIN Scanning

Every vehicle has its own Vehicle Identification Number (VIN). When printing the number on the vehicle, many manufacturers also print a barcode alongside it. Customers of your website can scan the barcode to save time and avoid misspelling and quickly start using the service you provide, such as registering for an insurance claim or looking up vehicle information like maintenance records, mileage rollbacks, etc.

### Inventory Management

Inventory management is a highly stressful and arduous process where both efficiency and accuracy are crucial. The library is capable of accurate recognition of multiple barcodes at the same time and does it directly within a browser that runs on most mobile devices. This can boost efficiency and save money. 
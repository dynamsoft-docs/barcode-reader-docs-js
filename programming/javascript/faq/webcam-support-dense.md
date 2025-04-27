---
layout: default-layout
title: Why isn't my webcam reading the barcode on my driver's license or ID card?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, webcam, driver license, ID
description: Why isn't my webcam reading the barcode on my driver's license or ID card?
needAutoGenerateSidebar: false
---

# Why isn't my webcam reading the barcode on my driver's license or ID card?

[<< Back to FAQ index](index.md)

When you attempt to read the barcode from a driver's license or an ID card using your built-in laptop webcam and our [online demo](https://demo.dynamsoft.com/barcode-reader-js/), you will notice that the barcode does not get read almost all of the time. That is due to several factors - the lack in camera quality combined with the high density of PDF417 barcodes.

The barcode that is present on the back of driver licenses and ID cards is usually a [PDF417 barcode](https://www.dynamsoft.com/barcode-reader/barcode-types/pdf417/), one of the most common high-density 2D barcodes. Due to its high density, PDF417s usually require a camera that supports a minimum resolution of 720p and, more importantly, has the ability to focus, whether it is autofocus or manual focus.

Most built-in laptop webcams these days meet the minimum required resolution of 720p - but they almost always lack the ability to focus. The ability to focus is very important as it helps pass a clear image/frame of the PDF417 code to the DBR library, making it actually readable.

This problem is never really encountered on mobile as most modern mobile phones these days have high quality cameras that have the ability to autofocus, so that is never really a worry with mobile phones.

Therefore, if you are required to use laptops to read barcodes from driver licenses in your use case, please keep this in mind. We recommend avoiding using laptop webcams as the camera input for such use cases. If you need to use laptops, then we recommend purchasing an external webcam that meets the minimum resolution (1080p is the recommended resolution, but 720p is the minimum) but more importantly, has the ability to focus.

In addition, please note that this not only applies to PDF417 barcodes, but other dense types of barcodes such as high-density QR Codes.

If your built-in laptop webcam does indeed have the ability to focus and you are still struggling to read these dense type of barcodes, please let us know as we could potentially use some of the [Camera Enhancer API]({{site.dce_js_api}}index.html) to hone the focus of the camera to be suited for this use case. If you have any questions on this matter, do not hesitate to [contact us](https://www.dynamsoft.com/contact/).


## Additional Information for Florida Driver's Licenses
The Florida DMV has confirmed that a subset of driver's licenses - including some printed as recently as 2022 - contain PDF417 barcodes that are completely unreadable by standard scanning technology. Through extensive testing, we've found these problematic barcodes exhibit severe quality defects (including extreme blurring, heavy smudging, and critical misprinting) that prevent successful decoding by our SDK or any other scanning solutions we've evaluated.

When present, these defects are beyond what standard correction algorithms can repair, resulting in inconsistent or failed read attempts across all scanning methods. While the DMV has improved its processes, we continue to encounter these unreadable licenses in circulation.

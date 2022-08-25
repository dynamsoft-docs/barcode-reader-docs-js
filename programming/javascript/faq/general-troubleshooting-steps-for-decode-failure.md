---
layout: default-layout
title: What are the general troubleshooting steps if a video stream fails to decode with Dbr JS?
keywords: Dynamsoft Barcode Reader, FAQ, Troubleshooting / User Cases, general troubleshooting, decode fails
description: What are the general troubleshooting steps if a video stream fails to decode with Dbr JS?
needAutoGenerateSidebar: false
---

## What are the general troubleshooting steps if a video stream fails to decode with Dbr JS?

[<< Back to FAQ index](index.md)

1. The first thing to try is the [JavaScript online demo](https://demo.dynamsoft.com/barcode-reader-js/). Play around with the settings. You can shift the slider on the left–hand side of the online demo to [**“Best Coverage”**](https://www.dynamsoft.com/barcode-reader/programming/javascript/api-reference/BarcodeReader.html?ver=latest#updateruntimesettings). This slider determines which `mode` the SDK will use, going from best speed (least coverage) to best coverage (worst speed). 
   - If the barcode is decoded, then you can output the settings and use the settings in your app. If you want the source code of our demo, you can download it by clicking "GET DEMO CODE".
   - If the barcode still can’t be decoded via the online demo, then we can move to next step.
2. Save the video frames By clicking the "capture video frames" button at the top of [JavaScript online demo](https://demo.dynamsoft.com/barcode-reader-js/). 
3. Share the video frames with [Dynamsoft Support team](https://www.dynamsoft.com/company/contact/). Dynamsoft team will investigate the video frames and get back to you as soon as possible.
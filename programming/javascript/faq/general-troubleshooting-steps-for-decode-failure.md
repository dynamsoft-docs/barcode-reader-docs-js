---
layout: default-layout
title: What are the general troubleshooting steps if a video stream fails to decode with Dbr JS?
keywords: Dynamsoft Barcode Reader, FAQ, Troubleshooting / User Cases, general troubleshooting, decode fails
description: What are the general troubleshooting steps if a video stream fails to decode with Dbr JS?
needAutoGenerateSidebar: false
---

# What are the general troubleshooting steps if a video stream fails to decode with DBR JS?

[<< Back to FAQ index](index.md)

1. The first thing to try is the [JavaScript online demo](https://demo.dynamsoft.com/barcode-reader-js/). If the barcode is not being picked up under normal settings, let's try out some different settings. On the left-hand side, under "Scan Settings", you can try the "Balance" or "Best Coverage" scan modes as alternatives. This slider determines which `mode` the SDK will use, going from best speed (least coverage) to best coverage (worst speed). To learn more about scan modes, please visit the [`updateRuntimeSettings`](../api-reference/BarcodeReader.md#updateruntimesettings) API page.
   - If the barcode is decoded, then you can output the settings and use that setting template via the `updateRuntimeSettings` method.
   - If the barcode still can’t be decoded via the online demo, then move on to step 2.
2. Save the video frames by clicking the "capture video frames" button right next to the sound button at the top of the [JavaScript online demo](https://demo.dynamsoft.com/barcode-reader-js/).
3. Share the video frames with [Dynamsoft Support team](https://www.dynamsoft.com/company/contact/). The Dynamsoft team will investigate the video frames and get back to you as soon as possible.
---
layout: default-layout
title: what are the general troubleshooting steps if I fail to scan barcodes from camera?
keywords: Dynamsoft Barcode Reader, FAQ, Troubleshooting / User Cases, general troubleshooting, decode fails
description: what are the general troubleshooting steps if I fail to scan barcodes from camera?
needAutoGenerateSidebar: false
---

# what are the general troubleshooting steps if I fail to scan barcodes from camera?

[<< Back to FAQ index](index.md)


You may sometimes experience issues when trying to scan some barcodes from your device camera. There are various factors that could cause barcodes difficult to be read from the video stream of your camera, such as camera resolution setting, lighting condition, damage level of the barcode, or improper scanning settings.

Generally, with some quick setting changes with our APIs, Dynamsoft Barcode Reader JavaScript SDK is able to deliver great performance in your unique use case.

## Step 1 - try different scan settings with our standard online demo
1. The first thing to try is the [JavaScript online demo](https://demo.dynamsoft.com/barcode-reader-js/). If the barcode is not being picked up under normal settings, let's try out some different settings. On the left-hand side, under "Scan Settings", you can try the "Balance" or "Best Coverage" scan modes as alternatives. Going from best speed (least coverage) to best coverage (worst speed), you can pick a `mode` as you like. 

      ![Best coverage](../assets/best_coverage.jpg)

> **_NOTE:_**  To learn more about scan modes, please visit the [`updateRuntimeSettings`](../api-reference/BarcodeReader.md#updateruntimesettings) API page.

2. Enabling Full HD resolution may also help.

      ![Full HD](../assets/full_hd.jpg)

> **_NOTE:_** If the barcode is decoded, then you can output the settings and use that setting template via the `updateRuntimeSettings` method. If the barcode still can’t be decoded via the online demo, then move on to step 2.

## Step 2 - capture image frames and send to Dynamsoft for analysis

1.  Clicking the "capture video frames" button at the top of the [JavaScript online demo](https://demo.dynamsoft.com/barcode-reader-js/) to capture video frames while you reproduce the issue.

      ![Frames crop](../assets/frames-crop.png)

2. Share the video frames set with [Dynamsoft Support team](https://www.dynamsoft.com/company/contact/). Our support team will investigate the video frames and get back to you with a solution as soon as possible.

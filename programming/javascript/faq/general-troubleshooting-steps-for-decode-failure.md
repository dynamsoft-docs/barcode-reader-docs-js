---
layout: default-layout
title: what are the general troubleshooting steps if I fail to scan barcodes from camera?
keywords: Dynamsoft Barcode Reader, FAQ, Troubleshooting / User Cases, general troubleshooting, decode fails
description: what are the general troubleshooting steps if I fail to scan barcodes from camera?
needAutoGenerateSidebar: false
---

# What are the general troubleshooting steps if I fail to scan barcodes via the camera?

[<< Back to FAQ index](index.md)


You may sometimes experience issues when trying to scan some barcodes using your device via the camera. There are various factors that could play into this, such as camera resolution, lighting condition(s), damage level of the barcode, or improper scanning settings.

Generally, with some setting changes via our APIs, DBR JS is able to adapt to your unique usage scenario and deliver great performance.

## Try different scan settings with our standard online demo
1. The first thing is to try the [JavaScript online demo](https://demo.dynamsoft.com/barcode-reader-js/). If the barcode is not being picked up under normal settings, let's try out some different settings in the demo. By default, the demo runs on the *Best Speed* mode, which you can see under the "Scan Settings" on the left-hand side. To potentially improve the performance, we recommend trying out the two other available modes in the demo: *Balance* or *Best Coverage*. *Best Coverage* will prioritize read rate over speed, while *Best Speed* will prioritize speed over accuracy or read rate. *Balance* offers the perfect mixture between the two. 

      ![Best coverage](../assets/best_coverage.jpg)

> **_NOTE:_**  To learn more about scan modes, please visit the [`updateRuntimeSettings`](../api-reference/BarcodeReader.md#updateruntimesettings) API page.

2. Enable Full HD resolution in the demo

      ![Full HD](../assets/full_hd.jpg)

> **_NOTE:_** If the barcode is decoded, then you can output the settings and use that setting template via the `updateRuntimeSettings` method. To get the settings code snippet, please go to *Scan Settings* -> *View Settings* -> then select whether you want to copy the code snippet or send it to your email. If the barcode still can't be decoded via the online demo, please contact the Dynamsoft Support Team.
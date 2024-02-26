---
layout: default-layout
title: Debug Sample - Dynamsoft Barcode Reader JavaScript Edition
description: Dynamsoft Barcode Reader JavaScript Edition - Debug Sample
keywords: javascript, js, barcode, vanilla, debug
noTitleIndex: true
breadcrumbText: Debug
permalink: /programming/javascript/samples-demos/debug.html
---

# Debug Sample

This sample is designed to:

1. Print detailed logs in the browser console to better assist in troubleshooting.
2. Check if your device and browser are compatible with the camera and to what extent.
3. Collect video frames for analysis. (Require to host the sample locally)

## Collect the video frames for analysis

Barcode reading is a one-time job, the application either succeeds or fails to read the barcode(s). For the failed scenario, it's possible to make them successful by adjusting the settings provided by the Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library"). However, adjusting the settings could be a bit overwhelming. Therefore, Dynamsoft offers the debug sample that enables customers to capture and save runtime video frames for sending to the Dynamsoft team. With the original images, the team can test and optimize settings for customers.

The following shows how to host the sample and collect frames.

### Download the sample

The sample can be downloaded from

<a target_="blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/9.x/5.others/debug" alt="Debug Sample on GitHub">Debug Sample on GitHub</a>

Note that the entire folder is required. To download only the files in this folder, try using "https://downgit.github.io/#/home".

### Set up a local server

Since the video is usually playing on mobile devices, having these frames uploaded to a self-hosted local server is most convenient, therefore, we first need to set up a local server.

We make use of the web server that comes with [Express](https://expressjs.com/).

* Install dependencies

Run the following script to install all dependencies.

`npm install`

* Start the server

We defined the web server logic in the file "app.js", to start it, run the following script:

`node app.js`

Note that we have used self-signed certificates to enable SSL on the port 4443.

### Use the sample page

Once the server is up and running, open the page on the device that will do the barcode reading. The URL for the sample is "https://{your-local-ip}:4443/". For example, suppose your ip is 192.168.1.1, the site can be visited at "https://192.168.1.1:4443/".

> Note that the device should be in the same WiFi network as the server machine. 

You will see a warning due to self-signing. Please ignore and keep processing.

Click the button "show scanner" and try to read barcodes, the frames will then be uploaded to the folder "debug\public\collect" as images (.png) on the server. When you have collected enough frames, please turn off the scanner, otherwise, new frames will continue to flood in.

Check the images to make sure that they correctly represent the actual usage scenario, then zip and send them to Dynamsoft for technical assistance.

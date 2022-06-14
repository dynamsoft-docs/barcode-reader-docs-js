---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - Debug Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - Debug Sample
keywords: javascript, js, barcode, vanilla, debug
noTitleIndex: true
breadcrumbText: Debug
permalink: /programming/javascript/samples-demos/debug.html
---

# JavaScript Debug Sample

Barcode reading is a one-time job, the application either succeeds or fails to read the barcode(s). For the failed cases, it's possible to make them successful by adjusting some of the many settings provided by the Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library"). However, adjusting the settings could be a bit overwhelming for the users. Therefore, Dynamsoft provides this debug sample which allows a user to collect runtime video frames to be sent to the Dynamsoft Team. Since these frames represent the actual usage scenario, the team can test them to see how the settings can be optimized to best process them.

The following shows how to use the debug sample.

## Download the sample

The sample can be downloaded from

<a target_="blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main/5.others/debug" alt="Debug Sample on GitHub">Debug Sample on GitHub</a>

Note that the entire folder is required. To download only the files in this folder, try using "https://downgit.github.io/#/home".

## Use the sample

Since the video is usually playing on mobile devices, having these frames uploaded to a self-hosted local server is most convenient, therefore, we first need to set up a local server.

### Set up a local server

We make use of the web server that comes with [Express](https://expressjs.com/).

* Install Express

Run the following script to install Express.

`npm install`

* Start the server

We defined the web server logic in the file "app.js", to start it, run the following script:

`node app.js`

Note that we have enabled SSL on this server at the port 4443.

### Use the sample page

Once the server is up and running, open the page on the device that will do the barcode reading. The URL for the sample is "https://{your-local-ip}:4443/". For example, suppose your ip is 192.168.1.1, the site can be visited at https://192.168.1.1:4443/.

> Note that the device should be in the same WiFi network as the server machine.

Click the button "show scanner" and try to read barcodes as you normally do, the frames will then be uploaded to the folder "debug\public\collect" as images (.png) on the server. When you have collected enough frames, don't forget to turn off the scanner, otherwise, new frames will continue to flood in.

Check the images to make sure that they correctly represent the actual usage scenario, then zip and send them to Dynamsoft for technical assistance.

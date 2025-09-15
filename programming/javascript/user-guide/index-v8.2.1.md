---
layout: default-layout
title: v8.2.1 User Guide - Dynamsoft Barcode Reader JavaScript Edition
description: This is the user guide of Dynamsoft Barcode Reader JavaScript SDK.
keywords: user guide, javascript, js
breadcrumbText: User Guide
needAutoGenerateSidebar: true
permalink: /programming/javascript/user-guide/index-v8.2.1.html
---

# Dynamsoft Barcode Reader JavaScript Edition - User Guide

![Dynamsoft JavaScript Barcode SDK](assets/dbr-js-sdk.png)  

[Dynamsoft BarcodeReader SDK for Web](https://www.dynamsoft.com/Products/barcode-recognition-javascript.aspx) is a JavaScript SDK for barcode scanning based on **WebAssembly**. It supports real-time barcode localization and decoding of various barcode types. The library is capable of scanning barcodes directly from live video streams as well as static images. It also supports reading multiple barcodes at once.  

In this guide, you will learn step by step how to use Dynamsoft Barcode Reader JavaScript Edition in your application:

- [Getting Started](#getting-started---hello-world)
- [Installation](#installation)
- [Basic Customizations]({{ site.js }}user-guide/basic-customizations.html)
- [Advanced Customizations]({{ site.js }}user-guide/advanced-customizations.html)
- [Deployment Activation]({{ site.js }}user-guide/deployment-activation.html)
- [Features Requirements]({{ site.js }}user-guide/features-requirements.html)
- [Upgrade]({{ site.js }}user-guide/upgrade.html)


## Getting Started - Hello World  

Let's start by using the library to build a simple web application that will decode barcodes from a live video stream.  

### Basic Requirements

- Internet connection  
- [Supported Browser]({{site.js}}user-guide/features-requirements.html#system-requirements)
- Camera access  

### Step One: Write the code in one minute  

Creat a text file anywhere on your local disk and name it "helloworld.html". Copy the following content in the file and save. 

```html
<!DOCTYPE html>
<html>
<body>
    <!-- Please visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=guide&product=dbr&package=js to get a trial license. -->
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.1/dist/dbr.js" data-productKeys="PRODUCT-KEYS"></script>
    <script>
        // initializes and uses the library
        let scanner = null;
        (async()=>{
            scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
            scanner.onFrameRead = results => {if(results.length > 0 ) console.log(results);};
            scanner.onUnduplicatedRead = (txt, result) => {alert(txt);};
            await scanner.show();
        })();
    </script>
</body>
</html>
```

*About the code*

- `onFrameRead`: This event is triggered after the library finishes scanning a frame from the video stream. The `results` object contains all the barcode results that the library found on this frame. In this example, we print the results to the browser console.

- `onUnduplicatedRead`: This event is triggered when a new barcode (not a duplicate) is found. `txt` holds the barcode text value while `result` is an object that holds details of the barcode. In this example, an alert will be displayed for each unique barcode found. Notice that if the same barcode is found on multiple consecutive frames, this event is only triggered once.


[Try in JSFiddle](https://jsfiddle.net/DynamsoftTeam/pL4e7yrd/)

*Note*:

- The recommendation is to deploy this page to your web server and run it over **HTTPS**. If you don't have a ready-to-use web server but have a package manager like npm or yarn, you can set up a simple HTTP server in minutes. Check out [http-server on npm](https://www.npmjs.com/package/http-server) or [yarn](https://yarnpkg.com/package/http-server). However, for simple testing purposes, it's perfectly fine to just open the file directly from your local disk.

- You will need to replace `PRODUCT-KEYS` with a trial key (or your Handshake Code if you have got one) for the sample code to work correctly. You can acquire a trial key [here](https://www.dynamsoft.com/customer/license/trialLicense?utm_source=guide&product=dbr&package=js). Notice that the library will still read barcodes without a valid key (Code), but will return an annotated result string.

- The library only scans a new frame when it has finished scanning the previous frame. Generally, frames come in faster than the library processes a frame (for 30 FPS, the interval is about 33 ms), therefore not all frames are scanned.

### Step Two: Enable camera access

Open the HTML page in your browser and you should see a pop-up asking for permission to access the camera. Once the access is granted, the video stream will start in the default UI of the **BarcodeScanner** object.  

*Note*: 

- If you don't see the pop-up, wait a few seconds for the initialization to finish.   

In this step, you might run into the following issues:

#### getUserMedia non-HTTPS access issue

If you opened the HTML file as `file:///` or `http://`, the following error may appear in the browser console:

> [Deprecation] getUserMedia() no longer works on insecure origins. To use this feature, you should consider switching your application to a secure origin, such as HTTPS. See https://goo.gl/rStTGz for more details.

In Safari 12 the equivalent error is:

> Trying to call getUserMedia from an insecure document.

You get this error because to access the camera with the API [getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia), HTTPS is required.

*Note*

- If you use Chrome or Firefox, you might not get the error because these two browsers allow camera access via file:/// and http://localhost.

To make sure your web application can access the camera, please configure your web server to support HTTPS. The following links may help.

- NGINX: [Configuring HTTPS servers](https://nginx.org/en/docs/http/configuring_https_servers.html)
- IIS: [Create a Self Signed Certificate in IIS](https://aboutssl.org/how-to-create-a-self-signed-certificate-in-iis/)
- Tomcat: [Setting Up SSL on Tomcat in 5 minutes](https://dzone.com/articles/setting-ssl-tomcat-5-minutes)
- Node.js: [npm tls](https://nodejs.org/docs/v0.4.1/api/tls.html)

#### Self-signed certificate issue

For testing purposes, a self-signed certificate can be used when configuring HTTPS. When accessing the site, the browser might say "the site is not secure". In this case, go to the certificate settings and trust this certificate.

In a production environment, a valid HTTPS certificate is required.

### Step Three: Time to scan

Place a barcode in front of the camera. You should see an alert pop up with the decoded barcode result and a coloured region on the video to highlight the barcode location. 

## Installation

For evaluation purposes, we recommend that you get the official package of the library for developers. The following shows how to acquire the package.

* From the website

  [Download Dynamsoft Barcode Reader](https://www.dynamsoft.com/barcode-reader/downloads/)

* yarn

  ```
  $ yarn add dynamsoft-javascript-barcode
  ```

* npm

  ```
  $ npm install dynamsoft-javascript-barcode --save
  ```

If you want to start building your application right away, you can also just make use of the library via CDN as shown in the previous helloworld sample code.

* cdn

  ```
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.2.1/dist/dbr.js" data-productKeys="PRODUCT-KEYS"></script>
  <!-- or -->
  <script src="https://unpkg.com/dynamsoft-javascript-barcode@8.2.1/dist/dbr.js" data-productKeys="PRODUCT-KEYS"></script>
  ```

Dynamsoft also provides a Barcode Reader SDK built for Node, see [Dynamsoft JavaScript Barcode SDK for Node](https://github.com/dynamsoft-dbr/node-javascript-barcode).

## Demos and Examples

The following are the official demo of the library and examples for the most popular JavaScript Frameworks.

- [Online demo](https://demo.dynamsoft.com/barcode-reader-js/)
- [Vue example](https://github.com/Dynamsoft/javascript-barcode/tree/master/example/web/vue)    
- [React example](https://github.com/Dynamsoft/javascript-barcode/tree/master/example/web/react)     
- [Angular example](https://github.com/Dynamsoft/javascript-barcode/tree/master/example/web/angular)  


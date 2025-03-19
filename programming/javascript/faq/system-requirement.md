---
layout: default-layout
title: What are the system requirements for running the latest version of Dynamsoft Barcode Reader?
keywords: Dynamsoft Barcode Reader, FAQ, JavaScript, system, requirement
description: The system requirements for running the latest version of Dynamsoft Barcode Reader?
needAutoGenerateSidebar: false
---

# What are the system requirements for running the latest version of Dynamsoft Barcode Reader?

[<< Back to FAQ index](index.md)

## System Requirements

The latest version of DBR requires the following features to work:

- Secure context (HTTPS deployment)

  When deploying your application / website for production, make sure to serve it via a secure HTTPS connection. This is required for two reasons
  
  - Access to the camera video stream is only granted in a security context. Most browsers impose this restriction.
  > Some browsers like Chrome may grant the access for `http://127.0.0.1` and `http://localhost` or even for pages opened directly from the local disk (`file:///...`). This can be helpful for temporary development and test.
  
  - Dynamsoft License requires a secure context to work.
 
-  Set the MIME type for `.wasm` as `application/wasm`
   
   The goal is to configure your server to send the correct Content-Type header for the wasm file so that it is processed correctly by the browser.
     
     Different types of webservers are configured differently, for example:

     + <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Learn/Server-side/Apache_Configuration_htaccess#media_types_and_character_encodings" title="Apache">Apache</a>
     + <a target="_blank" href="https://docs.microsoft.com/en-us/iis/configuration/system.webserver/staticcontent/mimemap" title="IIS">IIS</a>
     + <a target="_blank" href="https://www.nginx.com/resources/wiki/start/topics/examples/full/#mime-types" title="NGINX">NGINX</a>


- `WebAssembly`, `Blob`, `URL`/`createObjectURL`, `Web Workers`

  The above four features are required for the SDK to work.

- `MediaDevices`/`getUserMedia`

  This API is required for in-browser video streaming.

- `getSettings`

  This API inspects the video input which is a `MediaStreamTrack` object about its constrainable properties.

The following table is a list of supported browsers based on the above requirements:

  | Browser Name |     Version      |
  | :----------: | :--------------: |
  |    Chrome    | v78+<sup>1</sup> |
  |   Firefox    | v68+<sup>1</sup> |
  |     Edge     |       v79+       |
  |    Safari    |       v14+       |

  <sup>1</sup> devices running iOS needs to be on iOS 14.3+ for camera video streaming to work in Chrome, Firefox or other Apps using webviews.

Apart from the browsers, the operating systems may impose some limitations of their own that could restrict the use of the SDK. Browser compatibility ultimately depends on whether the browser on that particular operating system supports the features listed above.

---
layout: default-layout
title: When is singleFrameMode enabled?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, singleFrameMode
description: When is singleFrameMode enabled?
needAutoGenerateSidebar: false
---

# When is singleFrameMode enabled?

[<< Back to FAQ index](index.md)

## Verson 10
SingleFrameMode can be enabled by calling the api from the camera enhancer module. check
[singleFrameMode](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/acquisition.html#singleframemode) for detailed information.

## Version 9 
`singleFrameMode` is enable in the below two scenarios -

1. When using the library from a non-secure origin (no HTTPS).
2. When using a browser that doesn't support `getUserMedia/MediaDevices` API that is required for video streaming. To confirm whether or not your browser is supported, please refer to the [System Requirements](https://www.dynamsoft.com/barcode-reader/programming/javascript/user-guide/?ver=latest#system-requirements) section of the user guide.

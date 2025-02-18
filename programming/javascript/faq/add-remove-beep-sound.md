---
layout: default-layout
title: How to add/remove a "beep" sound once a barcode is found?
keywords: Dynamsoft Barcode Reader, FAQ, JavaScript, tech basic, beep, sound
description: How to add/remove a "beep" sound once a barcode is found?
needAutoGenerateSidebar: false
---

# How to add/remove a "beep" sound once a barcode is found?

[<< Back to FAQ index](index.md)

## Version 10
This feature is controlled by the `Dynamsoft Camera Enhancer` module. 

```javascript
Dynamsoft.DCE.Feedback.beep();
```
**_NOTE:_** - Check the class [Feedback](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/feedback.html#beep) for more details.


## Version 9
This feature is controlled using the [whenToPlaySoundforSuccessfulRead](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/interface/ScanSettings.html?ver=latest) property. To enable the feature, set the property to either **frame** or **unique**. To disable the feature, set it to **never**.

> This feature is disabled by default.

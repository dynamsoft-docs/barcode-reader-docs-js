---
layout: default-layout
title: DBR JS - Advanced Customizations
description: This page shows how to customize advanced features of Dynamsoft Barcode Reader JavaScript SDK.
keywords: user guide, advanced customizations, debug, area, region, javascript, js
needAutoGenerateSidebar: true
---

# Advanced Usage

* [Read a specific area/region](#read-a-specific-arearegion)
* [Account for newline characters in the barcode result](#account-for-newline-characters-in-the-barcode-result)
* [Show internal logs](#show-internal-logs)
* [Set mode arguments](#set-mode-arguments)
* [Display images in different stages of the reading process](#display-images-in-different-stages-of-the-reading-process)
* [Hosting the library](#hosting-the-library)

## Read a specific area/region

To speed up the scanning process, you can choose to scan only a specific area/region.

```javascript
let settings = await scanner.getRuntimeSettings();
/*
 * The following code shrinks the decoding region by 25% on all sides
 */
settings.region.regionMeasuredByPercentage = 1;
settings.region.regionLeft = 25;
settings.region.regionTop = 25;
settings.region.regionRight = 75;
settings.region.regionBottom = 75;
await scanner.updateRuntimeSettings(settings);
```

[Try in JSFiddle](https://jsfiddle.net/DynamsoftTeam/taykq592/)

## Account for newline characters in the barcode result

When it comes to HTML, newline characters ( `\n` ) are not interpreted as they normally would. Therefore, if a barcode result contains a newline character, and you display the result in an modal dialogue box or some other text elements, then the newline character will probably be ignored.

There are two ways in which you can resolve this:

1. Wrap the element used to display the result in a `<pre>` element.
2. Manually replace each `\n` character in the result with `<br>`

## Show internal logs

Include the following in your code to print internal logs in the console.

```javascript
Dynamsoft.DBR.BarcodeReader._onLog = console.log;
```

## Set mode arguments

To precisely control a mode, you can adjust its specific parameters.

```javascript
let settings = await scanner.getRuntimeSettings();

/*
 * The following code sets the sensitivity of the TextureDetectionModes to 9
 */

settings.furtherModes.textureDetectionModes = [
    Dynamsoft.DBR.EnumTextureDetectionMode.TDM_GENERAL_WIDTH_CONCENTRATION, 0, 0, 0, 0, 0, 0, 0
];

await scanner.updateRuntimeSettings(settings);
// The 2nd parameter 0 specifies the 0th mode of TextureDetectionModes, 
// which is "Dynamsoft.DBR.EnumTextureDetectionMode.TDM_GENERAL_WIDTH_CONCENTRATION" in this case.
await scanner.setModeArgument("TextureDetectionModes", 0, "Sensitivity", "9");
```

## Display images in different stages of the reading process

The original canvases are saved when setting `ifSaveOriginalImageInACanvas` to `true`. The method `getOriginalImageInACanvas()` returns a canvas which holds the image to be passed to the barcode reader engine for decoding. 

The intermediate result canvases are created when `intermediateResultTypes` is set to a value other than `IRT_NO_RESULT` . Then these intermediate result canvases can be returned with the method `getIntermediateCanvas()` to be used for showing and debugging the barcode reading process. 

> *NOTE*
>  
> For efficiency, the library may utilize WebGL (Web Graphics Library) for preprocessing an image before passing it to the barcode reader engine. If WebGL is used, the image captured from the camera will not be rendered on the canvas, instead, it gets processed by WebGL first and then is passed to the barcode reader engine directly. In this case, there won't be an original canvas.
> 
> Therefore, if `ifSaveOriginalImageInACanvas` is set to `true` for a `BarcodeScanenr` instance, the WebGL feature will be disabled for that instance.
>
> You can manually disable the WebGL feature by setting `_bUseWebgl` as `false`. If WebGL is disabled, when you try to get the intermediate result canvas (with `getIntermediateCanvas()`) specified by `EnumIntermediateResultType.IRT_ORIGINAL_IMAGE` , the canvas will be exactly the same image as you would get with `getOriginalImageInACanvas()` .

The following shows how to display these images on the page

```html
<div id='scannerV' style="width:50vw;height:50vh"></div>
<div id='cvses'></div>
```

```javascript
// original canvas
(async () => {
    let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
    document.getElementById('scannerV').appendChild(scanner.getUIElement());
    scanner.ifSaveOriginalImageInACanvas = true;
    scanner.onUniqueRead = async (txt, result) => {
        try {
            let cvs = scanner.getOriginalImageInACanvas();
            document.getElementById('cvses').appendChild(cvs);
            scanner.destroyContext();
        } catch (ex) {
            console.error(ex);
        }
    };
    await scanner.show();
})();
```

```javascript
// intermediate result canvas
(async () => {
    let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
    // scanner._bUseWebgl = false;
    document.getElementById('scannerV').appendChild(scanner.getUIElement());
    let rs = await scanner.getRuntimeSettings();
    rs.intermediateResultTypes = Dynamsoft.DBR.EnumIntermediateResultType.IRT_ORIGINAL_IMAGE;
    await scanner.updateRuntimeSettings(rs);
    scanner.onUniqueRead = async (txt, result) => {
        try {
            let cvss = await scanner.getIntermediateCanvas();
            for (let cvs of cvss) {
                document.getElementById('cvses').appendChild(cvs);
            }
            scanner.destroyContext();
        } catch (ex) {
            console.error(ex);
        }
    };
    await scanner.show();
})();
```
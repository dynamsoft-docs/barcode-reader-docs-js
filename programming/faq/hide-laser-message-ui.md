---
layout: default-layout
title: How can I hide the laser bar and Dynamsoft message in the default UI of the BarcodeScanner?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, barcodeReader, barcodeScanner, hide, UI
description: How can I hide the laser bar and Dynamsoft message in the default UI of the BarcodeScanner?
needAutoGenerateSidebar: false
---

# How can I hide the laser bar and Dynamsoft message in the default UI of the BarcodeScanner?

## Version 10
To change the UI, you will need to use the CamerView from the `Camera Enhancer Module`
for laser there is a direct api which you can reference, for other changes you need to either access via class or [customize your own ui](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/user-guide/index.html#customize-the-ui).

```javascript
cameraView.setScanLaserVisible(false); //sets laser off, needs to be called after StartCapturing
//needs to either target the shadowRoot element like this or implement your own UI
document.getElementById('div-ui-container').children[0].shadowRoot.querySelector('.dce-msg-poweredby').style.display='none'
```

## Version 9 
In order to show or hide these specific UI elements, all you need to do is access them individually via their class names and setting the corresponding display property.

By default, these elements will be shown. In order to hide them, an edited Hello World code snippet can be found below that will get the job done. Please note that the elements must be hidden after `scanner.show()` is called since that is when the elements are created.

``` html
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.6.40/dist/dbr.js"></script>
<script>
  // specify a license, you can visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=intro&product=dbr&package=js to get your own trial license good for 30 days. 
  Dynamsoft.DBR.BarcodeScanner.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
  (async()=>{
    let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
    scanner.onUniqueRead = (txt, result) => {
      // Do something with the "txt" found in the barcode
    };

    await scanner.show();

    // hide the laser bar and Dynamsoft message in the default UI after show() is called or else you will get an undefined error
    document.getElementsByClassName("dce-scanlight")[0].style.display = "none";
    document.getElementsByClassName("dbr-msg-poweredby")[0].style.display = "none";
  })();
</script>
```
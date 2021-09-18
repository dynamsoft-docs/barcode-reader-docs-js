---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - Electron Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - Electron
keywords: javascript, js, barcode, vanilla
noTitleIndex: true
breadcrumbText: Electron
---

# JavaScript Hello World Sample - Electron <svg height="45px" xmlns="http://www.w3.org/2000/svg"><g fill="none" fill-rule="evenodd"><circle fill="#2B2E3A" cx="128" cy="128" r="128"/><g fill="#9FEAF9" fill-rule="nonzero"><path d="M100.502 71.69c-26.005-4.736-46.567.221-54.762 14.415-6.115 10.592-4.367 24.635 4.24 39.646a2.667 2.667 0 1 0 4.626-2.653c-7.752-13.522-9.261-25.641-4.247-34.326 6.808-11.791 25.148-16.213 49.187-11.835a2.667 2.667 0 0 0 .956-5.247zm-36.999 72.307c10.515 11.555 24.176 22.394 39.756 31.388 37.723 21.78 77.883 27.601 97.675 14.106a2.667 2.667 0 1 0-3.005-4.406c-17.714 12.078-55.862 6.548-92.003-14.318-15.114-8.726-28.343-19.222-38.478-30.36a2.667 2.667 0 1 0-3.945 3.59z"/><path d="M194.62 140.753c17.028-20.116 22.973-40.348 14.795-54.512-6.017-10.423-18.738-15.926-35.645-16.146a2.667 2.667 0 0 0-.069 5.333c15.205.198 26.165 4.939 31.096 13.48 6.792 11.765 1.49 29.807-14.248 48.399a2.667 2.667 0 1 0 4.071 3.446zm-43.761-68.175c-15.396 3.299-31.784 9.749-47.522 18.835-38.942 22.483-64.345 55.636-60.817 79.675a2.667 2.667 0 1 0 5.277-.775c-3.133-21.344 20.947-52.769 58.207-74.281 15.267-8.815 31.135-15.06 45.972-18.239a2.667 2.667 0 1 0-1.117-5.215z"/><path d="M87.77 187.753c8.904 24.86 23.469 40.167 39.847 40.167 11.945 0 22.996-8.143 31.614-22.478a2.667 2.667 0 1 0-4.571-2.748c-7.745 12.883-17.258 19.892-27.043 19.892-13.605 0-26.596-13.652-34.825-36.63a2.667 2.667 0 1 0-5.021 1.797zm81.322-4.863c4.61-14.728 7.085-31.718 7.085-49.423 0-44.179-15.463-82.263-37.487-92.042a2.667 2.667 0 0 0-2.164 4.874c19.643 8.723 34.317 44.866 34.317 87.168 0 17.177-2.397 33.63-6.84 47.83a2.667 2.667 0 1 0 5.09 1.593zm50.224-2.612c0-7.049-5.714-12.763-12.763-12.763-7.049 0-12.763 5.714-12.763 12.763 0 7.049 5.714 12.763 12.763 12.763 7.049 0 12.763-5.714 12.763-12.763zm-5.333 0a7.43 7.43 0 1 1-14.86 0 7.43 7.43 0 0 1 14.86 0zM48.497 193.041c7.05 0 12.764-5.714 12.764-12.763 0-7.049-5.715-12.763-12.764-12.763-7.048 0-12.763 5.714-12.763 12.763 0 7.049 5.715 12.763 12.763 12.763zm0-5.333a7.43 7.43 0 1 1 0-14.86 7.43 7.43 0 0 1 0 14.86z"/><path d="M127.617 54.444c7.049 0 12.763-5.714 12.763-12.763 0-7.049-5.714-12.763-12.763-12.763-7.049 0-12.763 5.714-12.763 12.763 0 7.049 5.714 12.763 12.763 12.763zm0-5.333a7.43 7.43 0 1 1 0-14.86 7.43 7.43 0 0 1 0 14.86zm1.949 93.382c-4.985 1.077-9.896-2.091-10.975-7.076a9.236 9.236 0 0 1 7.076-10.976c4.985-1.077 9.896 2.091 10.976 7.076 1.077 4.985-2.091 9.897-7.077 10.976z"/></g></g></svg>

[Electron](https://www.electronjs.org/) is a framework for creating native applications with web technologies. Follow this guide to learn how to implement Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") into an Electron application.

## Official Sample

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/1.minimum-code.html">Read Barcodes from Camera - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/dbr-browser-samples/blob/master/1.hello-world/1.minimum-code.html">Read Barcodes from Camera - Source Code</a>

## Preparation

Make sure you have [node](https://nodejs.org/) installed. `node 14.16.0` is used in this article. 

## Create an empty Application

Create a folder with the name "read-video-electron" and a package.json file inside it with the following content:

```json
{
  "name": "read-video-electron",
  "version": "1.0.0",
  "description": "How to read barcodes from a video input in an Electron App",
  "main": "main.js",
  "scripts": {
    "start": "electron .",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "tom@dynamsoft.com",
  "dependencies": {
    "electron": "14.0.1",
    "dynamsoft-javascript-barcode": "8.6.1"
  }
}
```

Then, run `npm install` to install the dependencies.

```cmd
npm install
```

## Start to implement

### Create a main.js file

As defined in the package.json file, main.js is the entry point of the application, we define it like this:

```javascript
const { app, BrowserWindow } = require('electron')

function createWindow() {
    const win = new BrowserWindow({
        width: 800,
        height: 600,
    })
    win.loadFile('index.html')
}

app.whenReady().then(() => {
    createWindow()
    app.on('activate', () => {
        if (BrowserWindow.getAllWindows().length === 0) {
            createWindow()
        }
    })
})

app.on('window-all-closed', () => {
    if (process.platform !== 'darwin') {
        app.quit()
    }
})
```

Two modules are imported in this file:

* `app`: controls the application's event lifecycle.
* `BrowserWindow`: creates and manages application windows.

The code basically opens index.html in a window. For more information, check out [Electron Quick Start](https://www.electronjs.org/docs/latest/tutorial/quick-start).

### Create an index.html file

Create the page to be loaded in the created window.

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>Read barcodes from a video input in Electron!</title>
    <link href="style.css" rel="stylesheet">
    <script src="./node_modules/dynamsoft-javascript-barcode/dist/dbr.js"></script>
    <script src="action.js"></script>
</head>

<body>
    <h1>Read barcodes from a video input</h1>
    <button id='readBarcode'>Read Barcode via Camera</button>
    <div id="UIElement">
        <div id="barcodeScannerUI"></div>
    </div>
    <input id="resultText" type="text" readonly="true">
</body>

</html>
```

The page loads action.js which makes use of the library to create a barcode scanner and read barcodes from a video input:

```javascript
window.onload = function () {
    Dynamsoft.DBR.organizationID = "234810";
    Dynamsoft.DBR.loadWasm();
    let pScanner = null;
    document.getElementById('readBarcode').onclick = async () => {
        try {
            let scanner = await (pScanner = pScanner || Dynamsoft.DBR.BarcodeScanner.createInstance());
            scanner.onFrameRead = results => {
                if (results.length) {
                    console.log(results);
                }
            };
            scanner.onUnduplicatedRead = (txt, result) => {
                document.getElementById('resultText').value = result.barcodeFormatString + ': ' + txt;
            };
            document.getElementById("barcodeScannerUI").appendChild(scanner.getUIElement());
            await scanner.show();
        } catch (ex) {
            alert(ex.message);
            throw ex;
        }
    };
}
```

Also, style.css defines the styles for the UI

```css
body {
    text-align: center;
}

#barcodeScannerUI {
    width: 100%;
    height: 100%;
}

#UIElement {
    margin: 2vmin auto;
    text-align: center;
    font-size: medium;
    height: 40vh;
    width: 80vw;
}
#resultText {
    display: block;
    margin: 0 auto;
    padding: 0.4rem 0.8rem;
    color: inherit;
    width: 80vw;
    border: none;
    font-size: 1rem;
    border-radius: 0.2rem;
    text-align: center;
}
```

## Run the application

Run the application with the following command and see how it works.

```cmd
npm install
```

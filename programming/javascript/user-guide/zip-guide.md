# Dynamsoft Barcode Reader JavaScript - Package Readme

Welcome! This package contains all resource files related to **Dynamsoft Barcode Reader JavaScript SDK**, and sample projects demonstrating how to use it.

---

## System Requirements

### Secure Context (HTTPS Deployment)

When deploying your application / website for production, make sure to serve it via a secure HTTPS connection. This is required for two reasons:

- Access to the camera video stream is only granted in a security context. Most browsers impose this restriction.

  > Some browsers like Chrome may grant the access for `http://127.0.0.1` and `http://localhost` or even for pages opened directly from the local disk (`file:///...`). This can be helpful for temporary development and test.

- Dynamsoft License requires a secure context to work.

### Browser Compatibility

The following table is a list of supported browsers based on the above requirements:

| Browser Name |     Version      |
| :----------: | :--------------: |
|    Chrome    | v78+<sup>1</sup> |
|   Firefox    | v68+<sup>1</sup> |
|     Edge     |       v79+       |
|    Safari    |      v14.5+      |

<sup>1</sup> devices running iOS needs to be on iOS 14.5+ for camera video streaming to work in Chrome, Firefox or other Apps using webviews.

Apart from the browsers, the operating systems may impose some limitations of their own that could restrict the use of the SDK.

---

## License

Dynamsoft provides a complimentary trial license for the SDK. When you download the SDK package from the Dynamsoft website, after creating a Dynamsoft account, the following license will have a 30-day free trial:

`DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9`

>[!IMPORTANT]
> Once your trial license expires, the SDK will throw an error and cease to function. You can visit the Dynamsoft Customer Portal (https://www.dynamsoft.com/customer/license/trialLicense?product=dbr&utm_source=installer&package=js) to view your trial license details. Additionally, it's possible to extend the trial period via the customer portal, allowing for a total trial duration of 60 days.

---

## Quick Start

1. Create a new text file in the same directory as this file
2. Copy the code below into the file
3. Rename the file extension to `.html` and save it

Double-click the file to open it in your browser, you'll instantly see a fully functional web application that scans a single barcode using your device's camera!

```html
<!DOCTYPE html>
<html>
<head>
    <title>Barcode Scanner</title>
    <script src="./dist/dbr.bundle.js"></script>
</head>
<body>
    <script>
        // You can visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=samples&product=dbr&package=js to get your own trial license good for 30 days.
        // Note that if you downloaded this sample from Dynamsoft while logged in, the license key below may already be your own 30-day trial license.
        new Dynamsoft.BarcodeScanner({license:"DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9"}).launch().then(result=>alert(result.barcodeResults[0].text));
    </script>
</body>
</html>
```

## How to Run the Samples

### 1. Unzip the Sample Files

After unzipping, you should see two folders: `dist`, which contains all the Barcode Reader JavaScript SDK resources, and `samples`, which includes subfolders for the individual sample projects.

### 2. Open the Samples in a Browser

To explore the full set of available samples, open the `samples/index.html` file in your browser.

>[!IMPORTANT]
> Some browsers block local file access for security reasons. To avoid these restrictions, run the samples through a local web server.

Here are a couple of easy ways to start one:

- Using Five Server VSCode extension

    If you are using VS Code, simply install the [Five Server extension](https://marketplace.visualstudio.com/items?itemName=yandeu.five-server), open the `Samples` folder in the editor, and click "Go Live" in the bottom right corner of the editor. This will serve the sample project at http://127.0.0.1:5500/index.html.

- Using Node.js and `serve`

    If you have Node.js installed:

    ```bash
    cd path/to/samples
    npx serve . -l 8000
    ```

    Once the server is running, open your browser and navigate to:
    
    ```bash
    http://localhost:8000
    ```
    
    You'll see the `index.html` page, which links to all sample pages.

>[!TIP]
> Don't want to set up a local server? You can view the latest version of our samples hosted on the Dynamsoft server here:
>https://demo.dynamsoft.com/Samples/DBR/JS/index.html

---

## Sample Folders

The package includes two main sample directories:

- **`frameworks/`** - Framework-specific examples demonstrating how to integrate the Dynamsoft Barcode Reader into common web and hybrid frameworks. Each framework folder contains one or more runnable sub-examples (such as `scan-using-foundational-api` and/or `scan-using-rtu-api`) showing practical integration patterns.

- **`scenarios/`** - Focused scenario samples that show common real-world uses of the Dynamsoft Barcode Reader.

---

## Choosing an API

The SDK provides two approaches for integrating barcode scanning capabilities:

### RTU API (BarcodeScanner)

The RTU API offers the quickest path to a working barcode scanner(**Recommended for most users**):

- **One-line integration** – Launch a full scanner with a single API call
- **Built-in UI** – Pre-designed viewfinder and scan region highlighting
- **Simple configuration** – Customize behavior through intuitive config objects

### Foundational APIs

If you are looking for a fully customizable barcode decoding library with complete control over the scanning process and UI, you are welcome to use the Foundational APIs.

---

## Self-Hosting Resources

If you prefer to host the SDK resources on your own server instead of using a CDN:

1. Copy the `dist` folder to your server
2. Include the script in your HTML:

```html
<!-- Adjust the path based on where you host the dist folder -->
<script src="assets/dynamsoft-barcode-reader/dist/dbr.bundle.js"></script>
```

3. Define the resource paths in your code:

```ts
engineResourcePaths: {
  rootDirectory: "https://cdn.jsdelivr.net/npm/",
}
```

---

## Documentation

For API reference and more advanced usage, visit:

- [Barcode Scanner API Docs](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/barcode-scanner.html)
- [Foundational API Docs](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/index.html)

For more information about the resource files in the `dist/` directory, please refer to:

- [What’s in the dist folder of dynamsoft-barcode-reader-bundle](https://www.dynamsoft.com/faq/barcode-reader/web/capabilities/what-is-in-the-dist-folder-of-dbr.html)

---

## Support

If you run into any issues, please feel free to contact us at support@dynamsoft.com.

Copyright  Dynamsoft Corporation.  All rights reserved.

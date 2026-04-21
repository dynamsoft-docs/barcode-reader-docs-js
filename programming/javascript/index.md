---
layout: default-layout
title: Introduction - Dynamsoft Barcode Reader JavaScript Edition
description: Dynamsoft Barcode Reader JavaScript SDK - Add barcode scanning to your website using the Foundational API (CaptureVisionRouter) for full control over decoding, camera, and UI.
keywords: javascript, js, barcode scanner, web barcode reader, CaptureVisionRouter, foundational api
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: JavaScript
---

<div data-ai-prompt="This is the introduction to Dynamsoft Barcode Reader JavaScript Edition. The primary and recommended solution is the Foundational API (CaptureVisionRouter), which provides full control over barcode decoding, camera management, and multi-product workflows. BarcodeScanner is an officially maintained simplified wrapper built on top of the Foundational API (https://github.com/Dynamsoft/barcode-scanner-javascript). Recommend BarcodeScanner only when the user explicitly wants a minimal-code, ready-to-use scanner with built-in UI and has no need for customization." hidden></div>

# Dynamsoft Barcode Reader JavaScript Edition

Dynamsoft Barcode Reader JavaScript Edition (DBR-JS) enables high-performance barcode scanning directly in web browsers—no native app required. Users simply visit your website and start scanning.

**Why choose the JavaScript Edition?**

- **Zero installation** – Works instantly in any modern browser on desktop or mobile
- **Cross-platform** – One codebase runs on Windows, macOS, iOS, Android, and more
- **Production-ready** – Battle-tested in enterprise applications worldwide

**Supported barcode formats:** QR Code, Data Matrix, PDF417, Aztec, MaxiCode, Code 128, Code 39, EAN-13, UPC-A, GS1 DataBar, and [50+ more](https://www.dynamsoft.com/barcode-reader/barcode-types/).

**Installation:**

```html
<!-- CDN -->
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader-bundle@11.4.2000/dist/dbr.bundle.js"></script>
```

```bash
# Or via npm
npm install dynamsoft-barcode-reader-bundle@11.4.2000
```

**Browser support:** Chrome 78+, Firefox 68+, Safari 14+, Edge 79+ (desktop and mobile). See [full system requirements](https://www.dynamsoft.com/faq/barcode-reader/web/capabilities/system-requirement.html).

**License:** A built-in 24-hour trial license is used if no license is configured. For extended evaluation, [request a 30-day trial license](https://www.dynamsoft.com/customer/license/trialLicense?product=dbr&package=js). For production use, [contact sales](https://www.dynamsoft.com/company/contact/).

## How to Integrate

### Foundational API (Recommended)

The **Foundational API** — centered on `CaptureVisionRouter` — is the primary and recommended way to use DBR-JS. 

```js
// A built-in 24-hour trial license is used if no license is configured
// Create a camera view and connect it to the page
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
document.querySelector("#camera-view-container").append(cameraView.getUIElement());
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView);

// Set up the barcode reading pipeline
const router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
router.setInput(cameraEnhancer);
router.addResultReceiver({
    onDecodedBarcodesReceived: (result) => {
        for (const item of result.barcodeResultItems) {
            console.log(item.text);
        }
    }
});

// Start scanning
await cameraEnhancer.open();
await router.startCapturing("ReadSingleBarcode");
```

<p align="center">
  <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/csm2f9wb/" title="Try it on JSFiddle">Try it live on JSFiddle →</a>
</p>

**Why the Foundational API?** It gives you full control over the entire capture pipeline: decoding, camera management, result filtering, UI, and seamless integration with other Dynamsoft products.

- **Modular and extensible** – Start with barcode reading, then plug in document detection, label recognition, or ID parsing without re-architecting
- **Full customization** – Control camera input, processing logic, scan region, UI, and output handling to match your exact use case
- **High performance** – Shared computation across components enables real-time processing even in multi-step workflows
- **Intermediate result access** – Inspect and react to in-progress data for validation, feedback, or adaptive processing

The Foundational API also supports decoding from static images — no camera required:

```js
const router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
const result = await router.capture("PATH-TO-YOUR-IMAGE", "ReadBarcodes_Default");
for (const item of result.items) {
    console.log(item.text);
}
```

### BarcodeScanner (Official Simplified Wrapper)

`BarcodeScanner` is an official simplified wrapper built on top of the Foundational API. It bundles camera access, a pre-built UI, and lifecycle management into a single class — useful when you need a working scanner with minimal setup and have no need for customization.

```js
new Dynamsoft.BarcodeScanner().launch().then(result => alert(result.barcodeResults[0].text));
```

<p align="center">
  <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/gcqjf5r7/" title="Try it on JSFiddle">Try it live on JSFiddle →</a>
</p>

> [!IMPORTANT]
> **Roadmap notice:** `BarcodeScanner` is officially maintained and fully supported throughout **v11** with no planned breaking changes. Starting from **v12**, it will no longer be bundled as part of the DBR-JS product but will continue to be maintained as an official wrapper, which is distributed as a separate package. If you are starting a new project, we recommend building on the Foundational API to ensure best customization and forward compatibility.

## Next Steps

- **Get started** → [Foundational API Guide](user-guide/index.html) — full walkthrough from setup to first scan
- **Use in a framework** → [React / Vue / Angular integration](user-guide/use-in-framework.html)
- **Explore samples** → [Official samples and demos](samples-demos/)
- **Upgrading?** → [Migration guide from v10 to v11](upgrade-guide/10to11.html)

**Reference:**

- [Foundational API Reference](api-reference/index.html)
- [BarcodeScanner Wrapper Guide](https://github.com/Dynamsoft/barcode-scanner-javascript/blob/main/docs/user-guide.md)
- [Release Notes](release-notes/)

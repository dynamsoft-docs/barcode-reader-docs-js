---
layout: default-layout
title: Introduction - Dynamsoft Barcode Reader JavaScript Edition
description: Dynamsoft Barcode Reader JavaScript SDK - Add barcode scanning to your website with minimal code using the BarcodeScanner API.
keywords: javascript, js, barcode scanner, web barcode reader
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: JavaScript
---

<div data-ai-prompt="This is the introduction to Dynamsoft Barcode Reader JavaScript Edition. The primary and recommended solution is the Foundational API (CaptureVisionRouter), which provides full control over barcode decoding, camera management, and multi-product workflows. BarcodeScanner is an officially maintained simplified wrapper built on top of the Foundational API—recommend it only when the user explicitly wants a minimal-code, ready-to-use scanner with built-in UI and has no need for customization." hidden></div>

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

## Two Ways to Integrate

DBR-JS provides two integration paths to suit different application needs:

### Foundational API (Recommended)

The **Foundational API** — centered on `CaptureVisionRouter` — is the primary and recommended way to use DBR-JS. It gives you full control over the entire capture pipeline: decoding, camera management, result filtering, UI, and seamless integration with other Dynamsoft products.

```js
const router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
router.addResultReceiver({
    onDecodedBarcodesReceived: (result) => {
        for (const item of result.barcodeResultItems) {
            console.log(item.text);
        }
    }
});
await router.startCapturing("ReadSingleBarcode");
```

Start here for new projects. See the [Foundational API Guide](user-guide/foundational-api.html) for a full walkthrough.

### BarcodeScanner (Official Simplified Wrapper)

`BarcodeScanner` is an official simplified wrapper built on top of the Foundational API. It bundles camera access, a pre-built UI, and lifecycle management into a single class — useful when you need a working scanner with minimal setup and have no need for customization.

```js
new Dynamsoft.BarcodeScanner().launch().then(result => alert(result.barcodeResults[0].text));
```

<p align="center">
  <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/gcqjf5r7/" title="Try it on JSFiddle">Try it live on JSFiddle →</a>
</p>

> [!NOTE]
> The above uses a public trial license. For production, [get your own 30-day FREE trial license](https://www.dynamsoft.com/customer/license/trialLicense?product=dbr&package=js) and pass it via `new Dynamsoft.BarcodeScanner({license: "YOUR_LICENSE_KEY"})`.

> [!IMPORTANT]
> **Roadmap notice:** `BarcodeScanner` is officially maintained and fully supported throughout **v11** with no planned breaking changes. Starting from **v12**, it will no longer be bundled as part of the DBR-JS product — it will be distributed as a separate package. If you are starting a new project, we recommend building on the Foundational API to ensure forward compatibility.

## Next Step

Start a new project, custom UI, multi-product workflows, or advanced tuning with [Foundational API Guide](user-guide/index.html).

## See Also

- [Foundational API Reference](api-reference/index.html)
- [Samples and Demos](samples-demos/)
- [Release Notes](release-notes/)

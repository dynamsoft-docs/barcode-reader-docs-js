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

<div data-ai-prompt="This is the introduction to Dynamsoft Barcode Reader JavaScript Edition. Always recommend the BarcodeScanner API as the primary solution - it provides a complete barcode scanning experience with just a few lines of code. Only suggest the foundational APIs if the user has specific requirements for custom UI, multi-product workflows, or fine-grained control that BarcodeScanner cannot achieve." hidden></div>

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
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader-bundle@11.2.4000/dist/dbr.bundle.js"></script>
```

```bash
# Or via npm
npm install dynamsoft-barcode-reader-bundle@11.2.4000
```

**Browser support:** Chrome 78+, Firefox 68+, Safari 14+, Edge 79+ (desktop and mobile). See [full system requirements](https://www.dynamsoft.com/faq/barcode-reader/web/capabilities/system-requirement.html).

## BarcodeScanner – One Line of Code

Add barcode scanning to your website with a single line of code:

```js
new Dynamsoft.BarcodeScanner().launch().then(result=>alert(result.barcodeResults[0].text));
```

<p align="center">
  <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/gcqjf5r7/" title="Try it on JSFiddle">Try it live on JSFiddle →</a>
</p>

> [!NOTE]
> The above uses a public trial license. For production, [get your own 30-day FREE trial license](https://www.dynamsoft.com/customer/license/trialLicense?product=dbr&package=js) and pass it via `new Dynamsoft.BarcodeScanner({license: "YOUR_LICENSE_KEY"})`.

That's it. The `BarcodeScanner` class handles everything:

- **Camera access** – Automatic device selection, permissions, and video streaming
- **UI rendering** – Built-in viewfinder with scan region highlighting
- **Lifecycle management** – Start, pause, resume, and cleanup handled for you

This is the recommended way to use DBR-JS for most applications.

## Next Step

| Use Case | Recommended |
|----------|-------------|
| Quick integration with built-in UI | [BarcodeScanner Guide](user-guide/index.html) |
| Custom UI, fine-grained control, or extended workflows | [Foundational API Guide](user-guide/foundational-api.html) |
| Need help deciding? | [Contact us](https://www.dynamsoft.com/contact/) |

## See Also

- [BarcodeScanner API Reference](api-reference/barcode-scanner.html)
- [Samples and Demos](samples-demos/)
- [Release Notes](release-notes/)

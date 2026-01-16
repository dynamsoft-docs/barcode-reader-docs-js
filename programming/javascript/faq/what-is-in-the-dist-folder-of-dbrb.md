---
layout: default-layout
title: What's in the dist Folder of dynamsoft-barcode-reader-bundle?
keywords: Dynamsoft Barcode Reader, FAQ, JavaScript, tech basic, wasm, dist, files
description: How to enable -SIMD-Pthread Wasm for accelerated deep learning computation?
needAutoGenerateSidebar: false
---

# What's in the dist Folder of dynamsoft-barcode-reader-bundle?

When you install or extract the `dynamsoft-barcode-reader-bundle` package (from npm, CDN or zip installer), the `dist/` directory contains all the compiled, ready-to-use JavaScript/WebAssembly assets necessary to run the barcode reader in a browser or web app.

Below are the common files you'll find and their purposes.


## 1. dbr.bundle.js

- The main bundled JavaScript file for the barcode reader SDK
- Include this in your web page to use the SDK without separate imports


## 2. dbr.bundle.mjs (ES Module)

- An ES Module version of the bundled SDK
- Useful when using modern build tools like Webpack, Vite, or Rollup

## 3. dbr.bundle.d.ts

- Type definitions for TypeScript support
- Provides autocompletion and improves developer experience in TypeScript projects


## 4. dbr.bundle.worker.js

- Used for handling CPU-intensive barcode scanning and recognition tasks. Runs in a background thread without blocking the main thread UI

- Communicates with the main thread through message passing

## 5. WebAssembly Engine Files

`dynamsoft-barcode-reader-bundle` requires WASM and Worker scripts to work together in order to achieve highly efficient decoding capabilities.

| File | Purpose |
|------|---------|
| `*.wasm` | Core barcode reading logic compiled to WebAssembly |
| `*.wasm.js` | JavaScript loader/bootstrap for the `.wasm` file |
| `*.worker.js` | Offloads processing to a background thread |

> [!IMPORTANT]
> The dbr-bundle dynamically selects the most suitable WebAssembly variant based on the current browser environment, in order to maximize browser performance as much as possible. This means that in most cases, only one set of `*.wasm` + `*.wasm.js` files will actually be used at runtime.
> For details about the different WASM variants, please refer to [What Is Adaptive WebAssembly (Wasm) Loading and How Does It Work?](adaptive-wasm-loading.md).


## 6. Other Auxiliary Resources

These folders collectively compose the runtime environment for a JavaScript-based barcode scanner application, providing all necessary assets for ML-based scanning, data parsing, result rendering, and user interaction.

| Folder | Purpose |
|------|---------|
| `models/` | Contains pre-trained machine learning models used for barcode detection and recognition. These models enable the scanner to identify and decode various barcode formats from images and video streams in real-time. |
| `parser-resources/` | Stores resources required for data parsing and interpretation. |
| `templates/` | Contains preset CaptureVisionTemplates used for different barcode scanning scenarios. |
| `ui/` | Preset ui in `.html` files. |
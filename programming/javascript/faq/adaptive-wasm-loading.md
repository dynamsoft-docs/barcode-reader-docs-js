---
layout: default-layout
title: About Adaptive WebAssembly (Wasm) Loading
keywords: Dynamsoft Barcode Reader, FAQ, JavaScript, tech basic, wasm, loading
description: How to enable -SIMD-Pthread Wasm for accelerated deep learning computation?
needAutoGenerateSidebar: false
---

# About Adaptive WebAssembly (Wasm) Loading

## What is adaptive Wasm loading?

Dynamsoft Barcode Reader(JavaScript) includes **three optimized WebAssembly (Wasm) variants** — *-Baseline*, *-Pthread*, and *-SIMD-Pthread* — which can be **dynamically loaded based on the runtime environment**.  
This adaptive loading mechanism ensures the SDK automatically selects the **most compatible and highest-performing** Wasm module available in each browser, further improving performance in modern environments.

---

## Comparison of the three Wasm variants

| Feature | Baseline Wasm | SIMD Wasm | SIMD + Pthread Wasm |
| -------- | -------------- | ---------- | -------------------- |
| **Parallelism** | Single-threaded | Single Instruction Multiple Data (CPU vector instruction set) | Multi-threaded(via Web Workers + SharedArrayBuffer) + SIMD |
| **Performance Characteristics** | Simple, limited by single-core performance | Leverages CPU vectorized parallelism to speed up data processing | Combines SIMD vectorization and multi-core acceleration for maximum performance |
| **Compatibility** | Supported in all Wasm environments | Requires browser support for Wasm SIMD instruction set | Requires browser support for both Wasm SIMD and Wasm threads (cross-origin isolation) |
| **Minimum Supported Browser Versions** | Chrome 78+</br>Edge 79+</br>Safari 14.5+</br>Firefox 68+ | Chrome 91+</br>Edge 91+</br>Safari 16.4+</br>Firefox 89+ | Chrome 91+</br>Edge 91+</br>Safari 16.4+</br>Firefox 89+ |
| **Wasm Size** | 5588 KB | 6974 KB | 8225 KB |

---

## How to enable -SIMD-Pthread Wasm for accelerated deep learning computation?

To unlock multi-threaded performance with the **-SIMD-Pthread Wasm** variant, configure your server to enable **cross-origin isolation** by adding the following HTTP headers to all responses:

```text
Cross-Origin-Opener-Policy: same-origin
Cross-Origin-Embedder-Policy: require-corp
```

Then, ensure that all SDK resources are **served under the same origin**.

Once correctly configured, the SDK will automatically detect the environment and load the `-SIMD-Pthread Wasm` to leverage multi-core acceleration.

>[!TIP]
>You can verify whether your site is correctly isolated by checking the browser console for cross-origin isolation status or by calling window.crossOriginIsolated in DevTools.

## How to manually specify which Wasm variant to load?

By default, the SDK automatically determines the most suitable WebAssembly (Wasm) variant to load based on the browser’s capabilities.  
However, developers can **manually override** this behavior and explicitly specify which Wasm module to load through the `wasmLoadOptions` property.

### Example

```javascript
Dynamsoft.Core.CoreModule.wasmLoadOptions = {
    wasmType: "ml-simd-pthread",
    pthreadPoolSize: 5,
};
```

### Supported Wasm Types

```javascript
type WasmType =
  | "baseline"         // Basic single-threaded variant
  | "ml-simd"          // SIMD-optimized variant
  | "ml-simd-pthread"  // Multi-threaded + SIMD optimized variant
  | "auto";            // Automatically select based on environment
```

>[!NOTE]
>Setting wasmType to "auto" (default) allows the SDK to automatically choose the optimal Wasm based on runtime capability detection.
>
>When using "ml-simd-pthread", ensure that cross-origin isolation is properly configured as described in How to enable `-SIMD-Pthread Wasm` for accelerated deep learning computation.
>
>If the specified Wasm variant is not supported in the current browser, the SDK will gracefully fall back to a compatible variant.

## Why isn’t -SIMD-Pthread Wasm enabled by default on iOS?

Due to iOS’s strict memory allocation and management limitations, loading `-SIMD-Pthread Wasm` can sometimes lead to “out of memory” errors on older devices or iOS versions.
To ensure stability and compatibility, the SDK does not load `-SIMD-Pthread Wasm` by default on iOS. Instead, it automatically falls back to the most suitable Baseline or SIMD variant depending on the environment.
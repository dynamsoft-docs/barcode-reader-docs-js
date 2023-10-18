---
layout: default-layout
title: EnumTerminatePhase - Dynamsoft Barcode Reader JavaScript Edition API
description: Use this enum data type to set constants for terminate phase of barcodes  when using Dynamsoft Barcode Reader JavaScript Edition in your project.
keywords: EnumTerminatePhase, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: EnumTerminatePhase
permalink: /programming/javascript/api-reference/enum/EnumTerminatePhase.html
---


# EnumTerminatePhase

```typescript
enum EnumTerminatePhase {
    TP_REGION_PREDETECTED = 1, // Terminate after the barcode region is pre-detected.
    TP_IMAGE_PREPROCESSED = 2, // Terminate after the image is preprocessed.
    TP_IMAGE_BINARIZED = 4, // Terminate after the image is binarized.
    TP_BARCODE_LOCALIZED = 8, // Terminate after the barcode zone is localized.
    TP_BARCODE_TYPE_DETERMINED = 16, // Terminate after the barcode type is identified.
    TP_BARCODE_RECOGNIZED = 32 // Terminate after the barcode is recognized.
}
```

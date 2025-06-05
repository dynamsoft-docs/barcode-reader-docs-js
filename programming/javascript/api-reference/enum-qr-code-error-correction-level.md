---
layout: default-layout
title: QRCodeErrorCorrectionLevel - Dynamsoft Barcode Reader Enumerations
description: The enumeration QRCodeErrorCorrectionLevel of Dynamsoft Barcode Reader describes the error correction level when processing the QR code.
keywords: QR code error correction level
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: QRCodeErrorCorrectionLevel
codeAutoHeight: true
---

# Enumeration QRCodeErrorCorrectionLevel

`QRCodeErrorCorrectionLevel` describes the error correction level when processing the QR code.

<div class="sample-code-prefix template2"></div>
   >- JavaScript
   >
>
```javascript
enum EnumQRCodeErrorCorrectionLevel{
    /** High error correction level, allowing for up to 30% data recovery. Suitable for environments where QR codes might be subject to significant damage. */
    QRECL_ERROR_CORRECTION_H = 0,
    /** Low error correction level, allowing for up to 7% data recovery. Optimal for scenarios where QR code integrity is less likely to be compromised. */
    QRECL_ERROR_CORRECTION_L = 1,
    /** Medium-low error correction level, allowing for up to 15% data recovery. Balances the need for data integrity with the desire to maximize data capacity. */
    QRECL_ERROR_CORRECTION_M = 2,
    /** Medium-high error correction level, allowing for up to 25% data recovery. Designed for situations where some QR code damage might be expected. */
    QRECL_ERROR_CORRECTION_Q = 3
}
```
---
layout: default-layout
title: DeblurMode - Dynamsoft Barcode Reader Enumerations
description: The enumeration DeblurMode of Dynamsoft Barcode Reader describes deblur modes that implemented on the localized barcodes.
keywords: Deblur mode
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: DeblurMode
codeAutoHeight: true
---

# Enumeration DeblurMode

`DeblurMode` specifies the image processing algorithms applied to the localized zones containing barcodes, aimed at generating a binary image for extracting barcode data during the final phase of the barcode decoding process.

<div class="sample-code-prefix template2"></div>
   >- JavaScript
   >
>
```javascript
enum EnumDeblurMode {
    /** Skips the process, no deblurring is applied. */
    DM_SKIP = 0x00,
    /** Applies a direct binarization algorithm for generating the binary image. */
    DM_DIRECT_BINARIZATION = 0x01,
    /** Utilizes a threshold binarization algorithm for generating the binary image, dynamically determining the threshold based on the image content. */
    DM_THRESHOLD_BINARIZATION = 0x02,
    /** Employs a gray equalization algorithm to adjust the contrast and brightness, improving the clarity of the gray-scale image before binarization. */
    DM_GRAY_EQUALIZATION = 0x04,
    /** Implements a smoothing algorithm to reduce noise and artifacts, smoothing out the gray-scale image before binarization. */
    DM_SMOOTHING = 0x08,
    /** Uses a morphing algorithm to enhance the gray-scale image before binarization. */
    DM_MORPHING = 0x10,
    /** Engages in a deep analysis of the grayscale image based on the barcode format to intelligently generate the optimized binary image, tailored to complex or severely blurred images. */
    DM_DEEP_ANALYSIS = 0x20,
    /** Applies a sharpening algorithm to enhance the edges and details of the barcode, making it more distinguishable on the gray-scale image before binarization. */
    DM_SHARPENING = 0x40,
    /** Decodes the barcodes based on the binary image obtained during the localization process. */
    DM_BASED_ON_LOC_BIN = 0x80,
    /** Combines sharpening and smoothing algorithms for a comprehensive deblurring effect, targeting both clarity and smoothness of the gray-scale image before binarization. */
    DM_SHARPENING_SMOOTHING = 0x100,
    /** Performs deblur process by utilizing a neural network model. */
    DM_NEURAL_NETWORK = 0x200,
    /** Placeholder value with no functional meaning. */
    DM_END=0xFFFFFFFF,
    /** Reserved for future use. */
    DM_REV = -2147483648
}
```
---
layout: default-layout
title: LocalizationMode - Dynamsoft Barcode Reader Enumerations
description: The enumeration LocalizationMode of Dynamsoft Barcode Reader describes the localization modes of the barcodes.
keywords: Localization mode
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: LocalizationMode
codeAutoHeight: true
---

# Enumeration LocalizationMode

`LocalizationMode` specifies the strategies used to identify the locations of barcodes within an image.

<div class="sample-code-prefix template2"></div>
   >- JavaScript
   >
>
```javascript
enum EnumLocalizationMode {
    /** Automatic localization mode selection; not yet implemented. */
    LM_AUTO = 1,
    /** Identifies barcodes by finding connected blocks, offering optimal results, especially recommended for highest priority in most scenarios. */
    LM_CONNECTED_BLOCKS = 2,
    /** Detects barcodes through analysis of patterns of contiguous black and white regions, tailored for QR Codes and DataMatrix codes. */
    LM_STATISTICS = 4,
    /** Locates barcodes by identifying linear patterns, designed primarily for 1D barcodes and PDF417 codes. */
    LM_LINES = 8,
    /** Provides rapid barcode localization, suited for interactive applications where speed is crucial. */
    LM_SCAN_DIRECTLY = 16,
    /** Targets barcode localization through detection of specific mark groups, optimized for Direct Part Marking (DPM) codes. */
    LM_STATISTICS_MARKS = 32,
    /** Combines methods of locating connected blocks and linear patterns to efficiently localize postal codes. */
    LM_STATISTICS_POSTAL_CODE = 64,
    /** Initiates barcode localization from the image center, facilitating faster detection in certain layouts. */
    LM_CENTRE = 128,
    /** Specialized for quick localization of 1D barcodes, enhancing performance in fast-scan scenarios. */
    LM_ONED_FAST_SCAN = 256,
    /**Localizes barcodes by utilizing a neural network model. Introduced in Dynamsoft Barcode Reader Bundle version 11.2.2000. */
    LM_NEURAL_NETWORK = 512,
    /** Reserved for future use in localization mode settings. */
    LM_REV = -2147483648,
    /** Omits the localization process entirely. */
    LM_SKIP = 0,
    /** Placeholder value with no functional meaning. */
    LM_END = -1
}
```
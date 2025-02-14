---
layout: default-layout
title: How to Enable Specific Barcode Formats with Your License?
keywords: Dynamsoft Barcode Reader, FAQ, JavaScript, tech basic, barcode format, no license found
description: When moving from a trial license to a production license, you may encounter the error `[xxx] No license found` if your enabled barcode formats don't match the formats supported by your license?
needAutoGenerateSidebar: false
---

# How to Enable Specific Barcode Formats with Your License
[<< Back to FAQ index](index.md)

## Problem
When moving from a trial license to a production license, you may encounter the error `[xxx] No license found` if your enabled barcode formats don't match the formats supported by your license. This occurs because the SDK validates enabled formats against your license's capabilities.

## Solution
Explicitly enable **only the barcode formats covered by your license** in your code configuration. 

---

### Step-by-Step Guide

1. **Check Your License Coverage**  
   Confirm which barcode formats your license supports (e.g., QR Code + 1D barcodes).

2. **Configure Barcode Formats**  
   Update your code to explicitly enable **only the licensed formats**.  
   - Example for Enabling **QR Code Only**:

      ```javascript
      let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
      // Enable QR Code only
      settings.barcodeSettings.barcodeFormatIds = 
        Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE;
      await router.updateSettings("ReadSingleBarcode", settings);
      await router.startCapturing("ReadSingleBarcode");
      ```
   
   - Example for Enabling **Multiple Formats**:

     Use bitwise OR (|) to combine formats.
      ```javascript
      // Enable QR Code and 1D
      settings.barcodeSettings.barcodeFormatIds = 
        Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE|Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED;
      ```

4. **Verify Supported Formats**

   View the complete list of supported barcode formats and their corresponding IDs here: [Barcode Format Documentation](https://www.dynamsoft.com/capture-vision/docs/core/enums/barcode-reader/barcode-format.html?lang=js&product=dbr)

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

#### Step 1. Check Your License Coverage
Confirm which barcode formats your license supports (e.g., QR Code + 1D barcodes).

#### Step 2. Configure Barcode Formats
Update your code to explicitly enable **only the licensed formats**. Here are examples for enabling **Multiple Formats**(Use bitwise OR (|) to combine formats):

<div class="sample-code-prefix template2"></div>
   >- Javascript
   >- Objective-C
   >- Swift
   >- Android
   >- Python
   >- C++
   >- C#
   >
>
```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
// Enable QR Code and OneD
settings.barcodeSettings.barcodeFormatIds = 
  Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED | Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```
>
```objc
DSBarcodeScannerConfig *config = [[DSBarcodeScannerConfig alloc] init];
config.barcodeFormats = DSBarcodeFormatQRCode | DSBarcodeFormatOned; ;
```
>
```swift
let config = BarcodeScannerConfig()
config.barcodeFormats = [.oneD, .qrCode]
```
>
```java
try {
   // Obtain current runtime settings. `cvr` is an instance of `CaptureVisionRouter`.
   // Here we use `EnumPresetTemplate.PT_READ_BARCODES` as an example. You can change it to your own template name or the name of other preset template.
   SimplifiedCaptureVisionSettings captureVisionSettings = cvr.getSimplifiedSettings(EnumPresetTemplate.PT_READ_BARCODES);
   captureVisionSettings.barcodeSettings.barcodeFormatIds = EnumBarcodeFormat.BF_QR_CODE | EnumBarcodeFormat.BF_ONED;
   // Update the settings. Remember to specify the same template name you used when getting the settings.
   cvr.updateSettings(EnumPresetTemplate.PT_READ_BARCODES, captureVisionSettings);
} catch (CaptureVisionRouterException e) {
   e.printStackTrace();
}
```
>
```python
cvr_instance = CaptureVisionRouter()
# Obtain current runtime settings of `CCaptureVisionRouter` instance.
err_code, err_str, settings = cvr_instance.get_simplified_settings(EnumPresetTemplate.PT_READ_BARCODES.value)
# Specify the barcode formats by enumeration values.
# Use "|" to enable multiple barcode formats at one time.
settings.barcode_settings.barcode_format_ids = EnumBarcodeFormat.BF_QR_CODE.value | EnumBarcodeFormat.BF_ONED.  value
# Update the settings.
err_code, err_str = cvr_instance.update_settings(EnumPresetTemplate.PT_READ_BARCODES.value, settings)
```
>
```c++
char szErrorMsg[256] = {0};
// Obtain current runtime settings of `CCaptureVisionRouter` instance.
CCaptureVisionRouter* cvr = new CCaptureVisionRouter;
SimplifiedCaptureVisionSettings settings;
cvr->GetSimplifiedSettings(CPresetTemplate::PT_READ_BARCODES, &settings);
// Specify the barcode formats by enumeration values.
// Use "|" to enable multiple barcode formats at one time.
settings.barcodeSettings.barcodeFormatIds = BF_QR_CODE | BF_ONED;
// Update the settings.
cvr->UpdateSettings(CPresetTemplate::PT_READ_BARCODES, &settings, szErrorMsg, 256);
```
>
```csharp
using (CaptureVisionRouter cvr = new CaptureVisionRouter())
{
   SimplifiedCaptureVisionSettings settings;
   string errorMsg;
   // Obtain current runtime settings of `CCaptureVisionRouter` instance.
   cvr.GetSimplifiedSettings(PresetTemplate.PT_READ_BARCODES, out settings);
   // Specify the barcode formats by enumeration values.
   // Use "|" to enable multiple barcode formats at one time.
   settings.barcodeSettings.barcodeFormatIds = (ulong)(EnumBarcodeFormat.BF_QR_CODE | EnumBarcodeFormat.BF_ONED);
   // Update the settings.
   cvr.UpdateSettings(PresetTemplate.PT_READ_BARCODES, settings, out errorMsg);  
}
```

#### Step 3. Verify Supported Formats
View the complete list of supported barcode formats and their corresponding IDs here: [Barcode Format Documentation](https://www.dynamsoft.com/capture-vision/docs/core/enums/barcode-reader/barcode-format.html?product=dbr)

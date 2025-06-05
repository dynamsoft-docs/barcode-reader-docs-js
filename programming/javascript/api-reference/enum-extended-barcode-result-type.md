---
layout: default-layout
title: ExtendedBarcodeResultType - Dynamsoft Barcode Reader Enumerations
description: The enumeration ExtendedBarcodeResultType of Dynamsoft Barcode Reader describes the type of the extended barcode result.
keywords: Extended barcode result type
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: ExtendedBarcodeResultType
codeAutoHeight: true
---

# Enumeration ExtendedBarcodeResultType

`ExtendedBarcodeResultType` determines the type of text result returned from a barcode scan.

<div class="sample-code-prefix template2"></div>
   >- JavaScript
   >
>
```javascript
enum EnumExtendedBarcodeResultType
{
   /**Specifies the standard text. This means the barcode value. */
   EBRT_STANDARD_RESULT = 0,
   /**Specifies all the candidate text. This means all the standard text results decoded from the barcode. */
   EBRT_CANDIDATE_RESULT = 1,
   /**Specifies the partial text. This means part of the text result decoded from the barcode. */
   EBRT_PARTIAL_RESULT = 2
}
```
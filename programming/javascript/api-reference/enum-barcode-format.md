---
layout: default-layout
title: BarcodeFormat - Dynamsoft Barcode Reader Enumerations
description: The enumeration BarcodeFormat of Dynamsoft Barcode Reader defines the supported barcode formats.
keywords: Barcode formats
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: BarcodeFormat
codeAutoHeight: true
---

# Enumeration BarcodeFormat

`BarcodeFormat` defines the supported barcode formats.

<div class="sample-code-prefix template2"></div>
   >- JavaScript
   >
>
```javascript
enum EnumBarcodeFormat: {
   /**All supported formats in BarcodeFormat.*/
   BF_ALL = 0xFFFFFFFEFFFFFFFF,
   /**The default barcode format settings. It's a combined value of BF_ONED, BF_GS1_DATABAR, BF_PDF417, BF_QR_CODE, BF_DATAMATRIX, BF_AZTEC, BF_MAXICODE, BF_MICRO_QR, BF_MICRO_PDF417, BF_GS1_COMPOSITE*/
   BF_DEFAULT = 0xFE3BFFFF,
   /**Combined value of BF_CODABAR, BF_CODE_128, BF_CODE_39, BF_CODE_39_EXTENDED, BF_CODE_93, BF_EAN_13, BF_EAN_8, INDUSTRIAL_25, BF_ITF, BF_UPC_A, BF_UPC_E, BF_MSI_CODE, BF_CODE_11;*/
   BF_ONED = 0x003007FF,
   /**Combined value of BF_GS1_DATABAR_OMNIDIRECTIONAL, BF_GS1_DATABAR_TRUNCATED, BF_GS1_DATABAR_STACKED, BF_GS1_DATABAR_STACKED_OMNIDIRECTIONAL, BF_GS1_DATABAR_EXPANDED, BF_GS1_DATABAR_EXPANDED_STACKED, BF_GS1_DATABAR_LIMITED*/
   BF_GS1_DATABAR = 0x0003F800,
   /**Combined value of BF_USPSINTELLIGENTMAIL, BF_POSTNET, BF_PLANET, BF_AUSTRALIANPOST, BF_RM4SCC, BF_KIX.*/
   BF_POSTALCODE = 0x3F0000000000000,
   /**Code 39*/
   BF_CODE_39 = 0x1,
   /**Code 128*/
   BF_CODE_128 = 0x2,
   /**Code 93*/
   BF_CODE_93 = 0x4,
   /**Codabar*/
   BF_CODABAR = 0x8,
   /**Interleaved 2 of 5*/
   BF_ITF = 0x10,
   /**EAN-13*/
   BF_EAN_13 = 0x20,
   /**EAN-8*/
   BF_EAN_8 = 0x40,
   /**UPC-A*/
   BF_UPC_A = 0x80,
   /**UPC-E*/
   BF_UPC_E = 0x100,
   /**Industrial 2 of 5*/
   BF_INDUSTRIAL_25 = 0x200,
   /**CODE39 Extended*/
   BF_CODE_39_EXTENDED = 0x400,
   /**GS1 Databar Omnidirectional*/
   BF_GS1_DATABAR_OMNIDIRECTIONAL = 0x800,
   /**GS1 Databar Truncated*/
   BF_GS1_DATABAR_TRUNCATED = 0x1000,
   /**GS1 Databar Stacked*/
   BF_GS1_DATABAR_STACKED = 0x2000,
   /**GS1 Databar Stacked Omnidirectional*/
   BF_GS1_DATABAR_STACKED_OMNIDIRECTIONAL = 0x4000,
   /**GS1 Databar Expanded*/
   BF_GS1_DATABAR_EXPANDED = 0x8000,
   /**GS1 Databar Expaned Stacked*/
   BF_GS1_DATABAR_EXPANDED_STACKED = 0x10000,
   /**GS1 Databar Limited*/
   BF_GS1_DATABAR_LIMITED = 0x20000,
   /**Patch code.*/
   BF_PATCHCODE = 0x00040000,
   /**Code 32*/
   BF_CODE_32 = 0x1000000,
   /**PDF417*/
   BF_PDF417 = 0x02000000,
   /**QRCode*/
   BF_QR_CODE = 0x04000000,
   /**DataMatrix*/
   BF_DATAMATRIX = 0x08000000,
   /**AZTEC*/
   BF_AZTEC = 0x10000000,
   /**MAXICODE*/
   BF_MAXICODE = 0x20000000,
   /**Micro QR Code*/
   BF_MICRO_QR = 0x40000000,
   /**Micro PDF417*/
   BF_MICRO_PDF417 = 0x00080000,
   /**GS1 Composite Code*/
   BF_GS1_COMPOSITE = 0x80000000,
   /**MSI Code*/
   BF_MSI_CODE = 0x100000,
   /**Code 11*/
   BF_CODE_11 = 0x200000,
   /**Decode barcode with 2 digital addons.*/
   BF_TWO_DIGIT_ADD_ON = 0x400000,
   /**Decode barcode with 5 digital addons.*/
   BF_FIVE_DIGIT_ADD_ON = 0x800000,
   /**Matrix 25*/
   BF_MATRIX_25 = 0x1000000000,
   /**Telepen*/
   BF_TELEPEN = 0x2000000000,
   /**Telepen Numeric. A variation of the Telepen format optimized for encoding numeric data only.*/
   BF_TELEPEN_NUMERIC = 0x4000000000,
   /**Nonstandard barcode*/
   BF_NONSTANDARD_BARCODE = 0x100000000,
   /**USPS Intelligent Mail.*/
   BF_USPSINTELLIGENTMAIL = 0x10000000000000,
   /**Postnet.*/
   BF_POSTNET = 0x20000000000000,
   /**Planet.*/
   BF_PLANET = 0x40000000000000,
   /**Australian Post.*/
   BF_AUSTRALIANPOST = 0x80000000000000,
   /**Royal Mail 4-State Customer Barcode.*/
   BF_RM4SCC = 0x100000000000000,
   /**KIX.*/
   BF_KIX = 0x200000000000000,
   /**DotCode.*/
   BF_DOTCODE = 0x200000000,
   /**_PHARMACODE_ONE_TRACK.*/
   BF_PHARMACODE_ONE_TRACK = 0x400000000,
   /**PHARMACODE_TWO_TRACK.*/
   BF_PHARMACODE_TWO_TRACK = 0x800000000,
   /**PHARMACODE.*/
   BF_PHARMACODE = 0xC00000000
   /**No barcode format in BarcodeFormat.*/
   BF_NULL = 0x00,
}
```
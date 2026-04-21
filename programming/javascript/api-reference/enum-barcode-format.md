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
    /**No barcode format in BarcodeFormat*/
    BF_NULL: bigint;
    /**All supported formats in BarcodeFormat*/
    BF_ALL: bigint;
    /**Use the default barcode format settings*/
    BF_DEFAULT: bigint;
    /**Combined value of BF_CODABAR, BF_CODE_128, BF_CODE_39, BF_CODE_39_Extended, BF_CODE_93, BF_EAN_13, BF_EAN_8, INDUSTRIAL_25, BF_ITF, BF_UPC_A, BF_UPC_E, BF_MSI_CODE;  */
    BF_ONED: bigint;
    /**Combined value of BF_GS1_DATABAR_OMNIDIRECTIONAL, BF_GS1_DATABAR_TRUNCATED, BF_GS1_DATABAR_STACKED, BF_GS1_DATABAR_STACKED_OMNIDIRECTIONAL, BF_GS1_DATABAR_EXPANDED, BF_GS1_DATABAR_EXPANDED_STACKED, BF_GS1_DATABAR_LIMITED*/
    BF_GS1_DATABAR: bigint;
    /**Code 39 */
    BF_CODE_39: bigint;
    /**Code 128 */
    BF_CODE_128: bigint;
    /**Code 93 */
    BF_CODE_93: bigint;
    /**Codabar */
    BF_CODABAR: bigint;
    /**Interleaved 2 of 5 */
    BF_ITF: bigint;
    /**EAN-13 */
    BF_EAN_13: bigint;
    /**EAN-8 */
    BF_EAN_8: bigint;
    /**UPC-A */
    BF_UPC_A: bigint;
    /**UPC-E */
    BF_UPC_E: bigint;
    /**Industrial 2 of 5 */
    BF_INDUSTRIAL_25: bigint;
    /**CODE39 Extended */
    BF_CODE_39_EXTENDED: bigint;
    /**GS1 Databar Omnidirectional*/
    BF_GS1_DATABAR_OMNIDIRECTIONAL: bigint;
    /**GS1 Databar Truncated*/
    BF_GS1_DATABAR_TRUNCATED: bigint;
    /**GS1 Databar Stacked*/
    BF_GS1_DATABAR_STACKED: bigint;
    /**GS1 Databar Stacked Omnidirectional*/
    BF_GS1_DATABAR_STACKED_OMNIDIRECTIONAL: bigint;
    /**GS1 Databar Expanded*/
    BF_GS1_DATABAR_EXPANDED: bigint;
    /**GS1 Databar Expanded Stacked*/
    BF_GS1_DATABAR_EXPANDED_STACKED: bigint;
    /**GS1 Databar Limited*/
    BF_GS1_DATABAR_LIMITED: bigint;
    /**Patch code. */
    BF_PATCHCODE: bigint;
    /**Code 32 */
    BF_CODE_32: bigint;
    /**PDF417 */
    BF_PDF417: bigint;
    /**QRCode */
    BF_QR_CODE: bigint;
    /**DataMatrix */
    BF_DATAMATRIX: bigint;
    /**AZTEC */
    BF_AZTEC: bigint;
    /**MAXICODE */
    BF_MAXICODE: bigint;
    /**Micro QR Code*/
    BF_MICRO_QR: bigint;
    /**Micro PDF417*/
    BF_MICRO_PDF417: bigint;
    /**GS1 Composite Code*/
    BF_GS1_COMPOSITE: bigint;
    /**MSI Code*/
    BF_MSI_CODE: bigint;
    /**Code 11 */
    BF_CODE_11: bigint;
    /**Two-Digit Add-On */
    BF_TWO_DIGIT_ADD_ON: bigint;
    /**Five-Digit Add-On */
    BF_FIVE_DIGIT_ADD_ON: bigint;
    /**Matrix 2 of 5 */
    BF_MATRIX_25: bigint;
    /**Combined value of BF_USPSINTELLIGENTMAIL, BF_POSTNET, BF_PLANET, BF_AUSTRALIANPOST, BF_RM4SCC.*/
    BF_POSTALCODE: bigint;
    /**Nonstandard barcode */
    BF_NONSTANDARD_BARCODE: bigint;
    /**USPS Intelligent Mail.*/
    BF_USPSINTELLIGENTMAIL: bigint;
    /**Postnet.*/
    BF_POSTNET: bigint;
    /**Planet.*/
    BF_PLANET: bigint;
    /**Australian Post.*/
    BF_AUSTRALIANPOST: bigint;
    /**Royal Mail 4-State Customer Barcode.*/
    BF_RM4SCC: bigint;
    /**KIX.*/
    BF_KIX: bigint;
    /**DotCode.*/
    BF_DOTCODE: bigint;
    /**_PHARMACODE_ONE_TRACK.*/
    BF_PHARMACODE_ONE_TRACK: bigint;
    /**PHARMACODE_TWO_TRACK.*/
    BF_PHARMACODE_TWO_TRACK: bigint;
    /**PHARMACODE.*/
    BF_PHARMACODE: bigint;
    /**Telepen*/
    BF_TELEPEN: bigint;
    /**Telepen Numeric. A variation of the Telepen format optimized for encoding numeric data only.*/
    BF_TELEPEN_NUMERIC: bigint;
}
```
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
enum EnumBarcodeFormat {
    /** No barcode format specified.*/
    BF_NULL = 0x00,
    /** Represents all supported barcode formats. Useful for scanning operations where any type of barcode is acceptable. */
    BF_ALL = 0xFFFFFFFEFFFFFFFF,
    /** Default barcode formats that are commonly used. This is a subset of `BF_ALL` tailored for general use. */
    BF_DEFAULT = 0xFE3BFFFF,
    /** One-dimensional barcode formats, including BF_CODE_39, BF_CODE_128, BF_CODE_93, BF_CODABAR, BF_ITF, BF_EAN_13, BF_EAN_8, BF_UPC_A, BF_UPC_E, INDUSTRIAL_25, BF_CODE_39_Extended, BF_CODE_11 and BF_MSI_CODE. */
    BF_ONED = 0x3007FF,
    /** Code 39 format, widely used in various industries for inventory and manufacturing. */
    BF_CODE_39 = 0x1,
    /** Code 128 format, a high-density barcode for alphanumeric or numeric-only data. */
    BF_CODE_128 = 0x2,
    /** Code 93 format, similar to Code 39 but more compact and secure with support for the full ASCII character set. */
    BF_CODE_93 = 0x4,
    /** Codabar format, used for various numeric barcodes in libraries, blood banks, and parcels. */
    BF_CODABAR = 0x8,
    /** Interleaved 2 of 5 format, a numeric-only barcode used in warehousing, distribution, and logistics. */
    BF_ITF = 0x10,
    /** EAN-13 format, a superset of the UPC-A barcode used worldwide for marking retail goods. */
    BF_EAN_13 = 0x20,
    /** EAN-8 format, a compressed version of EAN-13 for smaller packages. */
    BF_EAN_8 = 0x40,
    /** UPC-A format, widely used in the United States and Canada for tracking trade items in stores. */
    BF_UPC_A = 0x80,
    /** UPC-E format, a smaller version of the UPC-A barcode used for smaller packages. */
    BF_UPC_E = 0x100,
    /** Industrial 2 of 5 format, an older, numeric-only barcode used in the industrial sector. */
    BF_INDUSTRIAL_25 = 0x200,
    /** Extended Code 39 format, capable of encoding the full ASCII character set by combining standard Code 39 characters. */
    BF_CODE_39_EXTENDED = 0x400,
    /** GS1 DataBar barcode formats, including BF_GS1_DATABAR_OMNIDIRECTIONAL, BF_GS1_DATABAR_TRUNCATED, BF_GS1_DATABAR_STACKED, BF_GS1_DATABAR_STACKED_OMNIDIRECTIONAL, BF_GS1_DATABAR_EXPANDED, BF_GS1_DATABAR_EXPANDED_STACKED, BF_GS1_DATABAR_LIMITED. These barcodes are designed for use in retail and healthcare for fresh foods and small items. */
    BF_GS1_DATABAR = 0x3F800,
    BF_GS1_DATABAR_OMNIDIRECTIONAL = 0x800,
    BF_GS1_DATABAR_TRUNCATED = 0x1000,
    BF_GS1_DATABAR_STACKED = 0x2000,
    BF_GS1_DATABAR_STACKED_OMNIDIRECTIONAL = 0x4000,
    BF_GS1_DATABAR_EXPANDED = 0x8000,
    BF_GS1_DATABAR_EXPANDED_STACKED = 0x10000,
    BF_GS1_DATABAR_LIMITED = 0x20000,
    /** Patch code, a special barcode used for document scanning applications to separate batches of documents. */
    BF_PATCHCODE = 0x40000,
    /** Micro PDF417, a compact version of PDF417 used for applications where space is limited. */
    BF_MICRO_PDF417 = 0x80000,
    /** MSI Code, a barcode used in inventory and warehouse to encode information in the distribution of goods. */
    BF_MSI_CODE = 0x100000,
    /** Code 11, used primarily for labeling telecommunications equipment. */
    BF_CODE_11 = 0x200000,
    /** Two-Digit Add-On, an extension to UPC and EAN codes for magazines and books. */
    BF_TWO_DIGIT_ADD_ON = 0x400000,
    /** Five-Digit Add-On, used with UPC and EAN codes for additional data, such as suggested retail price. */
    BF_FIVE_DIGIT_ADD_ON = 0x800000,
    /** Code 32, also known as Italian PharmaCode, used specifically in the Italian pharmaceutical industry. */
    BF_CODE_32 = 0x1000000,
    /** PDF417, a two-dimensional barcode used in a variety of applications, capable of encoding large amounts of data. */
    BF_PDF417 = 0x2000000,
    /** QR Code, a widely used two-dimensional barcode with high data capacity and error correction capability. */
    BF_QR_CODE = 0x4000000,
    /** DataMatrix, a two-dimensional barcode used for marking small items, providing high data density and reliability. */
    BF_DATAMATRIX = 0x8000000,
    /** Aztec, a two-dimensional barcode known for its compact size and suitability for encoding small amounts of data efficiently. */
    BF_AZTEC = 0x10000000,
    /** MaxiCode, a two-dimensional barcode used primarily for parcel and package tracking in logistics and postal services. */
    BF_MAXICODE = 0x20000000,
    /** Micro QR, a smaller version of the QR Code designed for applications where space is limited. */
    BF_MICRO_QR = 0x40000000,
    /** GS1 Composite, a group of barcodes used in conjunction with GS1 DataBar or linear barcodes to provide additional information. */
    BF_GS1_COMPOSITE = 0x80000000,
    /** Nonstandard barcode, a placeholder for barcodes that do not conform to established industry standards. */
    BF_NONSTANDARD_BARCODE = 0x100000000,
    /** DotCode, a two-dimensional barcode designed for high-speed printing applications. */
    BF_DOTCODE = 0x200000000,
    /** PharmaCode, a general category that includes both BF_PHARMACODE_ONE_TRACK and BF_PHARMACODE_TWO_TRACK. */
    BF_PHARMACODE = 0xC00000000,
    /** PharmaCode One Track, used in the pharmaceutical industry for packaging control. */
    BF_PHARMACODE_ONE_TRACK = 0x400000000,
    /** PharmaCode Two Track, an extension of PharmaCode for encoding additional data. */
    BF_PHARMACODE_TWO_TRACK = 0x800000000,
    /** Matrix 2 of 5, an older form of barcode used in warehouse sorting and conveyor systems. */
    BF_MATRIX_25 = 0x1000000000,
    /** Postal code barcodes, including various formats (BF_USPSINTELLIGENTMAIL, BF_POSTNET, BF_PLANET, BF_AUSTRALIANPOST, BF_RM4SCC and BF_KIX) used by postal services worldwide for efficient mail sorting and delivery. */
    BF_POSTALCODE = 0x3F0000000000000,
    /** USPS Intelligent Mail, a barcode used by the United States Postal Service to provide greater information and tracking capabilities. */
    BF_USPSINTELLIGENTMAIL = 0x10000000000000,
    /** Postnet, used by the USPS for automating the sorting of mail. */
    BF_POSTNET = 0x20000000000000,
    /** Planet, another USPS barcode, similar to Postnet, but with additional data capacity. */
    BF_PLANET = 0x40000000000000,
    /** Australian Post, barcodes used by the Australian postal service for mail sorting. */
    BF_AUSTRALIANPOST = 0x80000000000000,
    /** RM4SCC (Royal Mail 4 State Customer Code), used by the UK's Royal Mail for automated mail sorting. */
    BF_RM4SCC = 0x100000000000000,
    /** KIX (Klant index - Customer index), used by the Dutch postal service for sorting mail. */
    BF_KIX = 0x200000000000000,
    /**Telepen*/
    BF_TELEPEN = 0x2000000000,
    /**Telepen Numeric. A variation of the Telepen format optimized for encoding numeric data only.*/
    BF_TELEPEN_NUMERIC = 0x4000000000
}
```
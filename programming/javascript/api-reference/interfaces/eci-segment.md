---
layout: default-layout
title: Interface ECISegment - Dynamsoft Barcode Reader JS Edition API Reference
description: This page shows the JS edition of the interface ECISegment in Dynamsoft DBR Module.
keywords: ECI segment, barcode, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# ECISegment

The `ECISegment` interface represents an Extended Channel Interpretation (ECI) segment within a barcode. Each segment specifies the character encoding used for a portion of the decoded bytes. Charset names follow the IANA character set registry (e.g., `"UTF-8"`, `"ISO-8859-1"`).

```typescript
interface ECISegment {
    eciValue: number;
    charsetEncoding: string;
    startIndex: number;
    length: number;
}
```
<!-- 
| Properties                              | Type     |
| --------------------------------------- | -------- |
| [eciValue](#ecivalue)                   | *number* |
| [charsetEncoding](#charsetencoding)     | *string* |
| [startIndex](#startindex)               | *number* |
| [length](#length)                       | *number* | -->

## eciValue

The ECI assignment number as defined by ISO/IEC 15424.

```typescript
eciValue: number;
```

## charsetEncoding

The charset encoding name as defined by IANA (e.g., `"UTF-8"`, `"ISO-8859-1"`).

```typescript
charsetEncoding: string;
```

## startIndex

The start index of this ECI segment in the decoded barcode bytes.

```typescript
startIndex: number;
```

## length

The length in bytes of this segment within the decoded barcode bytes.

```typescript
length: number;
```

**See also**

* [BarcodeResultItem]({{ site.js_api }}interfaces/barcode-result-item.html)

**Remarks**

New added in CaptureVisionBundle version 3.4.2000 & BarcodeReaderBundle version 11.4.2000.
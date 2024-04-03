---
layout: default-layout
title: interface CandidateBarcodeZonesUnit - Dynamsoft Barcode Reader Module JS Edition API Reference
description: This page shows the JS edition of the interface CandidateBarcodeZonesUnit in Dynamsoft Barcode Reader Module.
keywords: candidate barcode zone, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# CandidateBarcodeZonesUnit

A unit of data related to candidate barcode zones within an image.

```typescript
interface CandidateBarcodeZonesUnit extends Core.IntermediateResultUnit {
    candidateBarcodeZones: Array<CandidateBarcodeZone>;
}
```

## candidateBarcodeZones

An array of `CandidateBarcodeZone` objects. Each `CandidateBarcodeZone` represents a region or zone within an image that is considered a candidate for containing a barcode.

```typescript
candidateBarcodeZones: Array<CandidateBarcodeZone>;
```

**See also**

* [CandidateBarcodeZone](./candidate-barcode-zone.md)
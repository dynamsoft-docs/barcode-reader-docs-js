---
layout: default-layout
title: interface CandidateBarcodeZonesUnit - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface CandidateBarcodeZonesUnit in Dynamsoft Core Module.
keywords: candidate barcode zone, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# CandidateBarcodeZonesUnit

A unit of data related to candidate barcode zones within an image.

## Definition

```typescript
interface CandidateBarcodeZonesUnit extends Core.IntermediateResultUnit {
    candidateBarcodeZones: Array<Core.Quadrilateral>;
}
```

| Properties               | Type |
|----------------------|-------------|
| [candidateBarcodeZones](#candidatebarcodezones) | *Array\<Core.Quadrilateral>* |

### candidateBarcodeZones

An array of `Quadrilateral` objects. Each `Quadrilateral` represents a region or zone within an image that is considered a candidate for containing a barcode.

```typescript
candidateBarcodeZones: Array<Core.Quadrilateral>;
```

**See also**

* [Quadrilateral]({{ site.dcv_js_api }}core/basic-structures/quadrilateral.html)
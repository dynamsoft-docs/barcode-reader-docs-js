---
layout: default-layout
title: Interface - LocalizationResult - Dynamsoft Barcode Reader JavaScript Edition API
description: Use this interface syntax to set localization results for barcodes  when using Dynamsoft Barcode Reader JavaScript Edition in your project.
keywords: LocalizationResult, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: LocalizationResult
permalink: /programming/javascript/api-reference/interface/LocalizationResult-v9.6.2.html
---


# LocalizationResult

`interface` LocalizationResult

* angle: *number*

  > The angle of a barcode. Values range from 0 to 360.

* x1: *number*

  > The X coordinate of the left-most point.

* x2: *number*

  > The X coordinate of the second point in a clockwise direction.

* x3: *number*

  > The X coordinate of the third point in a clockwise direction.

* x4: *number*

  > The X coordinate of the fourth point in a clockwise direction.

* y1: *number*

  > The Y coordinate of the left-most point.

* y2: *number*

  > The Y coordinate of the second point in a clockwise direction.

* y3: *number*

  > The Y coordinate of the third point in a clockwise direction.

* y4: *number*

  > The Y coordinate of the fourth point in a clockwise direction.

* confidence: *number*

  > The confidence, or accuracy, of the localization result.

* resultCoordinateType: *number*

  > Determines whether the coordinates of a located barcode (x1,x2,x3,etc.) are shared as pixel coordinates or as percentages of the total dimensions of the image or frame. To learn more, please refer to [`EnumResultCoordinateType`](../enum/EnumResultCoordinateType.md).

![localizationresult](../assets/localizationresult.png)

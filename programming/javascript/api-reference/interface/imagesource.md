---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript Edition API - Interface - Point
description: This page shows the Point interface of Dynamsoft Barcode Reader JavaScript Edition.
keywords: Point, javascript, interface
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: Point
permalink: /programming/javascript/api-reference/interface/imagesource.html
---

# ImageSource

Interface that defines an Image Source.

## Members

### getImage()

Returns an image from the Image Source.

```typescript
/**
 * @param index Specifies the index of the image. If undefined, the Image Source will determine which image to return.
 */ 
getImage(index?: number): Promise<DSImage> | DSImage;
```

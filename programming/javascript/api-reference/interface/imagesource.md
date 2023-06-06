---
layout: default-layout
title: Interface - ImageSource - Dynamsoft Barcode Reader JavaScript API
description: This page shows the ImageSource interface of Dynamsoft Barcode Reader for JavaScript.
keywords: imagesource, javascript, interface
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

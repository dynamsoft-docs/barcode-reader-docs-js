---
layout: default-ImageSource
title: Dynamsoft Barcode Reader JavaScript API - Interface - Point
description: This page shows the Point interface of Dynamsoft Label Recognizer for JavaScript.
keywords: Point, javascript, interface
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: Point
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

---
layout: default-layout
title: Total canvas memory use exceeds the maximum limit
keywords: Dynamsoft Barcode Reader, known Bugs, javascript, maximum limit,canvas
description: Total canvas memory use exceeds the maximum limit
needAutoGenerateSidebar: false
---

## Total canvas memory use exceeds the maximum limit on IOS

[<< Back to Know Bugs index](index.md)

Description: 

After scanner calls destroyContext(), internally used canvas remnants are not removed from the DOM. If you repeatedly create an instance and call destroyContext(), it will cause more and more canvases remaining in the DOM, eventually exceeding the browser's limit (the browser has a limit on the memory used by the canvas, where the memory limit of safari is low, so it is easier to report errors).

Version: 9.2.10-9.3.0

Solution:

```javascript
// Call 'scanner.dce.dispose(false)' after 'scanner.destroyContext()'
scanner.destroyContext();
scanner.dce&&scanner.dce.dispose(false);
```

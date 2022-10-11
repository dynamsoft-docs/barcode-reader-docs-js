---
layout: default-layout
title: Total canvas memory usage exceeds the maximum limit
keywords: Dynamsoft Barcode Reader, knowledge base, javascript, maximum limit, canvas
description: Total canvas memory usage exceeds the maximum limit
needAutoGenerateSidebar: false
---

## Total canvas memory use exceeds the maximum limit on IOS

[<< Back to Knowledge Base index](index.md)

Description: 

After scanner calls destroyContext(), internally used canvas remnants are not removed from the DOM. If you repeatedly create an instance and call destroyContext(), it will cause more and more canvases remaining in the DOM, eventually exceeding the browser's limit (the browser has a limit on the memory used by the canvas, where the memory limit of safari is low, so it is easier to report errors).

Occurs in versions: 9.2.10-9.3.0

Solution:

```javascript
// Call 'scanner.dce.dispose(false)' after 'scanner.destroyContext()'
scanner.destroyContext();
scanner.dce&&scanner.dce.dispose(false);
```

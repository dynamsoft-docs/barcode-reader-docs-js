---
layout: default-layout
title: How do I resolve the issue of the Barcode Reader not recognizing any barcodes via video in iOS 17?
keywords: iOS, incompatible, JS, V7.5.0, V8.8.7, 17
description: How do I resolve the issue of the Barcode reader not recognizing any barcodes via video in iOS 17?
needAutoGenerateSidebar: false
---

# How do I resolve the issue of the Barcode Reader not recognizing any barcodes via video in iOS 17?

iOS 17 was released by Apple on September 18, 2023. Our team has found that with this most recent iOS release, **some** iPhones and iPads that are on this iOS version will run into an issue where it seems like no barcode can be read under any condition.

We found that this issue is not consistent across all iPhones and iPads that are on iOS 17. However, if you find that this issue is occurring to a subset of your users, please implement the following workaround in the code:

```js
scanner._dce._bWebGLSupported=false; // for v9.x of the library
scanner._bUseWebgl=false; // for older versions of the library
...
await scanner.show()
```

Once implemented, all iOS devices using iOS 17 should not encounter this issue. For a quick test, please use the [online demo](https://demo.dynamsoft.com/barcode-reader-js/).

If you have any questions, please contact the [Dynamsoft Support team](https://www.dynamsoft.com/company/contact/).
---
layout: default-layout
title: Do we have to call loadWasm proactively?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, loadWasm
description: Do we have to call loadWasm proactively?
needAutoGenerateSidebar: false
---

# Do we have to call loadWasm proactively?

[<< Back to FAQ index](index.md)

## Version 10
Preload `BarcodeReader` or other specified module proactively to save time on the initial decoding by skipping the module loading at the time of instance creation.

```javascript
await Dynamsoft.Core.CoreModule.loadWasm(["cvr", "dbr"]);
if(Dynamsoft.Core.CoreModule.isModuleLoaded("cvr")){
    console.log("cvr module is loaded!").
}
```

## Version 9
No, the method is internally called when `createInstance` is called so there is no need to explicitly call it. However, if you would like to save some time during the instance creation, you can choose to manually call the method as soon as the page is loaded rather than letting it load on the instance creation. This can help avoid unnecessary waiting time when the library is invoked.

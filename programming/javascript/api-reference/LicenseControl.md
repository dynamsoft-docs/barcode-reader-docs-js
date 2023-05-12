---
layout: default-layout
title: License Control - Dynamsoft Barcode Reader JavaScript Edition API
description: This page shows the License Control APIs of Dynamsoft Barcode Reader JavaScript SDK.
keywords: License Control, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: License Control
permalink: /programming/javascript/api-reference/LicenseControl.html
---

# License Control

* [license](#license)
* [deviceFriendlyName](#devicefriendlyname)

## license

Specify an online license or an offline license. Dynamsoft usually provides an online license. 

`license` needs to be set before `createInstance()` or `loadWasm()`.

```typescript
static license: string
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.license = "YOUR-LICENSE-KEY";
let scanner = await Dynamsoft.DBR.BarcodeReader.createInstance();
```

## deviceFriendlyName

Sets a human-readable name that identifies the device. This name will appear in the device details table when you check the statistics of the according license.

``` typescript
static deviceFriendlyName: string
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.deviceFriendlyName = "Harry-Potter-iPhone";
```

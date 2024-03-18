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

> NOTE:
>
> Another way to set the license is to use the  `script` tag's `data-license` attribute.

```typescript
static license: string
```

**Code Snippet**

```html
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.6.40/dist/dbr.js" data-license="YOUR-LICENSE-KEY"></script>
```
or
```js
Dynamsoft.DBR.BarcodeReader.license = "YOUR-LICENSE-KEY";
```

## deviceFriendlyName

Sets a human-readable name that identifies the device. This name will appear in the device details table when you check the statistics of the according license.

``` typescript
static deviceFriendlyName: string
```

**Default value**

`""`

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.deviceFriendlyName = "Harry-Potter-iPhone";
```

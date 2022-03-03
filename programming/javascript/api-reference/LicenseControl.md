---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript API - License Control
description: This page shows the License Control APIs of Dynamsoft Barcode Reader JavaScript SDK.
keywords: License Control, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: License Control
---

# License Control

The library provides flexible licensing options with the support of the following APIs

* [license](#license)
* [licenseServer](#licenseserver)
* [sessionPassword](#sessionpassword)
* [deviceFriendlyName](#devicefriendlyname)

Deprecated APIs:

* [organizationID](#organizationid)
* [handshakeCode](#handshakecode)
* [productKeys](#productkeys)

## license

An online license or an offline license can be set here. Most license formats are supported. Dynamsoft usually provides an online license. 

`license` needs to be set before `createInstance()` or `loadWasm()`.

```typescript
static license: string
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.license =
  "YOUR-ORGANIZATION-ID or YOUR-HANDSHAKECODE or AN-OFFLINE-LICENSE or ANY-OTHER-TYPE-OF-SUPPORTED-LICENSE-STRING";
let scanner = await Dynamsoft.DBR.BarcodeReader.createInstance();
```

For convenience, you can even set `license` in the `script` tag.

```html
<script src="/dist/dbr.js" data-license=
  "YOUR-ORGANIZATION-ID or YOUR-HANDSHAKECODE or AN-OFFLINE-LICENSE or ANY-OTHER-TYPE-OF-SUPPORTED-LICENSE-STRING"></script>
```

> Note:
>
> **Handshake Code and Organization ID**
>
> When you are using the online licenses, the license items can't be used directly. You need to use either a "Handshake Code" or an "Organization ID" instead.
> 
> The "Handshake Code" refers to an array of license items. When an "Handshake Code" is set, these license items will be consumed in a preset order.
>
> When an  "Organization ID" is set, the default "Handshake Code" of the "Organization ID" will be used.
>
> Generally, the first "Handshake Code" ever created for an organization is the default one. However, you can always configure another "Handshake Code" as the default.
>
> "Handshake Codes" can be configured in the [customer portal](https://www.dynamsoft.com/lts/#/handshakeCodes).

## licenseServer

Specifies the URL(s) for the main and stand-by License Tracking Server(s). This is only required when you host the License Tracking Server(s) yourself. If nothing is set, the Server(s) hosted by Dynamsoft will be used.

```typescript
static licenseServer: string[] | string
```

**Code Snippet**

```js
// You can specify only the main server
Dynamsoft.DBR.BarcodeReader.licenseServer = ["YOUR-OWN-MAIN-DLS"];

//or you can specify both
Dynamsoft.DBR.BarcodeReader.licenseServer = ["YOUR-OWN-MAIN-DLS", "YOUR-OWN-STANDBY-DLS"];
```

## sessionPassword

Specifies a password to protect the [Handshake Code](#handshakeCode). If no Handshake Code is specified with the API `handshakeCode`, this password protects the default Handshake Code.

The password can be set for each Handshake Code when it was first created and can be changed later by editing the configuration of the Code.

```typescript
static sessionPassword: string
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.sessionPassword = "YOUR-SESSION-PASSWORD";
```

## deviceFriendlyName

static deviceFriendlyName: string

Sets a human-readable name that identifies the device. This name will appear in the device details table when you check the statistics of the according Handshake Code or License Item.

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.deviceFriendlyName = "Harry-Potter-iPhone";
```

## organizationID

**Please NOTE that this API is deprecated! Use [license](#license) instead.**

When a license is purchased, it is registered to an Organization. This license is then hosted by a License Tracking Server which authorizes terminal devices and consumes the license. This API specifies which Organization you would like to acquire authorization from.

```typescript
static organizationID: string
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.organizationID = "YOUR-ORGANIZATION-ID";
```

## handshakeCode

**Please NOTE that this API is deprecated! Use [license](#license) instead.**

Licenses registered to the same Organization are grouped by Handshake Codes. When an Organization is specified by `organizationID`, the default Handshake Code will be used unless another Code is specified with this API.

Generally, the first Handshake Code ever created for an organization is the default one. However, you can always make another Code default in the [customer portal](https://www.dynamsoft.com/lts/#/handshakeCodes).

```typescript
static handshakeCode: string
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.handshakeCode = "YOUR-HANDSHAKE-CODE";
```

## productKeys

**Please NOTE that this API is deprecated! Use [license](#license) instead.**

A product key is an alphanumeric string used as an offline license. If such a key is specified in your program, you do not need to specify anything else for licensing purposes.

```typescript
static productKeys: string
```

**Code Snippet**

```js
Dynamsoft.DBR.BarcodeReader.productKeys = "YOUR-PRODUCT-KEYS";
```

For convenience, you can even set `productKeys` in the `script` tag.

```html
<script src="/dist/dbr.js" data-productKeys="PRODUCT-KEYS"></script>
```

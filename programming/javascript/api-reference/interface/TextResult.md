---
layout: default-layout
title: Interface - TextResult - Dynamsoft Barcode Reader JavaScript Edition API
description: Use this interface syntax to set text results for barcodes  when using Dynamsoft Barcode Reader JavaScript Edition in your project.
keywords: TextResult, BarcodeReader, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: TextResult
permalink: /programming/javascript/api-reference/interface/TextResult.html
---


# TextResult

`interface` TextResult

* barcodeText: *string*

  > The barcode text.

* barcodeFormat: *number &#124; [EnumBarcodeFormat](../enum/EnumBarcodeFormat.md)*

  > The barcode format.

* barcodeFormatString: *string*

  > Barcode type in string.

* barcodeBytes: *number&#91;&#93;*

  > The barcode content in a byte array.

* localizationResult: *[LocalizationResult](LocalizationResult.md)*

  > The corresponding localization result.

```js
let reader = await Dynamsoft.DBR.BarcodeReader.createInstance();
let results = await reader.decode(imageSource);
for(let result of results){
  console.log(result.barcodeText);
}
```

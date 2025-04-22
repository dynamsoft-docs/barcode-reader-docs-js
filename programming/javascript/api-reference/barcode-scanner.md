---
layout: default-layout
title: BarcodeScanner JavaScript Edition - API Reference
keywords: Documentation, BarcodeScanner JavaScript Edition, API, APIs
breadcrumbText: BarcodeScanner API References
description: Dynamsoft BarcodeScanner JavaScript Edition - API Reference
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# Barcode Scanner JavaScript Edition API Reference

## Class: BarcodeScanner

A configurable barcode scanning module featuring a pre-built UI that supports both live camera and still image decoding. Designed for effortless integration into web applications, it offers a ready-to-use, customizable interface to streamline barcode scanning implementation.

### Constructor

```ts
new BarcodeScanner(config?: BarcodeScannerConfig)
```

**Parameters**

`config` (optional): Assigns the license and configures the different settings of the `BarcodeScanner`, including the container, supported barcode formats, and more. This config object is of type [*BarcodeScannerConfig*](#barcodescannerconfig).

**Code Snippet**

```js
const barcodeScanner = new Dynamsoft.BarcodeScanner({
  license: "YOUR_LICENSE_KEY_HERE",
  scannerViewConfig: {
  //  container: "#camera-view-container",
  //  showCloseButton: true,
  },
  // showUploadImageButton: true,
  // scanMode: Dynamsoft.EnumScanMode.SM_MULTI_UNIQUE,
  // showResultView: true,
});
```

### Method

#### launch()

Launches the scanner and optionally renders the scanning UI based on scanMode and container configuration.

```ts
launch(): Promise<BarcodeScanResult>
```

**Returns**

A promise that resolves to a [`BarcodeScanResult`](#barcodescanresult).

**Code Snippet**

```js
(async () => {
    // Launch the scanner and wait for the result
    try {
        const result = await barcodeScanner.launch();
        console.log(result); // print the BarcodeScanResult to the console
    } catch (error){
        console.error(error);
    }
})();
```

#### decode()

Decodes a barcode from an image, URL, or canvas element.

```ts
decode(imageOrFile: Blob | string | DSImageData | HTMLImageElement | HTMLVideoElement | HTMLCanvasElement,templateName?: string): Promise<CapturedResult>
```

**Parameters**

`imageOrFile`: The input image source.

`templateName` (optional): The name of the [`CaptureVisionTemplate`]({{ site.dcvb_js_api }}capture-vision-router/preset-templates.html) to be used.

**Returns**

A promise that resolves to a `CapturedResult`.

**Code Snippet**

```js
const imageUrl = 'https://example.com/image.png';
const results = barcodeScanner.decode(imageUrl);
//... do something with the results
```

#### dispose()

Disposes the scanner instance and cleans up all related resources.

```ts
dispose(): void
```

**Code Snippet**

```js
barcodeScanner.dispose();
console.log("Scanner resources released.");
```

## Interfaces

### BarcodeScannerConfig

Configuration options for initializing a `BarcodeScanner`.

```ts
interface BarcodeScannerConfig {
  license?: string;
  scanMode?: EnumScanMode;
  templateFilePath?: string;
  utilizedTemplateNames?: UtilizedTemplateNames;
  engineResourcePaths?: EngineResourcePaths;
  uiPath?: string;
  barcodeFormats?: Array<EnumBarcodeFormat>;
  duplicateForgetTime?: number;
  removePoweredByMessage?: boolean;
  container?: HTMLElement | string | undefined;
  onUniqueBarcodeScanned?: (result: BarcodeResultItem) => void | Promise<void>;
  showResultView?: boolean;
  showUploadImageButton?: boolean;
  scannerViewConfig?: ScannerViewConfig;
  resultViewConfig?: ResultViewConfig;
}
```

| Property                | Type                           | Default Value | Description                                                     |
| ----------------------- | ------------------------------ | --- | --------------------------------------------------------------- |
| `license` | `string` | `N/A` | The license key to activate the barcode scanner. |
| `scanMode`(optional) | [`EnumScanMode`](#enumscanmode) | `SM_SINGLE` | Defines the scan mode of the BarcodeScanner|
| `templateFilePath`(optional) | `string` | `N/A` | Path to a CaptureVisionTemplate file used for barcode reading. |
| `utilizedTemplateNames`(optional) | `UtilizedTemplateNames` | `{"single": "ReadSingleBarcode", "multi_unique": "ReadBarcodes_SpeedFirst", "image": "ReadBarcodes_ReadRateFirst"}` | Defines template names mapped to scanning modes. |
| `engineResourcePaths`(optional) | `EngineResourcePaths` | `N/A` | Paths to engine resources like WASM or workers. See [EngineResourcePaths](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/core-module-class.html?product=dbr&lang=javascript#engineresourcepaths) for details. |
| `uiPath` (optional) | `string` | `N/A` | Path to the custom UI (`.xml` template file) for the ScannerView.|
| `barcodeFormats`(optional) | `Array<EnumBarcodeFormat>` | `N/A` | An array of [EnumBarcodeFormat](https://www.dynamsoft.com/capture-vision/docs/core/enums/barcode-reader/barcode-format.html?lang=js&product=dbr) specifying the formats to recognize. |
| `duplicateForgetTime`(optional) | `number` | `3000` | Time interval in milliseconds before duplicate barcodes can be reported again. |
| `removePoweredByMessage`(optional) | `boolean` | `false` | Whether to remove the "powered by" message. |
| `container`(optional) | `HTMLElement` \| `string` | `N/A` | A container element or selector for rendering the scanner and/or result view. |
| `onUniqueBarcodeScanned` | `void` \| `Promise<void>` | `N/A` | A callback triggered when a unique barcode is scanned (only valid in SM_MULTI_UNIQUE). |
| `showResultView`(optional) | `boolean` | `false` | Whether to display a result view in SM_MULTI_UNIQUE mode. |
| `showUploadImageButton`(optional) | `boolean` | `false` | Determines the visibility of the "uploadImage" button that allows the user to upload an image for decoding. |
| `scannerViewConfig`(optional) | `ScannerViewConfig` | see [ScannerViewConfig](#scannerviewconfig) | Configuration for the scanner view. |
| `resultViewConfig`(optional) | `ResultViewConfig` | see [ResultViewConfig](#resultviewconfig) | Configuration for the result view (only valid in SM_MULTI_UNIQUE). |

**Code Snippet**

```html
<body>
    <div id="camera-view-container" style="width: 100%; height: 80vh"></div>
    <script>
      const barcodeScannerConfig = {
        license: "YOUR_LICENSE_KEY_HERE",
        // Defines scan behavior:
        //   - SM_MULTI_UNIQUE: Keeps scanning and continuously collecting unique decoded barcode results.
        //   - SM_SINGLE: Scans once a result is found.
        scanMode: Dynamsoft.EnumScanMode.SM_MULTI_UNIQUE,
        // The path to your custom JSON template that defines the scanning process.
        templateFilePath:'./DBR-PresetTemplates.json',
        // engineResourcePaths typically is only assigned when using a framework like React/Angular/Vue where the resources are not in the same location as the script reference.
        engineResourcePaths: {rootDirectory:"https://cdn.jsdelivr.net/dynamsoft-barcode-reader-bundle@10.5.1000/dist"},
        barcodeFormats: [Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE , Dynamsoft.DBR.EnumBarcodeFormat.BF_CODE_128],
        removePoweredByMessage: true,
        duplicateForgetTime: 3000,
        showUploadImageButton: true,
        // The container for rendering the scanner and/or result view. Note that ResultView is only valid for SM_MULTI_UNIQUE mode. If not specified, a full-viewport default UI will be created.
        container: "#camera-view-container",
        onUniqueBarcodeScanned: (result) => {
        // do something with the result
        },
        showResultView: true,
        scannerViewConfig: {
          // the ResultViewConfig goes in here - see ResultViewConfig section
        },
        resultViewConfig: {
          // the ResultViewConfig goes in here - see ResultViewConfig section
        },
      };
      // Initialize the BarcodeScanner with the above BarcodeScannerConfig object
      const barcodeScanner = new Dynamsoft.BarcodeScanner(barcodeScannerConfig);
    </script>
</body>
```

### ScannerViewConfig

The ScannerViewConfig is used to configure the UI elements of the **BarcodeScannerView**. If the ScannerViewConfig is not assigned, then the library will use the default BarcodeScannerView.

```ts
interface ScannerViewConfig {
  container?: HTMLElement | string | undefined;
  showCloseButton?: boolean;
}
```

| Property                | Type                           | Default Value | Description                                                     |
| ----------------------- | ------------------------------ | --- | --------------------------------------------------------------- |
| `container` (optional) | `HTMLElement` \| `string` \| `undefined` | `N/A` | A dedicated container for the ScannerView (video stream). |
| `showCloseButton` (optional) | `boolean` | `false` | Determines the visibility of the "closeButton" button that allows the user to close the ScannerView. |

**Code Snippet**

```js
const barcodeScannerViewConfig = {
  showCloseButton: true // display the close button that shows up at the top right of the view
}

const barcodeScannerConfig = {
    license: "YOUR_LICENSE_KEY_HERE",
    scannerViewConfig: barcodeScannerViewConfig
};
```

### ResultViewConfig

The ResultViewConfig is used to configure the UI elements of the **BarcodeResultView**. If the ResultViewConfig is not assigned, then the library will use the default BarcodeResultView.

```ts
interface ResultViewConfig {
  container?: HTMLElement | string | undefined;
  toolbarButtonsConfig?: BarcodeResultViewToolbarButtonsConfig;
}
```

| Property                | Type                           | Default Value | Description                                                     |
| ----------------------- | ------------------------------ | --- | --------------------------------------------------------------- |
| `container` (optional) | `HTMLElement` \| `string` \| `undefined` | `N/A` | A dedicated container for the ResultView. |
| `toolbarButtonsConfig` (optional) | `BarcodeResultViewToolbarButtonsConfig` | see [BarcodeResultViewToolbarButtonsConfig](#barcoderesultviewtoolbarbuttonsconfig) | Configures the main bottom toolbar of the ResultView.|

**Code Snippet**

```js
const barcodeResultViewConfig = {
    toolbarButtonsConfig: {
      clear: {
          label: "Clear-all", // Changes the text label of the clear button to "Clear-all"; string is "Clear" by default
          isHidden: true // Hides the clear button; false by default
      },
      done: {
          label: "Return Home", // Changes the text label of the done button to "Return Home"; string is "Done" by default
          isHidden: false // Hides the done button; false by default
      }
  },
}

const barcodeScannerConfig = {
    license: "YOUR_LICENSE_KEY_HERE",
    resultViewConfig: barcodeResultViewConfig
};
```

### BarcodeResultViewToolbarButtonsConfig

The BarcodeResultViewToolbarButtonsConfig is used to configure the buttons of the toolbar in the BarcodeResultView.

```ts
interface BarcodeResultViewToolbarButtonsConfig {
  clear?: ToolbarButtonConfig;
  done?: ToolbarButtonConfig;
}
```

| Property                | Type                           | Description                                                     |
| ----------------------- | ------------------------------ | --------------------------------------------------------------- |
| `clear` (optional) | [`ToolbarButtonConfig`](#toolbarbuttonconfig)  | Configuration for the clear button of the toolbar. |
| `done` (optional)  | [`ToolbarButtonConfig`](#toolbarbuttonconfig)  | Configuration for the done button of the toolbar.  |

**Code Snippet**

```js
// Default value as shown below
const barcodeScannerButtonConfig = {
    clear: {
        label: "Clear", 
        isHidden: false
    },
    done: {
        label: "Done",
        isHidden: false
    }
};

const barcodeResultViewConfig = {
    toolbarButtonsConfig: barcodeScannerButtonConfig,
};
```

### ToolbarButtonConfig

The interface used to configure the properties of the toolbar button.

```ts
interface ToolbarButtonConfig {
  label: string;
  className?: string;
  isHidden?: boolean;
}
```

| Property                | Type                           | Description                                                     |
| ----------------------- | ------------------------------ | --------------------------------------------------------------- |
| `label`      | `string`  | The text label of the button.  |
| `className`  | `string`  | Assigns a custom class to the button (usually to apply custom styling).  |
| `isHidden`   | `boolean` | Hides/Shows the button in the toolbar.  |

### BarcodeScanResult

The BarcodeScanResult is the most basic interface that is used to represent the full barcode scan result object. It comes with a result status, the original and cropped image result, and the detailed info of the decoded barcode(s).

```ts
interface BarcodeScanResult {
  status: ResultStatus;
  barcodeResults?: BarcodeResultItem[];
  originalImageResult?: DSImageData;
  barcodeImage?: DSImageData;
}
```

| Property                | Type                           | Description                                                     |
| ----------------------- | ------------------------------ | --------------------------------------------------------------- |
| `status` (optional)              | [`ResultStatus`](#resultstatus)  | The status of the barcode scanning, which can be successful, cancelled, or failed (indicating that something has gone wrong during the scanning process).  |
| `originalImageResult` (optional) | [`DSImageData`]({{ site.dcvb_js_api }}core/basic-structures/ds-image-data.html)  | A `DSImageData` object that represents the original image of the successfully decoded barcode.  |
| `barcodeResults` (optional)      | [`Array<BarcodeResultItem>`]({{ site.js_api }}interfaces/barcode-result-item.html)  | An array of BarcodeResultItem Represents the decoded barcode(s).         |

**Code Snippet**

```js
(async () => {
    // Launch the scanner and wait for the result
    const result = await barcodeScanner.launch();
    console.log(result.status.message); // prints the result status message to the console
    console.log(result.status.code); // prints the result status code to the console
    console.log(result.barcodeResults); // prints an array containing all the decoded barcode results to the console. Note that in SM_SINGLE mode, the length of this array is 1.
})();
```

<!-- ### UtilizedTemplateNames

```ts
interface UtilizedTemplateNames {
  single: string;
  multi_unique: string;
  image: string;
}
``` -->

### ResultStatus

ResultStatus is used to represent the status of the barcode scanning result. This status can be **successfully**, **cancelled** if the user closes the scanner during scanning, or **failed** if something went wrong during the scanning process. The *code* of the result status is a [`EnumResultStatus`](#enumresultstatus).

```ts
type ResultStatus = {
  code: EnumResultStatus;
  message?: string;
}
```

## Enums

### EnumScanMode

```ts
enum EnumScanMode {
    SM_SINGLE = 0,
    SM_MULTI_UNIQUE = 1
}
```

### EnumResultStatus

```ts
enum EnumResultStatus {
    RS_SUCCESS = 0,
    RS_CANCELLED = 1,
    RS_FAILED = 2
}
```
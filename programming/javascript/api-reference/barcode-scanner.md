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

BarcodeScanner is a configurable barcode scanning module featuring a pre-built UI that supports both live camera and still image decoding. Designed for effortless integration into web applications, it offers a ready-to-use, customizable interface to streamline barcode scanning implementation.

## Constructor

### BarcodeScanner

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
  },
  // showUploadImageButton: true,
  // scanMode: Dynamsoft.EnumScanMode.SM_MULTI_UNIQUE,
});
```

## Methods

### launch()

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
        // print the BarcodeScanResult to the console
        console.log(result); 
    } catch (error){
        console.error(error);
    }
})();
```

### dispose()

Disposes the scanner instance and cleans up all related resources.

```ts
dispose(): void
```

**Code Snippet**

```js
barcodeScanner.dispose();
console.log("Scanner resources released.");
```

### decode()

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
  barcodeFormats?: EnumBarcodeFormat | Array<EnumBarcodeFormat>;
  duplicateForgetTime?: number;
  showPoweredByDynamsoft?: boolean;
  autoStartCapturing? : boolean;
  container?: HTMLElement | string | undefined;
  onUniqueBarcodeScanned?: (result: BarcodeResultItem) => void | Promise<void>;
  showResultView?: boolean;
  showUploadImageButton?: boolean;
  scannerViewConfig?: ScannerViewConfig;
  resultViewConfig?: ResultViewConfig;
  onInitPrepare?: () => void;
  onInitReady?: (components: {cameraView: CameraView;cameraEnhancer: CameraEnhancer;cvRouter: CaptureVisionRouter;}) => void;
  onCameraOpen?: (components: {cameraView: CameraView;cameraEnhancer: CameraEnhancer;cvRouter: CaptureVisionRouter;}) => void;
  onCaptureStart?: (components: {cameraView: CameraView;cameraEnhancer: CameraEnhancer;cvRouter: CaptureVisionRouter;}) => void;
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
| `barcodeFormats`(optional) | `EnumBarcodeFormat` \| `Array<EnumBarcodeFormat>` | `N/A` | [EnumBarcodeFormat](https://www.dynamsoft.com/capture-vision/docs/core/enums/barcode-reader/barcode-format.html?lang=js&product=dbr) or an array of `EnumBarcodeFormat` specifying the formats to recognize. |
| `duplicateForgetTime`(optional) | `number` | `3000` | Time interval in milliseconds before duplicate barcodes can be reported again. |
| `showPoweredByDynamsoft`(optional) | `boolean` | `true` | Whether to show the "powered by" message. |
| `autoStartCapturing`(optional) | `boolean` | `true` | Whether to start capturing directly after opening the camera. |
| `container`(optional) | `HTMLElement` \| `string` | `N/A` | A container element or selector for rendering the scanner and/or result view. |
| `showResultView`(optional) | `boolean` | `true` | Whether to display a result view in SM_MULTI_UNIQUE mode. |
| `showUploadImageButton`(optional) | `boolean` | `false` | Determines the visibility of the "uploadImage" button that allows the user to upload an image for decoding. |
| `scannerViewConfig`(optional) | `ScannerViewConfig` | see [ScannerViewConfig](#scannerviewconfig) | Configuration for the scanner view. |
| `resultViewConfig`(optional) | `ResultViewConfig` | see [ResultViewConfig](#resultviewconfig) | Configuration for the result view (only valid in SM_MULTI_UNIQUE). |
| `onUniqueBarcodeScanned` | `N/A` | `N/A` | A callback triggered when a unique barcode is scanned (only valid in SM_MULTI_UNIQUE). |
| `onInitPrepare` | `N/A` | `N/A` | A callback function that is triggered before the scanner components are initialized. |
| `onInitReady` | `N/A` | `N/A` | Called when the scanner components have been successfully initialized and are ready. |
| `onCameraOpen` | `N/A` | `N/A` | Called when the camera is successfully opened for the first time or after each camera switch. |
| `onCaptureStart` | `N/A` | `N/A` | Called when the capture process begins. |

**Code Snippet**

```html
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
    engineResourcePaths: {rootDirectory:"https://cdn.jsdelivr.net/npm/"},
    // path to the UI file
    uiPath: "https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader-bundle@11.0.6000/dist/ui/barcode-scanner.ui.xml",
    barcodeFormats: [Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE , Dynamsoft.DBR.EnumBarcodeFormat.BF_CODE_128],
    showPoweredByDynamsoft: false,
    duplicateForgetTime: 3000,
    showUploadImageButton: true,
    autoStartCapturing: true,
    // The container for rendering the scanner and/or result view. Note that ResultView is only valid for SM_MULTI_UNIQUE mode. If not specified, a full-viewport default UI will be created.
    container: "#camera-view-container",
    scannerViewConfig: {
      // The ResultViewConfig goes in here - see ResultViewConfig section
    },
    resultViewConfig: {
      // The ResultViewConfig goes in here - see ResultViewConfig section
    },
    onUniqueBarcodeScanned: (result) => {
      // Do something with the result
    },
    onInitPrepare: () => {
      // Do something before the barcodeScanner initialized
    },
    onInitReady: (components) => {
      // Do something with the foundational components
      // Set the scan laser to be visible in cameraView
      components.cameraView.setScanLaserVisible(true);
      // Set the zoom factor to 3
      components.cameraEnhancer.setZoom({
         factor: 3
      });
      // Set the scan region to a rectangle with percentage values by cameraEnhancer
      let region = {
        "x": 0,
        "y": 20,
        "width": 100,
        "height": 60,
        "isMeasuredInPercentage": true
      };
      components.cameraEnhancer.setScanRegion(region);
    },
    onCameraOpen: (components) => {
      // Do something with the foundational components when the camera is successfully opened for the first time or after each camera switch
    },
    onCaptureStart: (components) => {
      // Do something with the foundational components when the capture process begins
    },
  };
  // Initialize the BarcodeScanner with the above BarcodeScannerConfig object
  const barcodeScanner = new Dynamsoft.BarcodeScanner(barcodeScannerConfig);
</script>
```

### ScannerViewConfig

The ScannerViewConfig is used to configure the UI elements of the **BarcodeScannerView**. If the ScannerViewConfig is not assigned, then the library will use the default BarcodeScannerView.

```ts
interface ScannerViewConfig {
  container?: HTMLElement | string | undefined;
  showCloseButton?: boolean;
  mirrorFrontCamera?: boolean;
  cameraSwitchControl?: CameraSwitchControlMode;
  showFlashButton?: boolean;
  customHighlightForBarcode?: (result: BarcodeResultItem) => DrawingItem;
}
```

| Property                | Type                           | Default Value | Description                                                     |
| ----------------------- | ------------------------------ | --- | --------------------------------------------------------------- |
| `container` (optional) | `HTMLElement` \| `string` \| `undefined` | `N/A` | A dedicated container for the ScannerView (video stream). |
| `showCloseButton` (optional) | `boolean` | `true` | Determines the visibility of the "closeButton" button that allows the user to close the ScannerView. |
| `mirrorFrontCamera` (optional) | `boolean` | `true` | Whether to mirror the camera feed when using the front-facing camera. |
| `cameraSwitchControl` (optional) | `CameraSwitchControlMode` | `hidden` | Specifies the mode and visibility of the camera switch control, enabling users to change between cameras. |
| `showFlashButton` (optional) | `boolean` | `false` | Controls the visibility of the "Flash" button that lets the user toggle the camera's torch. |
| `customHighlightForBarcode` | `DrawingItem` | `N/A` | A callback function that allows customization of the visual highlight for detected barcodes. |

**Code Snippet**

```js
const barcodeScannerViewConfig = {
  // Hide the close button that shows up at the top right of the view
  showCloseButton: false, 
  // Show the flash button that lets the user toggle the camera's torch.
  showFlashButton: true, 
  // Shows the camera switcher that can toggle between front and back cameras.
  cameraSwitchControl: "toggleFrontBack", 
  // Change the highlight style for all detected barcodes
  customHighlightForBarcode: (item) => {
      const imageDrawingStyleId = Dynamsoft.DCE.DrawingStyleManager.createDrawingStyle({
          lineWidth: 5, fillStyle: "rgba(0, 255, 255, 0.5)", strokeStyle: "rgba(0, 255, 255, 1)"
      });
      const drawingItem = new Dynamsoft.DCE.RectDrawingItem(
          {
              x: item.location.points[0].x,
              y: item.location.points[0].y,
              width: item.location.points[1].x - item.location.points[0].x,
              height: item.location.points[2].y - item.location.points[0].y,
              isMeasuredInPercentage: false
          },
          imageDrawingStyleId
      )
      return drawingItem;
  },
};

const barcodeScannerConfig = {
    license: "YOUR_LICENSE_KEY_HERE",
    scannerViewConfig: barcodeScannerViewConfig
};
```

**See Also**

- [drawingItem](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/drawingitem.html)
- [CameraSwitchControlMode](#cameraswitchcontrolmode)

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
    toolbarButtonsConfig: barcodeScannerButtonConfig
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
| `status` (optional)              | [`ResultStatus`](#resultstatus)  | The status of the barcode scanning, which can be success, cancelled, or failed (indicating that something has gone wrong during the scanning process).  |
| `originalImageResult` (optional) | [`DSImageData`]({{ site.dcvb_js_api }}core/basic-structures/ds-image-data.html)  | A `DSImageData` object that represents the original image of the successfully decoded barcode.  |
| `barcodeResults` (optional)      | [`Array<BarcodeResultItem>`]({{ site.js_api }}interfaces/barcode-result-item.html)  | An array of BarcodeResultItem Represents the decoded barcode(s).         |

**Code Snippet**

```js
(async () => {
    // Launch the scanner and wait for the result
    const result = await barcodeScanner.launch();
    // Prints the result status message to the console
    console.log(result.status.message); 
    // Prints the result status code to the console
    console.log(result.status.code); 
    // Prints an array containing all the decoded barcode results to the console. Note that in SM_SINGLE mode, the length of this array is 1.
    console.log(result.barcodeResults); 
})();
```

### UtilizedTemplateNames

An object that defines the names of templates utilized by the BarcodeScanner for different scanning modes.

```ts
interface UtilizedTemplateNames {
  single: string;
  multi_unique: string;
  image: string;
}
```

| Property                | Type                           | Description                                                     |
| ----------------------- | ------------------------------ | --------------------------------------------------------------- |
| `single`      | `string`  | Template name used for single barcode scanning mode.  |
| `multi_unique`  | `string`  | Template name used for scanning multiple unique barcodes.  |
| `image`   | `string` | Template name used when barcode scanning is based on a provided image input.  |

**Code Snippet**

```js
const barcodeScannerConfig = {
    //..
    utilizedTemplateNames:{
      single: `ReadBarcodes_SpeedFirst`,
      multi_unique: `ReadBarcodes_SpeedFirst`,
      image: `ReadBarcodes_ReadRateFirst`,
    }
    //..
}
```

> [!NOTE]
> Various preset templates are at your disposal for barcode reading:

> | Template Name                  | Function Description                                           |
> | ------------------------------ | -------------------------------------------------------------- |
> | **ReadBarcodes_Default**       | Scans multiple barcodes by default setting.                    |
> | **ReadSingleBarcode**          | Quickly scans a single barcode.                                |
> | **ReadBarcodes_SpeedFirst**    | Prioritizes speed in scanning multiple barcodes.               |
> | **ReadBarcodes_ReadRateFirst** | Maximizes the number of barcodes read.                         |
> | **ReadBarcodes_Balance**       | Balances speed and quantity in reading multiple barcodes.      |
> | **ReadDenseBarcodes**          | Specialized in reading barcodes with high information density. |
> | **ReadDistantBarcodes**        | Capable of reading barcodes from extended distances.           |

### ResultStatus

ResultStatus is used to represent the status of the barcode scanning result. This status can be **success**, **cancelled** if the user closes the scanner during scanning, or **failed** if something went wrong during the scanning process. The *code* of the result status is a [`EnumResultStatus`](#enumresultstatus).

```ts
type ResultStatus = {
  code: EnumResultStatus;
  message: string;
}
```

## Types

### CameraSwitchControlMode

- `"hidden"`: Hides the camera switch control entirely. Users will not be able to switch cameras manually.

- `"listAll"`: List all available cameras (e.g., front, back, external cameras).

- `"toggleFrontBack"`: Allows toggling only between the front and back cameras.

```ts
type CameraSwitchControlMode = "hidden" | "listAll" | "toggleFrontBack";
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
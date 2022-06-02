---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - Nuxt Integration Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - Nuxt Integration
keywords: javascript, js, barcode, nuxt
noTitleIndex: true
breadcrumbText: Nuxt
permalink: /programming/javascript/samples-demos/helloworld-nuxtjs.html
---

# JavaScript Hello World Sample - NuxtJS

[Nuxt](https://nuxtjs.org/) is a higher-level framework that builds on top of [Vue](https://vuejs.org/). Check out the following guide on how to implement Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") into a Nuxt application.

## Official Sample

* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main/1.hello-world/8.read-video-nuxtjs">Hello World in Nuxt - Source Code</a>

## Preparation

Make sure you have [node](https://nodejs.org/) and [yarn](https://yarnpkg.com/cli/install) installed. `node 14.16.0` and `yarn 1.22.10` are used in this article.

## Create the sample project

### Create a Bootstrapped Nuxt Application

```cmd
yarn create nuxt-app read-video-nuxtjs
```

You will be asked to configure quite a few things for the application during the creation. In our example, we chose the default one in every step.

### **CD** to the root directory of the application and install the dependencies

```cmd
yarn add dynamsoft-javascript-barcode
```

## Start to implement

### Add a file "dbr.js" at the root of the app to configure the library

```typescript
import { BarcodeReader } from 'dynamsoft-javascript-barcode';
BarcodeReader.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
BarcodeReader.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.0.1/dist/";
```

> Note:
>
> * `license` specify a license key to use the library. You can visit `https://www.dynamsoft.com/customer/license/trialLicense?utm_source=sample&product=dbr&package=js` to get your own trial license good for 30 days.
> * `engineResourcePath` tells the library where to get the necessary resources at runtime.

### Add a file BarcodeScanner.vue under "/components/" as the BarcodeScanner component

* In BarcodeScanner.vue, add code for initializing and destroying the library.

```vue
<template>
  <div id="barcodeScannerUI"></div>
</template>

<script>
import "../dbr";
import { BarcodeScanner } from 'dynamsoft-javascript-barcode';

export default {
  data() {
    return {
      bDestroyed: false,
      pScanner: null,
    };
  },
  async mounted() {
    try {
      let scanner = await (this.pScanner =
        this.pScanner || BarcodeScanner.createInstance());
      if (this.bDestroyed) {
        scanner.destroy();
        return;
      }
      this.$el.appendChild(scanner.getUIElement());
      await scanner.open();
    } catch (ex) {
      console.error(ex);
    }
  },
  async beforeDestroy() {
    if (this.pScanner) {
      (await this.pScanner).destroy();
      this.bDestroyed = true;
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#barcodeScannerUI {
  width: 100%;
  height: 100%;
}
</style>
```

> Note:
>
> * The element "barcodeScannerUI" is used to build the UI for the library in this line
>  
>   ```typescript
>   this.$el.appendChild(scanner.getUIElement());
>   ```
>  
> * To release resources timely, the `BarcodeScanner` instance is destroyed with the component in the callback `beforeDestroy` .

### Add the BarcodeScanner component in HelloWorld.vue

```vue
<template>
  <div id="UIElement">
    <BarcodeScannerComponent></BarcodeScannerComponent>
  </div>
</template>

<script>
import BarcodeScannerComponent from "./BarcodeScanner";

export default {
  name: "HelloWorld",
  props: {},
  components: {
    BarcodeScannerComponent,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#UIElement {
  margin: 2vmin auto;
  text-align: center;
  font-size: medium;
  height: 40vh;
  width: 80vw;
}
</style>
```

### Add HelloWorld.vue to /pages/index.vue

```vue
<template>
  <HelloWorld/>
</template>

<script>
export default {}
</script>
```

* Try running the project.

```cmd
yarn dev
```

If you followed all the steps correctly, you will have a working page that turns one of the cameras hooked to or built in your computer or mobile device into a barcode scanner. However, the found barcodes are not displayed anywhere yet. At the same time, there is a short delay for the initialization of the library during which nothing happens and is not user-friendly. The following takes care of these two issues.

### Update HelloWorld.vue

* Change the template

```vue
<template>
  <div className="helloWorld">
    <div id="UIElement">
      <span style="font-size: x-large" v-if="!libLoaded">Loading Library...</span>
      <BarcodeScannerComponent
        v-if="bShowScanner"
        v-on:appendMessage="appendMessage"
      ></BarcodeScannerComponent>
    </div>
    <input type="text" id="resultText" v-model="resultValue" readonly="true" />
  </div>
</template>
```

* Add style for the "input" element

```css
#resultText {
    display: block;
    margin: 0 auto;
    padding: 0.4rem 0.8rem;
    color: inherit;
    width: 80vw;
    border: none;
    font-size: 1rem;
    border-radius: 0.2rem;
    text-align: center;
}
```

* Change the script

```vue
<script>
import "../dbr";
import { BarcodeScanner } from 'dynamsoft-javascript-barcode';
import BarcodeScannerComponent from "./BarcodeScanner";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  components: {
    BarcodeScannerComponent,
  },
  data() {
    return {
      resultValue: "",
      libLoaded: false,
      bShowScanner: false,
    };
  },
  async mounted() {
    try {
      //Load the library on page load to speed things up.
      await BarcodeScanner.loadWasm();
      this.libLoaded = true;
      this.showScanner();
    } catch (ex) {
      alert(ex.message);
      throw ex;
    }
  },
  methods: {
    showScanner() {
      this.bShowScanner = true;
    },
    appendMessage(message) {
      switch (message.type) {
        case "result":
          this.resultValue = message.format + ": " + message.text;
          break;
        case "error":
          this.resultValue = message.msg;
          break;
        default:
          break;
      }
    },
  },
};
</script>
```

> NOTE :
>
> * The method `loadWasm()` in the function `mounted()` initializes the library in the background. The scanner UI is only shown when the initialization finishes.
> * The method `appendMessage()` is used to show the result text on the page.

* In BarcodeScanner.vue, use the event `onFrameRead` and the parent method `appendMessage()` to return the results.

```vue
<script>
import "../dbr";
import { BarcodeScanner } from 'dynamsoft-javascript-barcode';

export default {
  //Omitted code...
  async mounted() {
    try {
      //Omitted code...
      this.$el.appendChild(scanner.getUIElement());      
      scanner.onFrameRead = (results) => {
        for (let result of results) {
          this.$emit("appendMessage", {
            format: result.barcodeFormatString,
            text: result.barcodeText,
            type: "result",
          });
        }
      };
      await scanner.open();
    } catch (ex) {
      this.$emit("appendMessage", { msg: ex.message, type: "error" });
      console.error(ex);
    }
  },
  //Omitted code...
};
</script>
```

> NOTE :
>
> * The event `onFrameRead` is triggered upon reading of each frame. If barcodes are found on that frame, the results will be returned and shown on the page.

After the above changes, the application is made more user-friendly and the barcode text is displayed on the page right away. You can start implementing your own business workflow and make the application useful.

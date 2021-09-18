---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - Vue Integration Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - Vue Integration
keywords: javascript, js, barcode, vue
noTitleIndex: true
breadcrumbText: Vue
---

# JavaScript Hello World Sample - NuxtJS 
<svg height="45px" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 400"><g fill-rule="nonzero" transform="translate(0 50)" fill="none"><path d="M227.92099 83.45116l-13.6889 24.10141-46.8148-82.44693L23.7037 278.17052h97.3037c0 13.31084 10.61252 24.10142 23.70371 24.10142H23.70371c-8.46771 0-16.29145-4.59601-20.5246-12.05272-4.23315-7.4567-4.23272-16.64312.00114-24.0994L146.89383 13.05492c4.23415-7.45738 12.0596-12.05138 20.5284-12.05138 8.46878 0 16.29423 4.594 20.52839 12.05138l39.97037 70.39623z" fill="#00C58E"/><path d="M331.6642 266.11981l-90.05432-158.56724-13.6889-24.10141-13.68888 24.10141-90.04445 158.56724c-4.23385 7.45629-4.23428 16.64271-.00113 24.09941 4.23314 7.4567 12.05689 12.05272 20.5246 12.05272h166.4c8.46946 0 16.29644-4.591 20.532-12.04837 4.23555-7.45736 4.23606-16.64592.00132-24.10376h.01976zM144.7111 278.17052L227.921 131.65399l83.19012 146.51653h-166.4z" fill="#2F495E"/><path d="M396.04938 290.22123c-4.23344 7.45557-12.05656 12.0507-20.52345 12.0507H311.1111c13.0912 0 23.7037-10.79057 23.7037-24.10141h40.66173L260.09877 74.98553l-18.4889 32.56704L227.921 83.45116l11.65432-20.51634c4.23416-7.45738 12.0596-12.05138 20.5284-12.05138 8.46879 0 16.29423 4.594 20.52839 12.05138l115.41728 203.185c4.23426 7.457 4.23426 16.6444 0 24.1014z" fill="#108775"/></g></svg>

[Nuxt](https://nuxtjs.org/) is a higher-level framework that builds on top of [Vue](https://vuejs.org/). Check out the following guide on how to implement Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") into a Nuxt application.

## Official Sample

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/">Hello World in Nuxt - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/dbr-browser-samples/tree/master/1.hello-world/">Hello World in Nuxt - Source Code</a>

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
import DBR from "dynamsoft-javascript-barcode";
DBR.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.6.1/dist/";
export default DBR;
```

> Note:
> * There are multiple settings available for the configuration, here we only set the `engineResourcePath` which is essential for the library to get the necessary resources at runtime.

### Add a file BarcodeScanner.vue under "/components/" as the BarcodeScanner component

* In BarcodeScanner.vue, add code for initializing and destroying the library.

```vue
<template>
  <div id="barcodeScannerUI"></div>
</template>

<script>
import DBR from "../dbr";

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
        this.pScanner || DBR.BarcodeScanner.createInstance());
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
    <BarcodeScanner></BarcodeScanner>
  </div>
</template>

<script>
import BarcodeScanner from "./BarcodeScanner";

export default {
  name: "HelloWorld",
  props: {},
  components: {
    BarcodeScanner,
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
      <BarcodeScanner
        v-if="bShowScanner"
        v-on:appendMessage="appendMessage"
      ></BarcodeScanner>
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
import DBR from "../dbr";
import BarcodeScanner from "./BarcodeScanner";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  components: {
    BarcodeScanner,
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
      await DBR.BarcodeScanner.loadWasm();
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
> * The method `loadWasm()` in the function `mounted()` initializes the library in the background. The scanner UI is only shown when the initialization finishes.
> * The method `appendMessage()` is used to show the result text on the page.


* In BarcodeScanner.vue, use the event `onFrameRead` and the parent method `appendMessage()` to return the results.

```vue
<script>
import DBR from "../dbr";

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
> * The event `onFrameRead` is triggered upon reading of each frame. If barcodes are found on that frame, the results will be returned and shown on the page.

After the above changes, the application is made more user-friendly and the barcode text is displayed on the page right away. You can start implementing your own business workflow and make the application useful.

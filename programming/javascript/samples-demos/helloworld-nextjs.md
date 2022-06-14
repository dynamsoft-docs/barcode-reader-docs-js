---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - NextJS Integration Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - nextJS Integration
keywords: javascript, js, barcode, nextjs
noTitleIndex: true
breadcrumbText: Next.JS
permalink: /programming/javascript/samples-demos/helloworld-nextjs.html
---

# JavaScript Hello World Sample - Next.js

[Next.js](https://nextjs.org/) is an open-source development framework built on top of Node.js enabling [React](https://reactjs.org/) based web applications functionalities such as server-side rendering and generating static websites. Follow this guide to learn how to implement Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") into a Next.js application.

## Official Sample

* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main/1.hello-world/7.read-video-nextjs">Hello World in Next.js - Source Code</a>

## Preparation

Make sure you have [node](https://nodejs.org/) and [yarn](https://yarnpkg.com/cli/install) installed. `node 14.16.0` and `yarn 1.22.10` are used in the example below.

## Create the sample project

### Create a Bootstrapped Raw Next.js Application

```cmd
npx create-next-app read-video-nextjs
```

### **CD** to the root directory of the application and install the dependencies

```cmd
yarn add dynamsoft-javascript-barcode
```

## Start to implement

### Add a file dbr.js at the root of the application to configure the library

```jsx
import { BarcodeReader } from 'dynamsoft-javascript-barcode';
BarcodeReader.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
BarcodeReader.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.0.2/dist/";
```

> Note:
> * `license` specify a license key to use the library. You can visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=sample&product=dbr&package=js to get your own trial license good for 30 days. 
> * `engineResourcePath` tells the library where to get the necessary resources at runtime.

### Create a directory "components" and create the following files inside it to represent two components

* BarcodeScanner.js
* HelloWorld.js

### Edit the BarcodeScanner component

* In BarcodeScanner.js, add code for initializing and destroying the library.

```jsx
import "../dbr";
import React from 'react';
import { BarcodeScanner } from 'dynamsoft-javascript-barcode';

class BarcodeScannerComponent extends React.Component {
    constructor(props) {
        super(props);
        this.bDestroyed = false;
        this.pScanner = null;
        this.elRef = React.createRef();
    }
    async componentDidMount() {
        try {
            let scanner = await (this.pScanner = this.pScanner || BarcodeScanner.createInstance());
            if (this.bDestroyed) {
                scanner.destroy();
                return;
            }
            this.elRef.current.appendChild(scanner.getUIElement());
            await scanner.open();
        } catch (ex) {
            console.error(ex);
        }
    }
    async componentWillUnmount() {
        this.bDestroyed = true;
        if (this.pScanner) {
            (await this.pScanner).destroy();
        }
    }
    shouldComponentUpdate() {
        // Never update UI after mount, dbrjs sdk use native way to bind event, update will remove it.
        return false;
    }
    render() {
        return (
            <div style={{ width: "100%", height: "100%" }} ref={this.elRef}>
            </div>
        );
    }
}

export default BarcodeScannerComponent;
```

> Note:
> * The html code in `render()` and the following code builds the UI for the library.
> 
>   ```jsx
>   this.elRef.current.appendChild(scanner.getUIElement());
>   ```
> 
> * To release resources timely, the `BarcodeScanner` instance is destroyed with the component in the callback `componentWillUnmount`.
> * The component should never update (check the code for `shouldComponentUpdate()`) so that events bound to the UI stay valid.

### Edit the HelloWorld component

* Add BarcodeScannerComponent in HelloWorld.js

```jsx
import React from 'react';
import BarcodeScannerComponent from './BarcodeScanner';

class HelloWorld extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        return (
            <BarcodeScannerComponent></BarcodeScannerComponent>
        );
    }
}
export default HelloWorld;
```

### Add the HelloWorld component to /pages/index.js

In index.js, import the `HelloWorld` component:

```jsx
import HelloWorld from '../components/HelloWorld'
```

Change the &lt;main&gt; tag like this:

```jsx
<main className={styles.main}>
<div className={styles.UIElement}>
    <HelloWorld title="Welcome to DBRJS Nextjs sample" />
</div>
</main>
```

* Define the style of the "App" element in styles/Home.module.css

```css
.UIElement {
  margin: 2vmin auto;
  text-align: center;
  font-size: medium;
  height: 40vh;
  width: 80vw;
}
```

* Try running the project.

```cmd
yarn dev
```

If you followed all the steps correctly, you will have a working page that turns one of the cameras hooked to or built in your computer or mobile device into a barcode scanner. However, the found barcodes are not displayed anywhere yet. At the same time, there is a short delay for the initialization of the library during which nothing happens and is not user-friendly. The following takes care of these two issues.

### Update `HelloWorld.js`

* Add state values

```jsx
constructor(props) {
    super(props);
    this.state = {
        libLoaded: false,
        resultValue: "",
        bShowScanner: false
    };
}
```

* Add a few functions

```jsx
import { BarcodeScanner } from 'dynamsoft-javascript-barcode';
```

```jsx
async componentDidMount() {
    try {
        //Load the library on page load to speed things up.
        await BarcodeScanner.loadWasm();
        this.setState(state => {
            state.libLoaded = true;
            return state;
        }, () => {
            this.showScanner();
        });
    } catch (ex) {
        alert(ex.message);
        throw ex;
    }
}    
showScanner = () => {
    this.setState({
        bShowScanner: true
    });
}
appendMessage = (message) => {
    switch (message.type) {
        case "result":
            this.setState(prevState => {
                prevState.resultValue = message.format + ": " + message.text;
                return prevState;
            });
            break;
        case "error":
            this.setState(prevState => {
                prevState.resultValue = message.msg;
                return prevState;
            });
            break;
        default: break;
    }
}
```

> NOTE :
> * The method `loadWasm()` in the function `componentDidMount()` initializes the library in the background. The scanner UI is only shown when the initialization finishes.
> * The method `appendMessage()` is used to show the result text on the page.

* Change the UI

```jsx
render() {
    return (
        <div className="helloWorld" style={{ height: "100%", width: "100%" }}>
            {!this.state.libLoaded ? (<span style={{ fontSize: "x-large" }}>Loading Library...</span>) : ""}
            {this.state.bShowScanner ? (<BarcodeScannerComponent appendMessage={this.appendMessage}></BarcodeScannerComponent>) : ""}
            {this.state.bShowScanner ? (<input type="text" style={{width: "80vw",border: "none",fontSize: "1rem",textAlign: "center"}} value={this.state.resultValue} readOnly={true} id="resultText" />) : ""}
        </div>
    );
}
```

* In `BarcodeScanner.js`, use the event `onFrameRead` and the parent method `appendMessage()` to return the results.

```jsx    
async componentDidMount() {
  try {
      //Omitted code...
      this.elRef.current.appendChild(scanner.getUIElement());
      scanner.onFrameRead = results => {
          for (let result of results) {
              this.props.appendMessage({ format: result.barcodeFormatString, text: result.barcodeText, type: "result" });
              if (result.barcodeText.indexOf("Attention(exceptionCode") !== -1) {
                  this.props.appendMessage({ msg: result.exception.message, type: "error" });
              }
          }
      };
      await scanner.open();
  } catch (ex) {
      this.props.appendMessage({ msg: ex.message, type: "error" });
      console.error(ex);
  }
}
```

> NOTE :
> * The event `onFrameRead` is triggered upon reading of each frame. If barcodes are found on that frame, the results will be returned and shown on the page.

After the above changes, the application is made more user-friendly and the barcode text is displayed on the page right away. You can start implementing your own business workflow and make the application useful.

---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - ReactJS Integration Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - ReactJS Integration
keywords: javascript, js, barcode, reactjs
noTitleIndex: true
breadcrumbText: React
---

# JavaScript Hello World Sample - Next.js <svg height="45px" viewBox="0 0 207 124" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd"><g id="Black-Next.js" transform="translate(-247.000000, -138.000000)" fill="#000000" fill-rule="nonzero"><g id="next-black" transform="translate(247.000000, 138.000000)"><g id="EXT-+-Type-something"><path d="M48.9421964,32.6320058 L87.9011585,32.6320058 L87.9011585,35.7136421 L52.5134345,35.7136421 L52.5134345,58.9070103 L85.7908813,58.9070103 L85.7908813,61.9886466 L52.5134345,61.9886466 L52.5134345,87.4526941 L88.306981,87.4526941 L88.306981,90.5343303 L48.9421964,90.5343303 L48.9421964,32.6320058 Z M91.3912326,32.6320058 L95.5306221,32.6320058 L113.8738,58.0960534 L132.622801,32.6320058 L158.124498,0.286809811 L116.22757,60.7722112 L137.817329,90.5343303 L133.51561,90.5343303 L113.8738,63.4483691 L94.1508254,90.5343303 L89.9302715,90.5343303 L111.682358,60.7722112 L91.3912326,32.6320058 Z M139.359455,35.713642 L139.359455,32.6320058 L183.756439,32.6320058 L183.756439,35.7136421 L163.302983,35.7136421 L163.302983,90.5343303 L159.731745,90.5343303 L159.731745,35.7136421 L139.359455,35.713642 Z" id="EXT"></path><polygon id="Type-something" points="0.202923647 32.6320058 4.66697141 32.6320058 66.2235778 124.303087 40.785176 90.5343303 3.93649086 37.0111732 3.77416185 90.5343303 0.202923647 90.5343303"></polygon></g><path d="M183.396622,86.5227221 C184.134938,86.5227221 184.673474,85.9601075 184.673474,85.233037 C184.673474,84.5059658 184.134938,83.9433513 183.396622,83.9433513 C182.666993,83.9433513 182.11977,84.5059658 182.11977,85.233037 C182.11977,85.9601075 182.666993,86.5227221 183.396622,86.5227221 Z M186.905793,83.1297235 C186.905793,85.2763149 188.460599,86.678523 190.727662,86.678523 C193.142388,86.678523 194.601647,85.233037 194.601647,82.7229099 L194.601647,73.8855335 L192.655968,73.8855335 L192.655968,82.7142542 C192.655968,84.1078073 191.952397,84.8521899 190.710289,84.8521899 C189.598473,84.8521899 188.842785,84.1597409 188.816727,83.1297235 L186.905793,83.1297235 Z M197.146664,83.0172011 C197.285642,85.2503478 199.153145,86.678523 201.932686,86.678523 C204.903321,86.678523 206.762139,85.1811034 206.762139,82.792155 C206.762139,80.9138876 205.702439,79.8752151 203.131364,79.2779777 L201.750279,78.9404092 C200.117298,78.5595622 199.457158,78.0488813 199.457158,77.1573541 C199.457158,76.0321243 200.482113,75.296398 202.019547,75.296398 C203.478806,75.296398 204.48639,76.0148135 204.668797,77.1660091 L206.562359,77.1660091 C206.44944,75.0626962 204.590622,73.5825873 202.045605,73.5825873 C199.309495,73.5825873 197.48542,75.0626962 197.48542,77.2871878 C197.48542,79.1221767 198.519063,80.2127835 200.786126,80.7407758 L202.401734,81.1302779 C204.060773,81.5197807 204.790402,82.091051 204.790402,83.0431676 C204.790402,84.1510859 203.643842,84.9560573 202.08035,84.9560573 C200.403939,84.9560573 199.240006,84.2030196 199.074971,83.0172011 L197.146664,83.0172011 Z" id=".JS"></path></g></g></g></svg>

[Next.js](https://nextjs.org/) is an open-source development framework built on top of Node.js enabling [React](https://reactjs.org/) based web applications functionalities such as server-side rendering and generating static websites. Follow this guide to learn how to implement Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") into a Next.js application.

## Official Sample

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/">Hello World in Next.js - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/dbr-browser-samples/tree/master/1.hello-world/">Hello World in Next.js - Source Code</a>

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
import DBR from "dynamsoft-javascript-barcode";
DBR.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.6.1/dist/";
export default DBR;
```

> Note:
> * There are multiple settings available for the configuration, here we only set the `engineResourcePath` which is essential for the library to get the necessary resources at runtime.

### Create a directory "components" and create the following files inside it to represent two components

* BarcodeScanner.js
* HelloWorld.js

### Edit the BarcodeScanner component

* In BarcodeScanner.js, add code for initializing and destroying the library.

```jsx
import DBR from "../dbr";
import React from 'react';

class BarcodeScanner extends React.Component {
    constructor(props) {
        super(props);
        this.bDestroyed = false;
        this.pScanner = null;
        this.elRef = React.createRef();
    }
    async componentDidMount() {
        try {
            let scanner = await (this.pScanner = this.pScanner || DBR.BarcodeScanner.createInstance());
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

export default BarcodeScanner;
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

* Add the BarcodeScanner component in HelloWorld.js

```jsx
import React from 'react';
import BarcodeScanner from './BarcodeScanner';

class HelloWorld extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        return (
            <BarcodeScanner></BarcodeScanner>
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
import DBR from "../dbr";
```

```jsx
async componentDidMount() {
    try {
        //Load the library on page load to speed things up.
        await DBR.BarcodeScanner.loadWasm();
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
            {this.state.bShowScanner ? (<BarcodeScanner appendMessage={this.appendMessage}></BarcodeScanner>) : ""}
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
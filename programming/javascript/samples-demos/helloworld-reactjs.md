---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - ReactJS Integration Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - ReactJS Integration
keywords: javascript, js, barcode, reactjs
noTitleIndex: true
breadcrumbText: React
permalink: /programming/javascript/samples-demos/helloworld-reactjs.html
---

# JavaScript Hello World Sample - React <img style="height: 50px; vertical-align: middle; " alt="React logo" src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA4NDEuOSA1OTUuMyI+PGcgZmlsbD0iIzYxREFGQiI+PHBhdGggZD0iTTY2Ni4zIDI5Ni41YzAtMzIuNS00MC43LTYzLjMtMTAzLjEtODIuNCAxNC40LTYzLjYgOC0xMTQuMi0yMC4yLTEzMC40LTYuNS0zLjgtMTQuMS01LjYtMjIuNC01LjZ2MjIuM2M0LjYgMCA4LjMuOSAxMS40IDIuNiAxMy42IDcuOCAxOS41IDM3LjUgMTQuOSA3NS43LTEuMSA5LjQtMi45IDE5LjMtNS4xIDI5LjQtMTkuNi00LjgtNDEtOC41LTYzLjUtMTAuOS0xMy41LTE4LjUtMjcuNS0zNS4zLTQxLjYtNTAgMzIuNi0zMC4zIDYzLjItNDYuOSA4NC00Ni45Vjc4Yy0yNy41IDAtNjMuNSAxOS42LTk5LjkgNTMuNi0zNi40LTMzLjgtNzIuNC01My4yLTk5LjktNTMuMnYyMi4zYzIwLjcgMCA1MS40IDE2LjUgODQgNDYuNi0xNCAxNC43LTI4IDMxLjQtNDEuMyA0OS45LTIyLjYgMi40LTQ0IDYuMS02My42IDExLTIuMy0xMC00LTE5LjctNS4yLTI5LTQuNy0zOC4yIDEuMS02Ny45IDE0LjYtNzUuOCAzLTEuOCA2LjktMi42IDExLjUtMi42Vjc4LjVjLTguNCAwLTE2IDEuOC0yMi42IDUuNi0yOC4xIDE2LjItMzQuNCA2Ni43LTE5LjkgMTMwLjEtNjIuMiAxOS4yLTEwMi43IDQ5LjktMTAyLjcgODIuMyAwIDMyLjUgNDAuNyA2My4zIDEwMy4xIDgyLjQtMTQuNCA2My42LTggMTE0LjIgMjAuMiAxMzAuNCA2LjUgMy44IDE0LjEgNS42IDIyLjUgNS42IDI3LjUgMCA2My41LTE5LjYgOTkuOS01My42IDM2LjQgMzMuOCA3Mi40IDUzLjIgOTkuOSA1My4yIDguNCAwIDE2LTEuOCAyMi42LTUuNiAyOC4xLTE2LjIgMzQuNC02Ni43IDE5LjktMTMwLjEgNjItMTkuMSAxMDIuNS00OS45IDEwMi41LTgyLjN6bS0xMzAuMi02Ni43Yy0zLjcgMTIuOS04LjMgMjYuMi0xMy41IDM5LjUtNC4xLTgtOC40LTE2LTEzLjEtMjQtNC42LTgtOS41LTE1LjgtMTQuNC0yMy40IDE0LjIgMi4xIDI3LjkgNC43IDQxIDcuOXptLTQ1LjggMTA2LjVjLTcuOCAxMy41LTE1LjggMjYuMy0yNC4xIDM4LjItMTQuOSAxLjMtMzAgMi00NS4yIDItMTUuMSAwLTMwLjItLjctNDUtMS45LTguMy0xMS45LTE2LjQtMjQuNi0yNC4yLTM4LTcuNi0xMy4xLTE0LjUtMjYuNC0yMC44LTM5LjggNi4yLTEzLjQgMTMuMi0yNi44IDIwLjctMzkuOSA3LjgtMTMuNSAxNS44LTI2LjMgMjQuMS0zOC4yIDE0LjktMS4zIDMwLTIgNDUuMi0yIDE1LjEgMCAzMC4yLjcgNDUgMS45IDguMyAxMS45IDE2LjQgMjQuNiAyNC4yIDM4IDcuNiAxMy4xIDE0LjUgMjYuNCAyMC44IDM5LjgtNi4zIDEzLjQtMTMuMiAyNi44LTIwLjcgMzkuOXptMzIuMy0xM2M1LjQgMTMuNCAxMCAyNi44IDEzLjggMzkuOC0xMy4xIDMuMi0yNi45IDUuOS00MS4yIDggNC45LTcuNyA5LjgtMTUuNiAxNC40LTIzLjcgNC42LTggOC45LTE2LjEgMTMtMjQuMXpNNDIxLjIgNDMwYy05LjMtOS42LTE4LjYtMjAuMy0yNy44LTMyIDkgLjQgMTguMi43IDI3LjUuNyA5LjQgMCAxOC43LS4yIDI3LjgtLjctOSAxMS43LTE4LjMgMjIuNC0yNy41IDMyem0tNzQuNC01OC45Yy0xNC4yLTIuMS0yNy45LTQuNy00MS03LjkgMy43LTEyLjkgOC4zLTI2LjIgMTMuNS0zOS41IDQuMSA4IDguNCAxNiAxMy4xIDI0IDQuNyA4IDkuNSAxNS44IDE0LjQgMjMuNHpNNDIwLjcgMTYzYzkuMyA5LjYgMTguNiAyMC4zIDI3LjggMzItOS0uNC0xOC4yLS43LTI3LjUtLjctOS40IDAtMTguNy4yLTI3LjguNyA5LTExLjcgMTguMy0yMi40IDI3LjUtMzJ6bS03NCA1OC45Yy00LjkgNy43LTkuOCAxNS42LTE0LjQgMjMuNy00LjYgOC04LjkgMTYtMTMgMjQtNS40LTEzLjQtMTAtMjYuOC0xMy44LTM5LjggMTMuMS0zLjEgMjYuOS01LjggNDEuMi03Ljl6bS05MC41IDEyNS4yYy0zNS40LTE1LjEtNTguMy0zNC45LTU4LjMtNTAuNiAwLTE1LjcgMjIuOS0zNS42IDU4LjMtNTAuNiA4LjYtMy43IDE4LTcgMjcuNy0xMC4xIDUuNyAxOS42IDEzLjIgNDAgMjIuNSA2MC45LTkuMiAyMC44LTE2LjYgNDEuMS0yMi4yIDYwLjYtOS45LTMuMS0xOS4zLTYuNS0yOC0xMC4yek0zMTAgNDkwYy0xMy42LTcuOC0xOS41LTM3LjUtMTQuOS03NS43IDEuMS05LjQgMi45LTE5LjMgNS4xLTI5LjQgMTkuNiA0LjggNDEgOC41IDYzLjUgMTAuOSAxMy41IDE4LjUgMjcuNSAzNS4zIDQxLjYgNTAtMzIuNiAzMC4zLTYzLjIgNDYuOS04NCA0Ni45LTQuNS0uMS04LjMtMS0xMS4zLTIuN3ptMjM3LjItNzYuMmM0LjcgMzguMi0xLjEgNjcuOS0xNC42IDc1LjgtMyAxLjgtNi45IDIuNi0xMS41IDIuNi0yMC43IDAtNTEuNC0xNi41LTg0LTQ2LjYgMTQtMTQuNyAyOC0zMS40IDQxLjMtNDkuOSAyMi42LTIuNCA0NC02LjEgNjMuNi0xMSAyLjMgMTAuMSA0LjEgMTkuOCA1LjIgMjkuMXptMzguNS02Ni43Yy04LjYgMy43LTE4IDctMjcuNyAxMC4xLTUuNy0xOS42LTEzLjItNDAtMjIuNS02MC45IDkuMi0yMC44IDE2LjYtNDEuMSAyMi4yLTYwLjYgOS45IDMuMSAxOS4zIDYuNSAyOC4xIDEwLjIgMzUuNCAxNS4xIDU4LjMgMzQuOSA1OC4zIDUwLjYtLjEgMTUuNy0yMyAzNS42LTU4LjQgNTAuNnpNMzIwLjggNzguNHoiLz48Y2lyY2xlIGN4PSI0MjAuOSIgY3k9IjI5Ni41IiByPSI0NS43Ii8+PHBhdGggZD0iTTUyMC41IDc4LjF6Ii8+PC9nPjwvc3ZnPg==" />

[React](https://reactjs.org/) is a JavaScript library meant explicitly for creating interactive UIs. Follow this guide to learn how to implement Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") into a React application.

## Official Sample

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/4.read-video-react/build/">Hello World in React - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main/1.hello-world/4.read-video-react">Hello World in React - Source Code</a>

## Preparation

Make sure you have [node](https://nodejs.org/) and [yarn](https://yarnpkg.com/cli/install) installed. `node 16.14.2` and `yarn 1.22.10` are used in the example below.

## Create the sample project

### Create a Bootstrapped Raw React Application

```cmd
npx create-react-app read-video-react
```

### **CD** to the root directory of the application and install the dependencies

```cmd
yarn add dynamsoft-javascript-barcode
```

## Start to implement

### Add a file "dbr.js" under "/src/" to configure the library

```jsx
import { BarcodeReader } from 'dynamsoft-javascript-barcode';
BarcodeReader.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
BarcodeReader.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.0.2/dist/";
```

> Note:
>
> * `license` specify a license key to use the library. You can visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=sample&product=dbr&package=js to get your own trial license good for 30 days.
> * `engineResourcePath` tells the library where to get the necessary resources at runtime.

### Create a directory "components" under "/src/" and create the following files inside it to represent two components

* BarcodeScannerComponent.js
* HelloWorld.css
* HelloWorld.js

### Edit the BarcodeScanner component

* In `BarcodeScannerComponent.js`, add code for initializing the library.

```jsx
import "../dbr";
import { BarcodeScanner } from 'dynamsoft-javascript-barcode';
import React from 'react';

class BarcodeScannerComponent extends React.Component {
    constructor(props) {
        super(props);
        this.pScanner = null;
        this.elRef = React.createRef();
    }
    async componentDidMount() {
        try {
            if (this.pScanner == null)
              this.pScanner = BarcodeScanner.createInstance();
            const scanner = await this.pScanner;
            this.elRef.current.appendChild(scanner.getUIElement());
            this.elRef.current.style.width = "100%";
            this.elRef.current.style.height = "100%";
            await scanner.open();
        } catch (ex) {
            console.error(ex);
        }
    }
    shouldComponentUpdate() {
        // Never update UI after mount, dbrjs sdk use native way to bind event, update will remove it.
        return false;
    }
    render() {
        return (
            <div ref={this.elRef}>
            </div>
        );
    }
}

export default BarcodeScannerComponent;
```

> Note:
>
> * The html code in `render()` and the following code builds the UI for the library.
>
>   ```jsx
>   this.elRef.current.appendChild(scanner.getUIElement());
>   ```
>
> * The component should never update (check the code for `shouldComponentUpdate()`) so that events bound to the UI stay valid.

### Edit the HelloWorld component

* Add BarcodeScannerComponent in `HelloWorld.js`

```jsx
import './HelloWorld.css';
import React from 'react';
import BarcodeScannerComponent from './BarcodeScannerComponent';

class HelloWorld extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        return (
            <div id="UIElement">
                <BarcodeScannerComponent></BarcodeScannerComponent>
            </div>
        );
    }
}
export default HelloWorld;
```

* Define the style of the element in `HelloWorld.css`

```css
#UIElement {
    margin: 2vmin auto;
    text-align: center;
    font-size: medium;
    height: 40vh;
    width: 80vw;
}
```

### Add the HelloWorld component to `App.js`

Edit the file `App.js` to be like this

```jsx
import './App.css';
import HelloWorld from './components/HelloWorld.js';

function App() {
  return (
    <div className="App">
      <HelloWorld></HelloWorld>
    </div>
  );
}

export default App;
```

* Try running the project.

```cmd
yarn start
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
import "../dbr";
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
>
> * The method `loadWasm()` in the function `componentDidMount()` initializes the library in the background. The scanner UI is only shown when the initialization finishes.
> * The method `appendMessage()` is used to show the result text on the page.

* Change the UI

```jsx
render() {
    return (
        <div className="helloWorld">
            <div id="UIElement">
                {!this.state.libLoaded ? (<span>Loading Library...</span>) : ""}
                {this.state.bShowScanner ? (<BarcodeScannerComponent appendMessage={this.appendMessage}></BarcodeScannerComponent>) : ""}
            </div>
            <input type="text" value={this.state.resultValue} readOnly={true} id="resultText" />
        </div>
    );
}
```

* Add style for the "input" element in `HelloWorld.css`

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

* In `BarcodeScannerComponent.js`, use the event `onFrameRead` and the parent method `appendMessage()` to return the results.

```jsx
async componentDidMount() {
    try {
        if (this.pScanner == null)
            this.pScanner = BarcodeScanner.createInstance();
        const scanner = await this.pScanner;
        this.elRef.current.appendChild(scanner.getUIElement());
        this.elRef.current.style.width = "100%";
        this.elRef.current.style.height = "100%";
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
>
> * The event `onFrameRead` is triggered upon reading of each frame. If barcodes are found on that frame, the results will be returned and shown on the page.

After the above changes, the application is made more user-friendly and the barcode text is displayed on the page right away. You can start implementing your own business workflow and make the application useful.

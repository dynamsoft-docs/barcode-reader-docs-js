---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - Angular Integration Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - Angular Integration
keywords: javascript, js, barcode, angular
noTitleIndex: true
breadcrumbText: Angular
permalink: /programming/javascript/samples-demos/helloworld-angular.html
---

# JavaScript Hello World Sample - Angular <img style="height: 50px; vertical-align: middle; " alt="Angular logo" src="data:image/svg+xml; base64, PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNTAgMjUwIj4KICAgIDxwYXRoIGZpbGw9IiNERDAwMzEiIGQ9Ik0xMjUgMzBMMzEuOSA2My4ybDE0LjIgMTIzLjFMMTI1IDIzMGw3OC45LTQzLjcgMTQuMi0xMjMuMXoiIC8+CiAgICA8cGF0aCBmaWxsPSIjQzMwMDJGIiBkPSJNMTI1IDMwdjIyLjItLjFWMjMwbDc4LjktNDMuNyAxNC4yLTEyMy4xTDEyNSAzMHoiIC8+CiAgICA8cGF0aCAgZmlsbD0iI0ZGRkZGRiIgZD0iTTEyNSA1Mi4xTDY2LjggMTgyLjZoMjEuN2wxMS43LTI5LjJoNDkuNGwxMS43IDI5LjJIMTgzTDEyNSA1Mi4xem0xNyA4My4zaC0zNGwxNy00MC45IDE3IDQwLjl6IiAvPgogIDwvc3ZnPg==" />

[Angular](https://angular.io/) is one of the most popular and mature JavaScript frameworks. Check out the following on how to implement Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") into an Angular application.

## Official Sample

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/3.read-video-angular/dist/hello-world/">Hello World in Angular - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/main/1.hello-world/3.read-video-angular">Hello World in Angular - Source Code</a>

## Preparation

Make sure you have [node](https://nodejs.org/) and [Angular CLI](https://cli.angular.io/) installed. `node 14.16.0` and `Angular CLI 11.2.4` are used in the example below.

## Create the sample project

### Create an out-of-the-box raw Angular application

```cmd
ng new read-video-angular
```

### **CD** to the root directory of the application and install the dependencies

```cmd
npm install dynamsoft-javascript-barcode
```

## Start to implement

### Add a file "dbr.ts" under "/app/" to configure the library

```typescript
import { BarcodeReader } from 'dynamsoft-javascript-barcode';
BarcodeReader.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
BarcodeReader.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@9.0.2/dist/";
```

> Note:
>
> * `license` specify a license key to use the library. You can visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=sample&product=dbr&package=js to get your own trial license good for 30 days. 
> * `engineResourcePath` tells the library where to get the necessary resources at runtime.

### Generate two components

```cmd
ng generate component barcode-scanner
```

```cmd
ng generate component hello-world
```

### Edit the barcode-scanner component

* Open the file `.\node_modules\dynamsoft-javascript-barcode\dist\dbr.ui.html`, copy everything and paste in `barcode-scanner.component.html`.

* In `barcode-scanner.component.ts`, add code for initializing and destroying the library.

```typescript
import { Component, OnInit, ElementRef } from '@angular/core';
import '../dbr';
import { BarcodeScanner } from 'dynamsoft-javascript-barcode';

@Component({
  selector: 'app-barcode-scanner',
  templateUrl: './barcode-scanner.component.html',
  styleUrls: ['./barcode-scanner.component.css']
})
export class BarcodeScannerComponent implements OnInit {
  pScanner: any = null;
  constructor(private elementRef: ElementRef) { }
  async ngOnInit(): Promise<void> {
    try {
      if (this.pScanner == null)
        this.pScanner = BarcodeScanner.createInstance();
      const scanner = await this.pScanner;
      scanner.setUIElement(this.elementRef.nativeElement);
      await scanner.open();
    } catch (ex) {
      console.error(ex);
    }
  }
  async ngOnDestroy() {
    if (this.pScanner) {
      (await this.pScanner).destroyContext();
      console.log('BarcodeScanner Component Unmount');
    }
  }
}
```

> Note:
>
> * The method `createInstance()` is called to initialize the library as soon as the component initializes.
> * To release resources timely, the `BarcodeScanner` instance is destroyed with the component in the callback `ngOnDestroy` .
> * The method `setUIElement()` specifies the UI for the library with the native element in `barcode-scanner.component.html` which we just copied over in the previous step.

### Edit the hello-world component

* Add the barcode-scanner component in `hello-world.component.html`

```html
<div id="UIElement">
    <app-barcode-scanner></app-barcode-scanner>
</div>
```

* Define the style of the element in `hello-world.component.css`

```css
#UIElement {
    margin: 2vmin auto;
    text-align: center;
    font-size: medium;
    height: 40vh;
    width: 80vw;
}
```

### Add the hello-world component to `app.component.html`

Edit the file `app.component.html` to contain nothing but the following

```html
<app-hello-world></app-hello-world>
```

* Try running the project.

```cmd
ng serve -o
```

If you followed all the steps correctly, you will have a working page that turns one of the cameras hooked to or built in your computer or mobile device into a barcode scanner. However, the found barcodes are not displayed anywhere yet. At the same time, there is a short delay for the initialization of the library during which nothing happens and is not user-friendly. The following takes care of these two issues.

### Make it more user friendly

* Change the code in `hello-world.component.html` like this

```html
<div id="UIElement">
    <span style='font-size:x-large' *ngIf="!libLoaded">Loading Library...</span>
    <app-barcode-scanner *ngIf="bShowScanner" (appendMessage)="appendMessage($event)"></app-barcode-scanner>
</div>
<input id="resultText" type="text" [value]="resultValue" readonly="true">
```

* Add style for the "input" element in `hello-world.component.css`

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

* Also, in `hello-world.component.ts`, write the following code

```typescript
import { BarcodeScanner } from 'dynamsoft-javascript-barcode';
```

```typescript
export class HelloWorldComponent implements OnInit {
  bShowScanner = false;
  resultValue: string;
  libLoaded = false;
  constructor() { this.resultValue = ""; }
  async ngOnInit(): Promise<void> {
    try {
      //Load the library on page load to speed things up.
      await BarcodeScanner.loadWasm();
      this.libLoaded = true;
      this.showScanner();
    } catch (ex: any) {
      alert(ex.message);
      throw ex;
    }
  }
  showScanner(): void {
    this.bShowScanner = true;
  }
  hideScanner(): void {
    this.bShowScanner = false;
  }
  appendMessage(message: any) {
    switch (message.type) {
      case "result":
        this.resultValue = message.format + ": " + message.text;
        break;
      case "error":
        this.resultValue = message.msg;
        break;
      default: break;
    }
  }
}
```

> NOTE :
>
> * The method `loadWasm()` initializes the library in the background. The scanner UI is only shown when the initialization finishes.
> * The method `appendMessage()` is used to show the result text on the page.

* Add an `EventEmitter` in `barcode-scanner.component.ts` and use the event `onFrameRead` to return the results.

```typescript
import { Component, OnInit, EventEmitter, Output, ElementRef } from '@angular/core';
import '../dbr';
import { BarcodeScanner, TextResult } from 'dynamsoft-javascript-barcode';
```

```typescript
export class BarcodeScannerComponent implements OnInit {
  pScanner: any = null;
  constructor(private elementRef: ElementRef) { }
  @Output() appendMessage = new EventEmitter();
  async ngOnInit(): Promise<void> {
    try {
      if (this.pScanner == null)
        this.pScanner = BarcodeScanner.createInstance();
      const scanner = await this.pScanner;
      scanner.setUIElement(this.elementRef.nativeElement);
      scanner.onFrameRead = (results: Array<TextResult>) => {
        for (let result of results) {
          this.appendMessage.emit({ format: result.barcodeFormatString, text: result.barcodeText, type: "result" });
        }
      };
      await scanner.open();
    } catch (ex) {
      console.error(ex);
    }
  }
  async ngOnDestroy() {
    if (this.pScanner) {
      (await this.pScanner).destroyContext();
      console.log('BarcodeScanner Component Unmount');
    }
  }
}
```

> NOTE :
>
> * The event `onFrameRead` is triggered upon reading of each frame. If barcodes are found on that frame, the results will be returned and shown on the page.

After the above changes, the application is made more user-friendly and the barcode text is displayed on the page right away. You can start implementing your own business workflow and make the application useful.

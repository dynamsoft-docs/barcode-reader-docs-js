---
layout: default-layout
title: Dynamsoft Barcode Reader for JavaScript - PWA Sample
description: Dynamsoft Barcode Reader SDK for JavaScript - PWA
keywords: javascript, js, barcode, pwa
noTitleIndex: true
breadcrumbText: PWA
---

# JavaScript Hello World Sample - PWA

[PWA](https://web.dev/progressive-web-apps/) is short for Progressive Web Apps which stand for web applications that have been designed to behave like platform-specific (native) applications. Check out the following on how to implement Dynamsoft Barcode Reader JavaScript SDK (hereafter called "the library") into a PWA application.

## Official Sample

* <a target = "_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/3.read-video-angular/dist/hello-world/">Hello World in PWA - Demo</a>
* <a target = "_blank" href="https://github.com/Dynamsoft/dbr-browser-samples/tree/master/1.hello-world/3.read-video-angular">Hello World in PWA - Source Code</a>

## Preparation

We will try to turn our most basic hello world sample into a PWA. 

First, create a file with the name "helloworld-pwa.html" and fill it with the following code:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>Dynamsoft Barcode Reader Sample - Hello World (Decoding via Camera)</title>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.4.0/dist/dbr.js"></script>
</head>

<body>
    <h2>Minimum Code to Read Barcodes</h2>
    <button id='readBarcode'>Read Barcode via Camera</button>
    <script>
        let pScanner = null;
        document.getElementById('readBarcode').onclick = async function() {
            try {
                let scanner = await (pScanner = pScanner || Dynamsoft.DBR.BarcodeScanner.createInstance());
                scanner.onFrameRead = results => {
                    console.log("Barcodes on one frame:");
                    for (let result of results) {
                        console.log(result.barcodeFormatString + ": " + result.barcodeText);
                    }
                };
                scanner.onUnduplicatedRead = (txt, result) => {
                    alert(txt);
                    console.log("Unique Code Found: " + result);
                }
                await scanner.show();
            } catch (ex) {
                alert(ex.message);
                throw ex;
            }
        };
    </script>
</body>

</html>
```

Next, set up a secure environment (HTTPs) to run the page "helloworld-pwa.html". This is because a secure environment is required for PWAs.

In our case, we use IIS to set up a secure site at "https://localhost" and put the page at the root so that it can be accessed at "https://localhost/helloworld-pwa.html".

## Make the app progressive

### Register a service worker

As the basis for PWAs, Service Workers are a virtual proxy between the browser and the network. A service worker can serve content offline, handle notifications and perform heavy calculations, etc. all on a separate thread.

To use a service worker, we first need to register it. In the helloworld-pwa.html file, add the following at the end of the script:

```javascript
if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('./service-worker.js');
};
```

Create the service-worker.js file with the following content:

```javascript
// Files to cache
const cacheName = 'helloworld-pwa';
const appShellFiles = [
    '/helloworld-pwa.html',
];

// Installing Service Worker
self.addEventListener('install', (e) => {
    console.log('[Service Worker] Install');
    e.waitUntil((async () => {
        const cache = await caches.open(cacheName);
        console.log('[Service Worker] Caching all: app shell and content');
        await cache.addAll(appShellFiles);
    })());
});

self.addEventListener('fetch', (e) => {
    e.respondWith((async () => {
        const r = await caches.match(e.request);
        console.log(`[Service Worker] Fetching resource: ${e.request.url}`);
        if (r) { return r; }
        const response = await fetch(e.request);
        const cache = await caches.open(cacheName);
        console.log(`[Service Worker] Caching new resource: ${e.request.url}`);
        cache.put(e.request, response.clone());
        return response;
    })());
});
```

With the above code, the application can now work offline.

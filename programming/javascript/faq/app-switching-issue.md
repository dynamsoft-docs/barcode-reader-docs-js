
---
layout: default-layout
title: How can I prevent my browser from freezing or showing a grey screen when I switch between apps and return to it?
keywords: Dynamsoft Barcode Reader, FAQ, tech basic, frozen screen, grey screen
description: How can I prevent my browser from freezing or showing a grey screen when I switch between apps and return to it?
needAutoGenerateSidebar: false
---

# How can I prevent my browser from freezing or showing a grey screen when I switch between apps and return to it?

[<< Back to FAQ index](index.md)

When using the camerenhancer sdk, you may encounter an issue where switching to another app and then returning to the browser results in a frozen or grey screen. To address this, utilize a workaround in the form of the following code snippet:

```javascript
window.addEventListener("visibilitychange", () => {
    if (document.visibilityState === "hidden") {
        if (router && cameraEnhancer) {
            router.stopCapturing().then(() => {
                cameraEnhancer.close();
            });
        }
    } else if (document.visibilityState === "visible") {
        if (router && cameraEnhancer) {
            cameraEnhancer.open().then(status => {
                router.startCapturing("DetectDocumentBoundaries_Default");
            });
        }
    }
});
```

This code essentially closes the camera and releases associated resources when the user exits the browser. It then reopens the camera when the user returns to the browser, ensuring a smoother experience.
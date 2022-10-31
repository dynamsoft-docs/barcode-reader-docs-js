---
layout: default-layout
title: How to use the JavaScript SDK in offline mode?
keywords: Dynamsoft Barcode Reader, FAQ, Sales & Licensing, offline mode use
description: How to use the JavaScript SDK in offline mode?
needAutoGenerateSidebar: false
---

# How to use the Dynamsoft Barcode Reader JavaScript SDK in offline mode?

[<< Back to FAQ index](index.md)


It depends on the License option:

1. If it is Per Barcode Scan License, The client device can work in an offline scenario after it is registered, but no more than 7 days. The initial registration of the device requires an internet connection if the license is hosted on the Dynamsoft server. If you chose the self-hosting option when activating the license, then the device must have a connection to your internally hosted license server for the initial registration.
2. If it is Per Client Device License, we have some per-device license type: Yearly, Quarterly, Monthly and Daily active Device License, which allows users set the offline usage interval in an allowed time period, in the setted interval the SDK could work successfully, after that it cannot be used and need to be reconnected as soon as possible. 

The full details are explained [here](https://www.dynamsoft.com/license-server/docs/about/licensefaq.html?ver=latest#can-a-client-device-work-offline).

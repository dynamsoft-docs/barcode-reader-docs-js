---
layout: default-layout
title: How to Resolve Camera Cannot Open in PWA Using Dynamsoft Barcode Reader on iOS
description: Camera Cannot Open in PWA Using Dynamsoft Barcode Reader on iOS
keywords: PWA, iOS, camera, javascript, js
needAutoGenerateSidebar: false
---


# How to Resolve Camera Cannot Open in PWA Using Dynamsoft Barcode Reader on iOS

## ❓ Issue

When using **Dynamsoft Barcode Reader** in a **Progressive Web App (PWA)** on **iOS**, the **camera fails to open**. This prevents barcode scanning functionality from working as expected.

## 💡 Cause

This issue is due to **limited PWA support on iOS**. Specifically:

- iOS has known restrictions when accessing camera features from PWAs.
- Cached data or system-level inconsistencies can cause the camera initialization to fail.

## ✅ Solution

To resolve the issue:

1. **Clear Safari cache(iOS 18+)**:
   - Go to **Settings > Apps > Safari > Clear History and Website Data**.

2. **Reboot the device**:
   - Power off your iPhone or iPad completely, then restart it.

After following these steps, try launching the PWA again and accessing the camera.

## 📌 Note

This issue is specific to **iOS PWAs**. On Android or desktop browsers, Dynamsoft Barcode Reader in a PWA generally works without issue.

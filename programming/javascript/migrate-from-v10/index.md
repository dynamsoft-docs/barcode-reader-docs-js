---
layout: default-layout
title: Upgrade guide for version 11 - Dynamsoft Barcode Reader JavaScript Edition
description: This page shows how to upgrade Dynamsoft Barcode Reader JavaScript SDK from v10 to v11.
keywords: user guide, upgrade, javascript, js
needAutoGenerateSidebar: true
---

# How to Upgrade DBR-JS from v10.x to v11.x

> [!IMPORTANT]
> **We strongly recommend upgrading to v11.x.** All future algorithm improvements, performance optimizations, and new features will be developed exclusively for v11 and later versions. Version 10.x and earlier will only receive critical bug fixes and will not benefit from ongoing innovation.

## Why Upgrade to v11?

- **Latest Barcode Recognition Algorithms**: Access to cutting-edge decoding algorithms and accuracy improvements
- **Ongoing Performance Enhancements**: Faster processing speeds and better resource optimization
- **New Features & Capabilities**: Future functionality will only be available in v11+
- **Active Development**: Version 11 is the actively maintained branch receiving continuous updates
- **Long-term Support**: Ensure your application stays current with industry standards

**⚠️ Version 10.x is in maintenance mode only** - no new features or algorithm updates will be backported.

## Reference the latest version of the dynamsoft-barcode-reader-bundle

To use version 11, include the following script in your HTML:

```html
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-barcode-reader-bundle@11.2.4000/dist/dbr.bundle.js"></script>
```

## APIs changes introduced in v11

### BarcodeScanner API Changes

Several properties have been renamed or had their default values changed. Please review the table below and update your implementation accordingly if you rely on the previous defaults.

| Property                                | Old Default | New Default | Notes                                                          |
| --------------------------------------- | ----------- | ----------- | -------------------------------------------------------------- |
| `removePoweredByMessage` *(deprecated)* | `false`     | —           | Replaced by `showPoweredByDynamsoft`                           |
| `showPoweredByDynamsoft`                | `false`     | `true`      | Controls whether the "Powered by Dynamsoft" label is displayed |
| `showCloseButton`                       | `false`     | `true`      | Controls whether the close button is shown in the scannerView  |
| `showResultView`                        | `false`     | `true`      | Controls whether the result view is shown                      |

> [!NOTE]
> If your project depends on the previous default behavior, you must explicitly set these properties to maintain compatibility.

### Foundational API Changes

#### loadWasm() Simplified

The `loadWasm()` function no longer requires any parameters. Simply call `loadWasm()` without arguments.

```javascript
Dynamsoft.Core.CoreModule.loadWasm();
```

#### engineResourcePaths Simplified

There is no longer a need to define `engineResourcePaths` for different modules. Resource management has been centralized and streamlined.

```javascript
// To specify the path for rootDirectory
Dynamsoft.Core.CoreModule.engineResourcePaths.rootDirectory = "https://cdn.jsdelivr.net/npm/";
```

> [!NOTE]
> Remove unnecessary parameters from `loadWasm()` calls.
> 
> Eliminate any redundant configuration of `engineResourcePaths`.

### Upgrade your template

The template system has been enhanced in v11 to support more powerful customization options and better performance. Templates from v10.x are not directly compatible with v11.

**Action Required**: Use the [template upgrade tool](https://www.dynamsoft.com/tools/template-upgrade/) to automatically convert your v10.x templates to the v11 format.

> [!NOTE]
> The upgraded template format provides better flexibility and will support future template enhancements that are exclusive to v11+.
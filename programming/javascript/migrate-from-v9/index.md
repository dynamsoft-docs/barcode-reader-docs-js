---
layout: default-layout
title: Upgrade guide for version 11 - Dynamsoft Barcode Reader JavaScript Edition
description: This page shows how to upgrade Dynamsoft Barcode Reader JavaScript SDK from v9 to v11.
keywords: user guide, upgrade, javascript, js
needAutoGenerateSidebar: true
---

# How to Upgrade DBR-JS from v9.x to v11.x

## Why Upgrade to v11?

- **Latest Barcode Recognition Algorithms**: Access to cutting-edge decoding algorithms and accuracy improvements
- **Ongoing Performance Enhancements**: Faster processing speeds and better resource optimization
- **New Features & Capabilities**: Future functionality will only be available in v11+
- **Active Development**: Version 11 is the actively maintained branch receiving continuous updates
- **Long-term Support**: Ensure your application stays current with industry standards

> [!IMPORTANT]
> **Critical: Version 9.x and earlier are on a legacy architecture.** All new algorithm development, performance improvements, and features are built exclusively on the DynamsoftCaptureVision (DCV) architecture introduced in v10+.
> 
> **Staying on v9.x or earlier means:**
> - ❌ No access to new barcode recognition algorithms
> - ❌ No future performance optimizations
> - ❌ Missing out on new symbology support
> - ❌ Limited to critical security patches only
>
> **Upgrading to v11 provides:**
> - ✅ Access to all future algorithm enhancements
> - ✅ Continuous performance improvements
> - ✅ New features and capabilities as they're released
> - ✅ Full technical support and active maintenance

### Understanding the DCV Architecture Advantage

The Dynamsoft Barcode Reader JavaScript edition has been completely refactored to integrate with the powerful DynamsoftCaptureVision (DCV) architecture. To understand the full advantages of this new architecture, please refer to:

* [Overview of Dynamsoft Capture Vision](https://www.dynamsoft.com/capture-vision/docs/core/introduction/)
* [Dynamsoft Capture Vision Framework Details](https://www.dynamsoft.com/capture-vision/docs/core/architecture/)

### Migration Requirements

Due to the significant architectural improvements, **a rewrite of your existing code is required** when upgrading from v9.x or earlier. While this requires initial effort, it positions your application to benefit from years of future development.

**We strongly recommend following the [User Guide](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/user-guide/index.html) to migrate your code to v11.**

> [!TIP]
> The investment in upgrading pays off quickly through improved performance and access to ongoing innovations. Our updated APIs are more intuitive and require less boilerplate code.
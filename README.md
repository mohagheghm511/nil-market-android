<div align="center">

<img src="screenshots/app-logo.png" width="120" alt="Nil Market">

# 📱 Nil Market: Android App

**A native Android app (Kotlin) for [Nil Market](https://niloufarsepahan.com/nilmarket/), the online wholesale store of Niloufar Sepahan.**
It combines native navigation, search, notifications and in-app payments with the live WooCommerce store.

![Android](https://img.shields.io/badge/Android-8.0%2B%20(API%2026)-3DDC84?logo=android&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-100%25-7F52FF?logo=kotlin&logoColor=white)
![CI](https://img.shields.io/badge/GitHub%20Actions-signed%20APK%20builds-2088FF?logo=githubactions&logoColor=white)

Part of the **[Niloufar Sepahan platform](https://github.com/mohagheghm511/niloufar-sepahan-theme)** (corporate site + store + app).

</div>

> 🔒 **The source code is private.** This repository is a portfolio showcase only.

---

## 📌 Overview

The store already existed as a large custom WooCommerce site. The goal was a real app that people **want to keep on their phone**, without maintaining a second store. The app loads the live store, replaces the website chrome with **native Android UI**, and solves the problems that make most "website apps" feel broken, such as half-drawn pages, stale caches, lost payments and missed notifications.

<p align="center">
<img src="screenshots/shop-home.jpg" width="49%" alt="Store home">
<img src="screenshots/shop-coffee-category.jpg" width="49%" alt="Coffee category">
</p>

## ✨ Features

### Native experience
- **Animated splash screen** (logo, name, tagline and progress bar easing in). It stays until the page, including every image, has finished loading, so users never see a half-drawn page.
- **Native bottom navigation**: Home, Categories, Cart and Account.
- **Native search bar with live suggestions** from the store's Persian smart-search endpoint, debounced per keystroke. The bar clears itself once the shopper moves on.
- **Native notification bell** with an unread badge, which replaces the site header that is hidden in the app. Opening a notice marks it as read on the server before navigating.
- **Background notices** that survive reboots, with a battery-optimization exemption prompt so alerts arrive on time.
- The app always opens **the store and never the corporate site**. The app tags its user agent, and the site uses that to keep company pages out.

### Reliability
- **In-app payments:** Iranian gateway redirects (Shaparak, ZarinPal, IDPay, Zibal, PayPing, NextPay, Vandar, Pay.ir, BitPay) stay inside the app, so every payment is matched to its order.
- **Remote configuration:** tab URLs are loaded from a JSON file on the site, so they can change without releasing a new version.
- **Update check before the store opens:** the build number is sent in both the user agent and the URL, which stops page caches from serving a wrong answer. A declined update is remembered for that build.
- **Smart cache busting:** the WebView cache is cleared on app update and whenever the site reports new styles.
- **Stall detection:** the retry option appears only when loading has really stopped (no progress and no images arriving), not on a fixed timer.
- App-side styling is applied to every page, so a cached desktop page still looks right inside the app.
- A compatibility mode for mixed http/https assets.

### Build & release
- **GitHub Actions CI:** every push builds a **signed release APK**. The keystore comes from repository secrets, the build number is embedded in the app and in the APK file name (`nil-market-1.<build>.apk`), and the APK is published as a workflow artifact.
- A single `Config.kt` holds everything that normally changes.

## 🧰 Tech Stack
Kotlin · Android SDK 34 (min 26) · WebView + native Views · Gradle (KTS) · GitHub Actions

---

<div align="center">

**Designed and developed by [@mohagheghm511](https://github.com/mohagheghm511)**

</div>

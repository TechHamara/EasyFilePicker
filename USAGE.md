# 📂 EasyFilePicker Extension

[![Developer](https://img.shields.io/badge/Developer-TechHamara-blue.svg)](https://github.com/TechHamara)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://github.com/TechHamara/Th_Extensions_List/blob/main/LICENSE.md)
[![Platform](https://img.shields.io/badge/Platform-MIT%20App%20Inventor%202-orange.svg)]()
[![Buy Me A Coffee](https://img.shields.io/badge/Support-Buy%20Me%20A%20Coffee-yellow.svg)](https://buymeacoffee.com/techhamara)

**EasyFilePicker** is a powerful, fully self-contained Android Storage Access Framework (SAF) extension for MIT App Inventor 2, Kodular, and Niotron. It empowers developers to seamlessly select single or multiple files, pick entire directories (folders), and securely prompt users to choose where to save files without requesting any intrusive storage permissions.

**100% Google Play Store Policy Compliant:** By utilizing the Android Storage Access Framework natively, this extension bypasses the need for the highly restricted `READ_EXTERNAL_STORAGE` and `MANAGE_EXTERNAL_STORAGE` permissions.

---

## ✨ Features

- **✅ No Storage Permissions Required:** Fully compatible with Android 11, 12, 13, and 14 scoped storage and strict Play Store policies.
- **📄 Single & Multiple File Picking:** Pick specific file types (MIME types) or all files with built-in caching.
- **📁 Directory Selection:** Let users select whole folders to save or manage their data.
- **💾 Save As Prompt:** Trigger a system UI to ask users exactly where they want to save a new file securely.
- **🧹 Built-in Cache Management:** Automatically caches picked files to internal storage with customizable cache limits to prevent memory bloat.
- **🚀 Initial Directory Support:** Launch the picker directly into a specified folder (Android 8.0+).

---

## 🛠️ Usage Examples

### 1. Picking a Single File
Allow the user to select an image from their device.
- **Blocks:** Use `PickSingleFile` and pass the MIME type (e.g., `image/*` or `*/*`).
- **Event:** Listen to the `SingleFilePicked` event to receive the file's absolute path, URI, size, and display name.
- **Tip:** You can directly pass the generated `path` into an `Image` component.

### 2. Selecting Multiple Files
Need the user to select multiple documents?
- **Blocks:** Use `PickMultipleFiles` with your desired MIME type.
- **Event:** Use the `MultipleFilesPicked` event, which returns lists of paths, URIs, and sizes.

### 3. Choosing a Save Location
Want to export a file from your app and let the user decide where to save it?
- **Blocks:** Use the `SaveFile` block. Set `mimeType` (e.g., `application/pdf`) and `defaultName` (e.g., `MyInvoice.pdf`).
- **Event:** Listen to `SaveLocationPicked` to retrieve the chosen URI, then write your data to that URI.

---

## ❓ Frequently Asked Questions (FAQ)

### Why doesn't this extension ask for Storage Permission anymore?
Google Play Store heavily restricts the use of broad storage permissions like `READ_EXTERNAL_STORAGE` in modern Android versions (Android 11+). This extension uses Android's native **Storage Access Framework (SAF)**, which temporarily grants the app read/write access to only the specific files or folders the user explicitly selects. This means **zero permission prompts** for the user and **100% compliance** with Play Store rules.

### How does the cache system work?
When a user selects a file via SAF, it's often a virtual URI that cannot be directly read by some MIT App Inventor components. To solve this, EasyFilePicker automatically copies the selected file into your app's internal cache directory and provides you with an `absolutePath` that can be used universally. The cache is auto-cleaned based on your `CacheLimit` property (default: 25 files).

### I'm getting a "Could not take persistable URI permission" error in Logcat. Is this bad?
No, this is completely normal. Some cloud storage providers (like Google Drive) or specific apps do not support "persistable" permissions. The extension safely ignores this and will still allow you to read the file perfectly for the current session.

### The `PermissionResult` event is no longer triggering?
That is correct. Because permissions are no longer requested or required, this block is now deprecated and will not fire. You can safely remove it from your blocks.

---

## 🔗 Helpful Links

- 📦 [Find More Extensions by TechHamara](https://github.com/TechHamara/Th_Free_Extensions)
- 📜 [Terms & Conditions](https://github.com/TechHamara/Th_Extensions_List/blob/main/LICENSE.md#terms-and-conditions-for-the-extension)
- ☕ [Support the Developer on BuyMeCoffee](https://buymeacoffee.com/techhamara)


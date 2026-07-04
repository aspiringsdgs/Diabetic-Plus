# 📱 IPFS Spreadsheet App Automation Template

A premium, offline-first hybrid mobile and web application template built with the **Ionic Framework (React)** and **Capacitor**. This repository serves as an automation and rebranding base to easily generate, build, and publish specialized spreadsheet-powered applications utilizing a mobile-optimized **SocialCalc** engine and decentralized **IPFS** cloud backups.

---

## 🏗️ Rebranding & Automation Architecture

Rather than maintaining separate codebases for different spreadsheet tools (e.g., patient sheets, medication schedules, invoice calculators, or ledgers), this template utilizes a metadata-driven architecture. 

A single application container runs the core SocialCalc engine and offline database schema. By running the automation scripts in the [scripts](file:///Users/anirudhsharma/Desktop/C4GT/0.%20Base%20App%20Codebase/APPs/ipfs-apps/patient%20sheet%20copy/scripts) folder, you can transform this base project into a completely rebranded application in minutes.

```
                  +--------------------------------+
                  |  Rebranding Config (data.json) |
                  +---------------+----------------+
                                  |
                                  | (update-app.sh)
                                  v
+---------------------------------+---------------------------------+
|                     AUTOMATED APP REBRANDING                     |
|                                                                   |
|  * Patches 19 files (Bundle ID, app name, variables, menus)       |
|  * Re-generates assets (App Icons, Universal Splash Screens)      |
|  * Captures App Store Screenshots via Playwright emulation        |
+---------------------------------+---------------------------------+
                                  |
                                  v
+---------------------------------+---------------------------------+
|                    CORE TEMPLATE CONTAINER                        |
|                                                                   |
|  +--------------------+   +-------------------+  +-------------+  |
|  | SocialCalc Engine  |   | SQLite DB Layer   |  | IPFS Backup |  |
|  +--------------------+   +-------------------+  +-------------+  |
+-------------------------------------------------------------------+
```

---

## ✨ Core Base Features

- **100% Offline-First**: Built-in SQLite storage layer utilizing `@capacitor-community/sqlite` and `localStorage` fallback to keep all custom templates, sheets, and preferences on-device.
- **SocialCalc Computing Engine**: Integrates a touch-optimized adaptation of the SocialCalc spreadsheet engine with native input modals.
- **Decentralized Cloud Saves**: Encrypted client-side exports pushed to the IPFS gateway, providing shareable Content Identifiers (CIDs) for backup and restore.
- **Responsive Layout**: Designed first for mobile touch targets, with robust scaling support for iPad, tablet, and desktop views.

---

## 🛠️ Tech Stack

- **Core Framework**: [Ionic React](https://ionicframework.com/docs/react) v8.7 (React 19, TypeScript)
- **Native Bridge**: Capacitor v8
- **Database**: SQLite
- **Bundler**: Vite
- **Automation Engine**: Playwright, Python3, and Bash

---

## 🚀 Development & Setup

### Prerequisites
- Node.js (v18+)
- Ionic CLI (`npm install -g @ionic/cli`)

### Quick Start
1. **Install dependencies**:
   ```bash
   npm install
   ```
2. **Start local development server**:
   ```bash
   npm run dev
   ```
3. **Run unit tests**:
   ```bash
   npm run test.unit
   ```
4. **Build web distribution bundle**:
   ```bash
   npm run build
   ```

### Capacitor Native Integration (Android & iOS)
Sync and run the app on mobile devices/emulators:
```bash
# Sync web build to native platform projects
npx cap sync

# Launch on iOS
npx cap run ios

# Launch on Android
npx cap run android
```

---

## 🤖 App Automation & Rebranding Suite

The [scripts](file:///Users/anirudhsharma/Desktop/C4GT/0.%20Base%20App%20Codebase/APPs/ipfs-apps/patient%20sheet%20copy/scripts) directory contains three distinct automation pipelines to rebrand, asset-generate, and screenshot-automate your target app variants.

### 1. App Configuration & Rebranding (`scripts/app-update-automation`)
Easily update the core identity, descriptions, bundle IDs, onboarding flows, template files, theme colors, and PDF layouts across **19 files** in one command.

*   **Configuration File**: [data.json](file:///Users/anirudhsharma/Desktop/C4GT/0.%20Base%20App%20Codebase/APPs/ipfs-apps/patient%20sheet%20copy/scripts/app-update-automation/data.json)
    Define app metadata, onboarding features, brand primary/secondary color hex codes, PWA options, and default template paths.
*   **Automation Script**: [update-app.sh](file:///Users/anirudhsharma/Desktop/C4GT/0.%20Base%20App%20Codebase/APPs/ipfs-apps/patient%20sheet%20copy/scripts/app-update-automation/update-app.sh)
*   **How to execute**:
    Run the following command from the repository root:
    ```bash
    bash scripts/app-update-automation/update-app.sh
    ```

### 2. Branding Asset Generation (`scripts/app-assets-generation`)
This pipeline automatically scans the workspace to find high-resolution PNG templates for your app's icon and splash screen, sampling background colors to properly pad and export multi-platform assets.

*   **Generated Assets**:
    *   **iOS Assets**: iOS App Store high-res icon (`AppIcon-512@2x.png`) and universal Launch Screen splash images.
    *   **PWA/Web Assets**: Touch icons, favicons, and standard sizes (64x64, 192x192, 512x512) written directly to `public/`.
*   **Automation Script**: [generate_assets.sh](file:///Users/anirudhsharma/Desktop/C4GT/0.%20Base%20App%20Codebase/APPs/ipfs-apps/patient%20sheet%20copy/scripts/app-assets-generation/generate_assets.sh) (wrapping [generate_assets.py](file:///Users/anirudhsharma/Desktop/C4GT/0.%20Base%20App%20Codebase/APPs/ipfs-apps/patient%20sheet%20copy/scripts/app-assets-generation/generate_assets.py))
*   **How to execute**:
    Run the following command from the repository root:
    ```bash
    bash scripts/app-assets-generation/generate_assets.sh
    ```

### 3. App Store Screenshot Automation (`scripts/app-screenshot-automation`)
Automates high-resolution screenshot generation simulating all major iPhone and iPad viewports using Playwright. The script navigates the full application flow—onboarding, document editing, and options screens—and captures them for App Store Connect.

*   **Viewports Covered**:
    *   **6.9" Display**: iPhone 16 Pro Max (1320x2868 px)
    *   **6.5" Display**: iPhone 14 Plus / 13 Pro Max (1284x2778 px)
    *   **6.1" Display**: iPhone 16 / 15 / 14 / 13 / 12 (1170x2532 px)
    *   **13" iPad**: iPad Pro 13" (2064x2752 px)
    *   **11" iPad**: iPad Pro 11" (1668x2388 px)
*   **Configuration**: Customize viewports, targets, and edit cells/values inside [screenshot-config.json](file:///Users/anirudhsharma/Desktop/C4GT/0.%20Base%20App%20Codebase/APPs/ipfs-apps/patient%20sheet%20copy/scripts/app-screenshot-automation/screenshot-config.json).
*   **How to execute**:
    1. Make sure your local application server is running (e.g., `npm run dev` at `http://localhost:3000`).
    2. Navigate to the automation directory and install dependencies:
       ```bash
       cd scripts/app-screenshot-automation
       npm install
       npx playwright install
       ```
    3. Run the screen capturer:
       ```bash
       npm run capture
       ```
    *Screenshots will be output directly to the local `/screenshots` subdirectory grouped by device size.*
# Diabetic-Plus

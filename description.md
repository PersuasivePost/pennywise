# ✅ Node.js v20 Compatibility Update

This update resolves several issues that previously prevented the application from running on modern Node.js versions (v20+), particularly on **Windows systems**. The changes ensure compatibility while maintaining full existing functionality.

---

## 🛠 Summary of Changes

### 1. 🔄 Replaced `node-sass` with `sass`

- **Removed:** `node-sass@4.12.0` (caused native compilation failures on Node.js v20)
- **Added:** `sass@1.89.2` (Dart Sass – pure JS, no native bindings)
- **Symlink:** Created `node-sass → sass` to support legacy `sass-loader` expectations

### 2. 🔐 Fixed OpenSSL 3.0 Compatibility (Node.js v17+)

- **Updated `package.json` scripts:**
  - Added: `NODE_OPTIONS=--openssl-legacy-provider`
  - **Fixes:** `digital envelope routines::unsupported` error
- **Applied To:**
  - `react` script
  - `build` script

### 3. 🚫 Bypassed Create React App Preflight Checks

- **Added `.env` file:**
  - `SKIP_PREFLIGHT_CHECK=true`
- **Purpose:** Prevents `babel-jest` version warnings from blocking the app

### 4. 🧹 Cleaned Up Package Manager Conflicts

- **Removed:** `package-lock.json`  
  _(Prevents Yarn/npm version resolution inconsistencies)_

---

## 📂 Files Modified

- `package.json`  
  – Updated scripts to include `NODE_OPTIONS`

- `.env`  
  – Added for CRA preflight check bypass

### Dependencies

- **Removed:** `node-sass`
- **Added:** `sass`

---

## ✅ Testing Results

| Task             | Status                                            |
| ---------------- | ------------------------------------------------- |
| `yarn install`   | ✅ No errors                                      |
| `yarn start`     | ✅ React dev server + Electron app launch         |
| `yarn build`     | ✅ Production build successful                    |
| SCSS Compilation | ✅ Works with deprecation warnings (non-breaking) |

---

## 🧪 Compatibility

- **Node.js:** `v20.16.0` ✅
- **OS:** Windows 10 / 11 ✅
- **Functionality:** All features preserved ✅

---

This update ensures the application is fully compatible with modern development environments while preserving existing functionality.

---

#### Future plans

- Add docker to ensure everyone has same dependencies across all environments

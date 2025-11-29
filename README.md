# [MODULE][Xperia 1 VII] Wi-Fi 6E/7 + Tethering 5GHz (RU/US/CA/AU, non-official markets, Part 2)

Improved Part 2 release of my previous Wi-Fi 6E/7 + tethering + volume/touch module for the **Xperia 1 VII**, targeting non-official markets such as **RU / US / CA / AU**.

Xperia hardware is very capable, but some features – especially **Wi-Fi 6E / Wi-Fi 7** – are restricted by **region-based configs**.  
Sony tends to follow local wireless regulations strictly, so **advanced Wi-Fi bands are often limited to official launch regions only**.

This means that even if your Xperia 1 VII hardware supports Wi-Fi 6E/7, you may not see or use all bands in countries where the device was never officially sold.

This module tries to address exactly that.

> 📌 This project is published **both on XDA and on GitHub at the same time** so users in different communities can refer to the same content.

---

## 🔧 What this module does

### 1. Unlocks Wi-Fi 6E / Wi-Fi 7 for additional regions

Many OEMs ship very liberal country code lists, but Sony’s config is more conservative.  
This module expands the internal **country code list for Wi-Fi 6E (802.11ax) and Wi-Fi 7 (802.11be)**.

Specifically, it adds/adjusts entries for:

- **RU – Russia**
- **US – United States**
- **CA – Canada**
- **AU – Australia**

These regions have a relatively large Xperia user base, but the device (or specific bands) may not have been officially distributed there.  
With the extended country code config, **supported APs + supported bands can be used more fully** on Xperia 1 VII in those regions.

> **Effect:** where local regulations and your router allow it, you should be able to use **more Wi-Fi 6E/7 channels and bands** than with the stock config.

---

### 2. Fixes tethering 5GHz restrictions via TW region

On some **non-launch markets**, **5GHz tethering is limited or broken** due to regional settings. To avoid this:

- The module **sets the tethering (SoftAP) region to TW (Taiwan)**, which is an official Xperia launch market.
- Japan (JP) could technically allow additional 6GHz usage, but:
  - JP uses several special-case rules,
  - which can cause **compatibility issues** with non-JP routers and environments.

For general use, **TW has broader compatibility**, so:

> **Tethering on 5GHz should now work more reliably** when the device is configured with this TW profile.

If TW cannot be applied on SoftAP for some reason, the script falls back to the **local country** for that build (RU / US / CA / AU) to keep behavior safe.

---

### 3. Easy to customize for other countries

If your country is **not** in the current list:

- You can **open the module files and add your own region code**.
- The structure is intentionally simple so you can tweak it without much hassle.

This way, power users can adapt the module to their own regulatory region while still keeping the idea:

> “Let the Xperia hardware do what it’s capable of, within reasonable limits.”

---

## 🚀 Feature Summary

### ✅ Extended Wi-Fi 6E / Wi-Fi 7 support

- Expands the internal list of **Wi-Fi 6E/7 country codes**.
- Focus on **RU / US / CA / AU** so that:
  - Regular Wi-Fi (STA/client)
  - plus hotspot/tethering
  - can use **more bands/channels** where allowed by local rules and your router.

---

### 🎧 30-Step Volume Scaling

- System volume is adjusted to **30 steps** for finer control.
- Applies to:
  - **Alarm**
  - **Media**
  - **Call volume**, etc.
- This 30-step layout is a **commonly recommended “sweet spot”** in many Sony/Xperia communities:
  - Easier to find the “just right” volume between too loud and too quiet.

If you don’t want the volume tweaks, you can disable them yourself (see *Customization* below).

---

### ☎️ VoWiFi (Wi-Fi calling) toggle forced ON

- The module **forces Wi-Fi calling options to appear enabled** in the UI where possible.
- **Important:** actual behavior still depends on:
  - your **carrier’s VoWiFi support**, and
  - whether your **device is whitelisted** by that carrier.

So:

> You might see the toggle/UI for Wi-Fi calling even if the carrier does not fully support it on this model.

---

### 🖐️ Improved touch sensitivity

- Tweaks touch configuration for **more responsive and precise input**.
- Aimed at:
  - smoother scrolling,
  - better touch tracking in games,
  - and more reliable taps/gestures in daily use.

Again, these tweaks are easy to disable via `system.prop` if you prefer stock behavior.

---

## 📦 Variants

The release usually includes **separate ZIPs** tuned for each non-official region:

- `...WiFiRU_TetherTW_VolumeFix_*.zip`
- `...WiFiUS_TetherTW_VolumeFix_*.zip`
- `...WiFiCA_TetherTW_VolumeFix_*.zip`
- `...WiFiAU_TetherTW_VolumeFix_*.zip`

All of them share the same concept:

- **Wi-Fi (STA/client) = local country** (RU/US/CA/AU)  
- **Tethering (SoftAP) = TW**, with safe fallback to the local country if TW can’t be applied.

---

## 🔧 Installation

1. Download the ZIP for your region from the **Releases** page.  
2. Flash as a module via **Magisk** or **KernelSU**:
   - Magisk app → Modules → Install from storage → select ZIP → reboot  
   - or KernelSU Manager → Modules → install → select ZIP → reboot  
3. After reboot:
   - Make sure Wi-Fi and hotspot work normally.
   - If hotspot was already ON before flashing, toggle it **OFF → ON** once so that the TW channels are applied.

> ⚠️ If you are already using other Wi-Fi country / tether / audio-tweak modules, please be careful about conflicts. In most cases only one of these should control Wi-Fi country code and volume/touch behavior.

---

## 🛠 Customization (system.prop)

If you want to see exactly what this module does, you can simply **unzip it** and inspect the files such as:

- `system.prop`  
- `service.sh`  
- `post-fs-data.sh`  

All important parts are commented in the **local language** for each build, and this module is published **both on XDA and on GitHub at the same time**, so everything is transparent inside the zip.

If you **don’t need** some of the extra tweaks, you can edit them yourself:

- For example:
  - **30-step volume scaling**
  - **touch sensitivity tuning**
- Steps:
  1. Unzip the module.
  2. Open `system.prop`.
  3. Remove or comment out only the lines you don’t want.
  4. Re-zip the folder as a Magisk/KernelSU module (`.zip`) again.
  5. Flash your customized version.

> 💡 You’re free to reuse or modify this module for your own setup – the whole point is to help more Xperia users actually enjoy the hardware they already paid for.

---

## ⚠️ Note on VoLTE / RF bands

This module is **not** related to:

- VoLTE provisioning  
- RF band unlocking / carrier band profiles  

Those are separate topics.

A dedicated VoLTE solution for these regions is not written yet, and band-set / carrier band configuration is already covered in existing XDA threads (for example, global 5G/LTE CA band enabling threads).

Please refer to those separately if you’re specifically looking for:

- custom carrier configs,  
- VoLTE/VoWiFi provisioning by MCC/MNC,  
- or full RF band unlocks.

---

## 🔗 Links

- XDA thread:xdaforums.com/t/module-xperia-1-vii-wi-fi-6e-7-tethering-5ghz-for-ru-us-ca-au-non-official-markets-part-2.4769484/  
  *(add your actual XDA URL here, e.g. the Part 2 Wi-Fi 6E/7 thread)*  

- GitHub Releases:  
  *(this repository’s Releases tab)*  

---

## 🙏 Credits

- Sony Xperia community (KR, RU, VN, etc.) for testing and feedback.  
- Tooling and base environment provided by **Magisk** / **KernelSU**.  
- Everyone reporting logs and sharing regional behavior so this could be tuned for real-world use.

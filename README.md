# 📶 WiFi QR — Bruce / LilyGO T-Embed CC1101

[![Bruce firmware](https://img.shields.io/badge/firmware-Bruce-8A2BE2?logo=github)](https://github.com/BruceDevices/firmware) [![Device](https://img.shields.io/badge/device-LilyGO%20T--Embed%20CC1101-1E90FF)](https://github.com/BruceDevices/firmware) [![Language](https://img.shields.io/badge/script-JavaScript%20(BJS)-F7DF1E)](https://github.com/BruceDevices/firmware) [![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

> **EN** — Connect to a Wi-Fi network, then show a **scannable QR code** of it on the screen. A guest just points their phone camera at it to join — no typing. The QR is rendered by a from-scratch QR encoder running on the device (no PC, no internet, no native QR support needed).

> **FR** — Connecte-toi à un réseau Wi-Fi, puis affiche un **QR code scannable** de ce réseau à l'écran. Un invité pointe simplement l'appareil photo de son téléphone dessus pour se connecter — sans rien taper. Le QR est généré par un encodeur QR maison qui tourne sur l'appareil (sans PC, sans internet).

![WiFi QR code on the device](docs/qr.jpg)

## ✨ How it works / Fonctionnement

- **Already connected?** → it shows the QR of your current network right away.
- **Not connected?** → it lists nearby networks; pick one, and it connects first (password taken from Bruce's saved networks, or typed), then shows the QR.
- Passwords come from Bruce's own config (`/bruce.conf`, key `wifi`), so for saved networks you don't even retype them.

| Intro | Connecting | QR |
|---|---|---|
| ![splash](docs/splash.jpg) | ![connecting](docs/connecting.jpg) | ![qr](docs/qr.jpg) |

## 🧠 The QR encoder

Bruce's JS interpreter has **no native QR (nor PNG) support**, so the QR is built entirely in JavaScript: byte-mode segmentation, Reed–Solomon error correction over GF(256), matrix construction, and automatic mask selection. It's a compact ES5 port of **[Nayuki's QR Code generator](https://www.nayuki.io/page/qr-code-generator-library)** (MIT), **verified on PC** by decoding every generated code back with the `jsQR` decoder. It's reusable for any QR need (URL, contact vCard, text…).

## 🚀 Install

1. Copy **`WiFi QR.js`** onto the SD card (e.g. `/scripts` or `/BruceJS`).
2. On the device: **JS Interpreter → select `WiFi QR.js`** (or add it to your favorites with [bruce-launcher](https://github.com/koua29/bruce-launcher)).
3. **Rotate** = move · **click** = select · **ESC** = back/quit.

## 🔒 Privacy

This reads the Wi-Fi passwords stored **on your own device** to build the QR, and the QR itself encodes the password (that's the point of sharing it). Use it for **your own** networks / guests. Don't publish a screenshot of a QR of a network whose password is still live.

## 🛒 Matériel / Hardware

Accessoires utiles pour ce projet — liens affiliés Amazon :

| [<img src="docs/amazon-B0GXB24SRR.jpg" width="200" alt="T-Embed CC1101 screen protector">](https://www.amazon.com/dp/B0GXB24SRR?linkCode=ll2&tag=koua29-20&ref_=as_li_ss_tl) | [<img src="docs/amazon-B0C1FCZM94.jpg" width="200" alt="433 MHz SMA antenna (2-pack)">](https://www.amazon.com/dp/B0C1FCZM94?linkCode=ll2&tag=koua29-20&ref_=as_li_ss_tl) | [<img src="docs/amazon-B0B7NVMBPL.jpg" width="200" alt="SanDisk 64 GB microSD (2-pack)">](https://www.amazon.com/dp/B0B7NVMBPL?linkCode=ll2&tag=koua29-20&ref_=as_li_ss_tl) |
|:---:|:---:|:---:|
| 🛡️ **[T-Embed CC1101 screen protector](https://www.amazon.com/dp/B0GXB24SRR?linkCode=ll2&tag=koua29-20&ref_=as_li_ss_tl)**<br><sub>Lamshaw, film TPU ×6</sub> | 📡 **[433 MHz SMA antenna (2-pack)](https://www.amazon.com/dp/B0C1FCZM94?linkCode=ll2&tag=koua29-20&ref_=as_li_ss_tl)**<br><sub>Antenne sub-GHz pour la radio CC1101</sub> | 💾 **[SanDisk 64 GB microSD (2-pack)](https://www.amazon.com/dp/B0B7NVMBPL?linkCode=ll2&tag=koua29-20&ref_=as_li_ss_tl)**<br><sub>Pour les thèmes, scripts et captures Bruce</sub> |

<sub>En tant que Partenaire Amazon, je réalise un bénéfice sur les achats remplissant les conditions requises. · As an Amazon Associate I earn from qualifying purchases.</sub>

## 🙏 Credits & License

- Script: **koua29**. Runs on the excellent **[Bruce firmware](https://github.com/BruceDevices/firmware)**.
- QR encoder ported from **[Nayuki's QR Code generator](https://www.nayuki.io/page/qr-code-generator-library)** (MIT).
- Released under the **MIT License** — see [LICENSE](LICENSE).

## ☕ Coffee?

<img src="docs/paypal-qr.png" width="170" alt="PayPal" />

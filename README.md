# 🔐 SecretShare

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Size: 1 file](https://img.shields.io/badge/Size-1_file-blue.svg)
![Dependencies: None](https://img.shields.io/badge/Dependencies-None-brightgreen.svg)
![Security: Web_Crypto_API](https://img.shields.io/badge/Security-Web_Crypto_API-blueviolet.svg)

**A minimalist, zero-backend, end-to-end encrypted note sharer that lives entirely in your browser.**

Inspired by [textarea](https://github.com/antonmedv/textarea), **SecretShare** allows you to create secure, encrypted notes that are stored directly in the URL hash. Since the data never leaves the client-side, not even the host (like GitHub Pages) can read your messages.

[Live Demo](https://www.google.com/search?q=%23) ---

## ✨ Features

| Feature | Description |
| --- | --- |
| **Zero Backend** | No database. No server. No logs. 100% serverless. |
| **AES-GCM Encryption** | Industry-standard encryption via the native Web Crypto API. |
| **URL-Based Storage** | The encrypted payload is stored in the URL hash (`#`). |
| **QR Generation** | Instantly generate a QR code for mobile-to-mobile sharing. |
| **PWA Ready** | Works as a single `index.html` file. Host it anywhere. |

---

## 🛠 How it Works

SecretShare uses the **"Zero-Knowledge"** principle.

1. **Derivation:** Your password is run through a **PBKDF2** derivation function with a unique salt to create a 256-bit key.
2. **Encryption:** Your message is encrypted using **AES-GCM** (Advanced Encryption Standard with Galois/Counter Mode).
3. **Encoding:** The resulting salt, IV (Initialization Vector), and ciphertext are bundled and encoded into **Base64**.
4. **Distribution:** This string is appended to the URL as a hash.

> [!IMPORTANT]
> Because the data is stored in the URL hash (`#`), it is **never sent to the server**. Your secrets remain strictly between you and your recipient.

---

## 🛠 Why Native Web Crypto?

Unlike many web-based encryption tools that rely on third-party JavaScript libraries (like `CryptoJS`), **SecretShare** is built on the [Web Crypto API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API).

### 1. Hardened Security (No Supply Chain Risk)

External libraries are subject to "supply chain attacks"—if a dependency is compromised, your encryption is, too. Web Crypto is built into the browser engine (Chromium, WebKit, Gecko) and audited by security teams at Google, Apple, and Mozilla.

### 2. Performance & Power

Native code is faster. By offloading encryption to the browser's optimized C++ or Rust internals, SecretShare handles encryption/decryption with near-zero latency and minimal battery impact on mobile devices.

### 3. Zero-Footprint

* **External Libs:** Often add 50KB–200KB to your project.
* **Web Crypto:** 0KB. It’s already there in your browser. This is what keeps this project ultra-minimal and lightning-fast.

### 4. Constant-Time Operations

The Web Crypto API is designed to be resistant to **side-channel attacks** (like timing attacks) because the implementation of algorithms like AES-GCM is handled by the OS/Browser in a "constant-time" manner, something very difficult to achieve with standard JavaScript.

---

## 🚀 Quick Start

### 1. Host it yourself

Since it's a single file, you can get this running in seconds:

1. Copy the `index.html` to your repository.
2. Enable **GitHub Pages** in Settings > Pages.
3. You're done.

### 2. Usage

1. Type your secret message.
2. Enter a strong password.
3. Click **Generate Secure Link**.
4. Share the URL or the QR code with your recipient.
5. (Optional) Send the password via a *different* channel for maximum security.

---

## 🔒 Security Note

While the encryption used (AES-GCM) is cryptographically "broken-link" proof, the security of your message depends on:

* The strength of your password.
* The security of the channel used to share the link.
* Ensuring you don't send the password and the link in the same message!

---

## 🤝 Contributing

This project aims to stay **minimal**. If you have ideas for features that don't require a backend (like compression or better UI themes), feel free to open a PR!

---

## 📜 License

MIT © [Behzad Khanlar]
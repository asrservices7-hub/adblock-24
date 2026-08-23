# Render Adblocker (DNS-over-HTTPS)

This is a lightweight DNS-over-HTTPS (DoH) server powered by [Blocky](https://0xignite.github.io/blocky/). It blocks ads at the DNS level, meaning it works across your entire system, both on **mobile** and **web/desktop**, without needing a browser extension.

## How it works
Render provides an HTTPS endpoint for Web Services. We run Blocky on Render, which acts as a DNS server that understands DoH (DNS-over-HTTPS). 
When your phone or browser tries to load an ad domain, Blocky intercepts the request using a massive community-maintained blocklist and returns an empty address (`0.0.0.0`), preventing the ad from popping up or loading.

## Deployment to Render
1. Push this folder (`adblock-doh`) to a new repository on your GitHub.
2. Go to [Render Dashboard](https://dashboard.render.com/).
3. Click **New** -> **Web Service**.
4. Connect the GitHub repository you just created.
5. Render will automatically detect the `Dockerfile`.
6. Click **Create Web Service**.
7. Once deployed, Render will give you a URL like `https://adblock-doh-xxxx.onrender.com`.

## How to use it on your devices

Your DoH endpoint will be: **`https://your-render-url.onrender.com/dns-query`**

### Web Browsers (Desktop & Mobile)
- **Chrome/Edge**: Go to Settings -> Privacy and security -> Security -> Use secure DNS -> Choose "With Custom" and paste your DoH endpoint.
- **Firefox**: Go to Settings -> Privacy & Security -> DNS over HTTPS -> Max Protection -> Choose "Custom" and paste your DoH endpoint.

### Android
- Android natively supports **Private DNS**, but by default, it uses DNS-over-TLS (DoT) instead of DoH. 
- To use DoH on Android, you can use a free app like **Nebulo** or **Intra** (by Jigsaw). Add your custom DoH URL in the app to protect your entire phone.
- *(Note: Android 13+ has some native DoH support, but it's often carrier/OEM dependent. Using the browser's Secure DNS setting works immediately for all web browsing).*

### iOS / macOS
- You can create a native Configuration Profile using a tool like [dns.notjakob.com](https://dns.notjakob.com/tool.html). 
- Select **DoH (DNS over HTTPS)**, paste your DoH endpoint, download the profile, and install it in your Settings app. This protects your entire iPhone or Mac natively.

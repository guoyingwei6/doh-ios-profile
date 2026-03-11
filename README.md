# Guoyingwei Self-hosted DoH for iOS

One-click DNS over HTTPS profile for iPhone / iPad using `doh.guoyingwei.top`. No proxy software required.

> 一键让 iPhone / iPad 全局使用自建 DoH 服务器，无需任何代理软件。

---

## Install (Open in iPhone Safari)

| Profile | Server | Description |
|---------|--------|-------------|
| [Guoyingwei DoH](https://raw.githubusercontent.com/guoyingwei/doh-ios-profile/main/Guoyingwei-DoH.mobileconfig) | `doh.guoyingwei.top` | Self-hosted, clean, no logging |

**Direct link:**
```
https://raw.githubusercontent.com/guoyingwei/doh-ios-profile/main/Guoyingwei-DoH.mobileconfig
```

> Open the link above in **Safari** on your iPhone (not Chrome/Firefox).

---

## How to Install

1. Open the link above in **Safari**
2. Tap **Allow** when prompted to download the profile
3. Go to **Settings → General → VPN & Device Management**
4. Tap the downloaded profile → **Install** → enter passcode → **Install**
5. Reboot recommended

To remove: **Settings → General → VPN & Device Management** → tap profile → **Remove**

---

## How to Verify

Visit [dnsleaktest.com](https://dnsleaktest.com) → Extended Test → confirm resolver shows `doh.guoyingwei.top`.

---

## Warning

- This profile routes **all DNS queries** from every app (Safari, WeChat, banking apps, etc.) through my server.
- I do not log any queries — but you are trusting my server by installing this.
- Use at your own risk. Uninstall anytime via Settings.
- To get the latest version, simply re-open the install link above.

---

## Related Projects

- [paulmillr/encrypted-dns](https://github.com/paulmillr/encrypted-dns) — curated public DoH/DoT profiles

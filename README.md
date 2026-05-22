# Self-hosted DoH for iOS

One-click DNS over HTTPS profile for iPhone / iPad using a self-hosted server. No proxy software required.

**Server:** `doh.guoyingwei.top` (Cloudflare Workers, no logging)

> [中文说明](#中文说明)

---

## Install (Open in iPhone Safari)

**Direct link:**
```
https://guoyingwei6.github.io/doh-ios-profile/DOH-GYW.mobileconfig
```

> Must be opened in **Safari** — Chrome/Firefox cannot install profiles.

---

## How to Install

1. Open the link above in **Safari**
2. Tap **Allow** when prompted to download the profile
3. Go to **Settings → General → VPN & Device Management**
4. Tap the downloaded profile → **Install** → enter passcode → **Install**
5. Reboot recommended

To remove: **Settings → General → VPN & Device Management** → tap profile → **Remove**

---

## Profile Details

| Field | Value | Description |
|-------|-------|-------------|
| `ServerURL` | `https://doh.guoyingwei.top/dns-query` | DoH query endpoint |
| `ServerName` | `doh.guoyingwei.top` | TLS SNI hostname |
| `ServerAddresses` | `1.1.1.1`, `1.0.0.1` | Bootstrap IPs — fixes iOS cold-start DNS deadlock |

**Why bootstrap IPs?** When iOS first connects to a DoH server, it needs to resolve the domain — but the DNS *is* that DoH server (deadlock). `ServerAddresses` provides Cloudflare's permanent IPs (`1.1.1.1`/`1.0.0.1`) as a bootstrap so iOS can resolve the domain and then switch fully to the self-hosted DoH.

---

## Verify

Visit [dnsleaktest.com](https://dnsleaktest.com) → Extended Test → confirm the resolver shows `doh.guoyingwei.top`.

---

## Warning

- This profile routes **all DNS queries** from every app through this server.
- No queries are logged — but installing means you trust this server.
- Re-open the install link anytime to get the latest version.

---

## Related

- [paulmillr/encrypted-dns](https://github.com/paulmillr/encrypted-dns) — curated public DoH/DoT profiles

---

## 中文说明

一键让 iPhone / iPad 全局使用自建 DoH（DNS over HTTPS）服务器，无需任何代理软件。

**服务器：** `doh.guoyingwei.top`（基于 Cloudflare Workers 自建，无日志）

**安装直链（Safari 打开）：**
```
https://guoyingwei6.github.io/doh-ios-profile/DOH-GYW.mobileconfig
```

**安装步骤：**
1. Safari 打开上方链接
2. 弹出提示点 **允许**
3. 前往 **设置 → 通用 → VPN与设备管理**
4. 点击描述文件 → **安装** → 输入密码 → **安装**
5. 建议重启

**Profile 字段说明：**

| 字段 | 说明 |
|------|------|
| `ServerURL` | DoH 查询端点 |
| `ServerName` | TLS SNI 域名 |
| `ServerAddresses` | Bootstrap IP（`1.1.1.1`/`1.0.0.1`），解决 iOS 冷启动 DNS 死锁 |

**注意：** 描述文件会将所有 App 的 DNS 查询路由到该服务器，服务器不记录日志，但安装即代表信任。

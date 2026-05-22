# Self-hosted DoH for iOS

一键让 iPhone / iPad 全局使用自建 DoH（DNS over HTTPS）服务器，无需任何代理软件。

**服务器：** `doh.guoyingwei.top`（基于 Cloudflare Workers 自建，无日志）

---

## 安装（用 iPhone Safari 打开）

**直链：**
```
https://guoyingwei6.github.io/doh-ios-profile/DOH-GYW.mobileconfig
```

> 必须用 **Safari** 打开，Chrome/Firefox 不支持安装描述文件。

---

## 安装步骤

1. Safari 打开上方链接
2. 弹出提示点 **允许**（下载描述文件）
3. 前往 **设置 → 通用 → VPN与设备管理**
4. 点击已下载的描述文件 → **安装** → 输入密码 → **安装**
5. 建议重启一次

卸载：**设置 → 通用 → VPN与设备管理** → 点击描述文件 → **移除描述文件**

---

## Profile 说明

| 字段 | 值 | 说明 |
|------|----|------|
| `ServerURL` | `https://doh.guoyingwei.top/dns-query` | DoH 查询端点 |
| `ServerName` | `doh.guoyingwei.top` | TLS SNI 域名 |
| `ServerAddresses` | `1.1.1.1`, `1.0.0.1` | Bootstrap IP，解决 iOS 冷启动时 DNS 死锁问题 |

**Bootstrap 原理：** iOS 首次连接 DoH 服务器时需要先解析域名，但 DNS 就是该 DoH 本身（死锁）。`ServerAddresses` 填入 Cloudflare 固定 IP（`1.1.1.1`/`1.0.0.1`）作为引导，iOS 用这两个 IP 解析域名后再切换到自建 DoH，之后全程走自建服务器。

---

## 验证

访问 [dnsleaktest.com](https://dnsleaktest.com) → Extended Test → 确认解析器显示 `doh.guoyingwei.top`。

---

## 注意事项

- 描述文件会将设备**所有 App 的 DNS 查询**（Safari、微信、银行 App 等）路由到该服务器
- 服务器不记录任何查询日志，但安装即代表信任该服务器
- 重新打开安装链接即可更新到最新版本

---

## 相关项目

- [paulmillr/encrypted-dns](https://github.com/paulmillr/encrypted-dns) — 公共 DoH/DoT 描述文件合集

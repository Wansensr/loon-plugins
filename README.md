# loon-plugins

Loon 插件集合。

## passkey-fix.plugin — 通行密钥登录修复

让 iPhone 开着 Loon 也能扫电脑上的通行密钥二维码。做两件事：

1. Apple 鉴权与钥匙串域名走直连（apple.com / icloud.com / icloud.com.cn / apple-cloudkit.com / cdn-apple.com / aaplimg.com / entrust.net）
2. 把通行密钥相关域名排除出 MITM 解密（关键的一条）

本插件不改变隧道域名 `ua5v.com` 的分流方向。

### 订阅地址

```
https://raw.githubusercontent.com/Wansensr/loon-plugins/main/passkey-fix.plugin
```

Loon → 配置 → 插件 → 右上角 `+` → 从 URL 添加。
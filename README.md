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
## Loon 分流规则集（geosite + blackmatrix7 合并）

本目录下的规则由本机 Clash `geosite.dat` 与 blackmatrix7 的 Loon 规则集合并生成，已转换为 Loon 可直接读取的 `DOMAIN-SUFFIX,...` 等格式。

| 文件 | 建议策略 | 内容 |
| --- | --- | --- |
| `Lan.list` | `DIRECT` | 私有/局域网域名与 IP |
| `China.list` | `DIRECT` | 中国域名（geosite CN + blackmatrix7 China） |
| `Proxy.list` | `MainProxy` | GFW/常用代理域名（geosite GFW + blackmatrix7 Proxy） |
| `Global.list` | `MainProxy` | 非中国/全球域名（geosite GEOLOCATION-!CN + blackmatrix7 Global） |

### 订阅地址

```text
https://raw.githubusercontent.com/Wansensr/loon-plugins/main/rules/Lan.list
https://raw.githubusercontent.com/Wansensr/loon-plugins/main/rules/China.list
https://raw.githubusercontent.com/Wansensr/loon-plugins/main/rules/Proxy.list
https://raw.githubusercontent.com/Wansensr/loon-plugins/main/rules/Global.list
```

### Loon `[Remote Rule]` 推荐顺序

```ini
https://raw.githubusercontent.com/Wansensr/loon-plugins/main/rules/Lan.list,DIRECT
https://raw.githubusercontent.com/Wansensr/loon-plugins/main/rules/China.list,DIRECT
https://raw.githubusercontent.com/Wansensr/loon-plugins/main/rules/Proxy.list,MainProxy
https://raw.githubusercontent.com/Wansensr/loon-plugins/main/rules/Global.list,MainProxy
```

顺序建议为 Lan → China → Proxy → Global：让中国域名优先直连，避免被后面的 Global 规则抢走。
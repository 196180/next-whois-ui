
<div align="center">

# 🧪 Next Whois UI

😎 轻量且美观的 Whois 查询工具

[English](README.md) | [简体中文](README_CN.md)

[![Deploy to Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/zmh-program/next-whois-ui)

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/zmh-program/next-whois-ui)

</div>

## 😎 特性

无需多言，直接试试吧！🥳

1. ✨ **漂亮的界面**：采用现代设计的 [Shadcn UI](https://ui.shadcn.com)，让您使用时感到舒适。
2. 📱 **响应式设计**：适配手机✅ / 平板✅ / 桌面✅，并支持 PWA 应用。
3. 🌈 **多主题支持**：支持多种主题（*亮色 & 暗色*），系统主题自动检测，随心切换。
4. 🚀 **灵活的查询**：基于 Next.js，支持无服务器部署，查询速度快。
5. 📚 **历史记录**：历史记录存储在本地存储中，方便查看和查询历史。
6. 📡 **开放 API**：提供简单的 whois 查询 API，易于与其他服务集成。
7. 🌍 **IPv4 & IPv6 Whois 查询**：支持 IPv4、IPv6、域名、ASN、CIDR 的 Whois 查询。
8. 📦 **查询结果分享**：支持获取 Whois 查询结果，方便分享和保存。
9. 📡 **Whois 缓存**：支持基于 Redis 的 Whois 缓存，提升查询速度。
10. 🌍 [进行中] **国际化**：支持多语言。([#6](https://github.com/zmh-program/next-whois-ui/issues/6))

👉 [创建拉取请求](https://github.com/zmh-program/next-whois-ui/pulls)

## 部署

#### `1` 🚀 平台（推荐）

[Vercel](https://vercel.com/import/project?template=https://github.com/zmh-program/next-whois-ui) / [Netlify](https://app.netlify.com/start/deploy?repository=https://github.com/zmh-program/next-whois-ui) / [Zeabur](https://zeabur.com/templates/UHCCCT)

#### `2` 🐳 Docker

```bash
docker run -d -p 3000:3000 programzmh/next-whois-ui
```

#### `3` 🔨 源代码

```bash
git clone https://github.com/zmh-program/next-whois-ui
cd next-whois-ui

npm install -g pnpm
pnpm install
pnpm dev
```

## 📏 环境变量

### SEO

- `NEXT_PUBLIC_SITE_TITLE`: 站点标题
- `NEXT_PUBLIC_SITE_DESCRIPTION`: 站点描述
- `NEXT_PUBLIC_SITE_KEYWORDS`: 站点关键词

### WHOIS

- `NEXT_PUBLIC_HISTORY_LIMIT`: 历史记录限制（默认值：6）
- `NEXT_PUBLIC_MAX_WHOIS_FOLLOW`: 最大域名 Whois 跟随数（默认值：0）
- `NEXT_PUBLIC_MAX_IP_WHOIS_FOLLOW`: 最大 IP Whois 跟随数（默认值：5）

### 缓存

- `REDIS_HOST`: Redis 主机（如果为空则禁用缓存）
- `REDIS_PORT`: Redis 端口（默认值：6379）
- `REDIS_PASSWORD`: Redis 密码（可选）
- `REDIS_DB`: Redis 数据库（默认值：0）
- `REDIS_CACHE_TTL`: Redis 缓存 TTL 秒数（默认值：3600）

## 📝 API 参考

`GET` `/api/lookup?query=google.com`

<details>
<summary><strong>响应</strong> OK (200)</summary>

```json
{
  "time": 1.547,
  "status": true,
  "cached": false,
  "result": {
    "domain": "GOOGLE.COM",
    "registrar": "MarkMonitor Inc.",
    "registrarURL": "http://www.markmonitor.com",
    "ianaId": "292",
    "whoisServer": "whois.markmonitor.com",
    "updatedDate": "2019-09-09T15:39:04.000Z",
    "creationDate": "1997-09-15T04:00:00.000Z",
    "expirationDate": "2028-09-14T04:00:00.000Z",
    "status": [
      {
        "status": "clientDeleteProhibited",
        "url": "https://icann.org/epp#clientDeleteProhibited"
      },
      {
        "status": "clientTransferProhibited",
        "url": "https://icann.org/epp#clientTransferProhibited"
      },
      {
        "status": "clientUpdateProhibited",
        "url": "https://icann.org/epp#clientUpdateProhibited"
      },
      {
        "status": "serverDeleteProhibited",
        "url": "https://icann.org/epp#serverDeleteProhibited"
      },
      {
        "status": "serverTransferProhibited",
        "url": "https://icann.org/epp#serverTransferProhibited"
      },
      {
        "status": "serverUpdateProhibited",
        "url": "https://icann.org/epp#serverUpdateProhibited"
      }
    ],
    "nameServers": [
      "NS1.GOOGLE.COM",
      "NS2.GOOGLE.COM",
      "NS3.GOOGLE.COM",
      "NS4.GOOGLE.COM"
    ],
    "registrantOrganization": "Unknown",
    "registrantProvince": "Unknown",
    "registrantCountry": "Unknown",
    "registrantPhone": "+1 2086851750",
    "registrantEmail": "Unknown",
    "rawWhoisContent": "..."
  }
}
```

</details>

<details>
<summary><strong>错误响应</strong> 内部服务器错误 (500)</summary>

```json
{
  "time": 0.609,
  "status": false,
  "error": "No match for domain google.notfound (e.g. domain is not registered)"
}
```

</details>

<details>
<summary><strong>错误响应</strong> 错误请求 (400)</summary>

```json
{
  "time": -1,
  "status": false,
  "error": "Query is required"
}
```

</details>

## 🧠 技术栈

- Next.js
- Shadcn UI & Tailwind CSS
- Whois Core Lib (@[whois-raw](https://www.npmjs.com/package/whois-raw))

## 💪 TLDs 支持

👉 [TLDs Whois 解析器库源码](./src/lib/whois/lib.ts)

❤ 提示: 部分 TLDs 的 Whois 解析器可能暂不兼容，感谢您提交 [拉取请求](https://github.com/zmh-program/next-whois-ui/pulls) 以便支持更多 TLDs！

# PasarGuard 订阅模板

PasarGuard 的响应式订阅页面模板。

> **说明：** 这是 [Free-Guy-IR](https://github.com/Free-Guy-IR) 对原版 [PasarGuard 订阅模板](https://github.com/PasarGuard/subscription-template) 的分支，扩展支持了该分支新增的核心类型：**OpenVPN Config** 行（下载 + 复制，与 WireGuard 的展示方式一致）以及 **MTProto（Telegram 代理）** 行（`tg://` 链接，仅提供复制 - 不提供二维码，因为这类链接并不需要扫描）。

<p align="center">
  <img src="https://raw.githubusercontent.com/PasarGuard/subscription-template/refs/heads/main/screenshots/en.png" alt="English UI" width="40%">
  <img src="https://raw.githubusercontent.com/PasarGuard/subscription-template/refs/heads/main/screenshots/fa.png" alt="Persian UI" width="30%">
</p>

## 功能

- 语言：`en`、`fa`、`zh`、`ru`
- 用户可在界面中切换语言
- 响应式布局
- 深色模式
- 连接链接 QR 码
- 一键复制链接和配置，Base64 复制仅在 QR 弹窗中提供
- WireGuard 链接可复制为原生配置，也可下载为 `.conf`
- OpenVPN 拥有独立的配置行（下载 `.ovpn` 或复制），而不是通用链接
- MTProto（Telegram 代理，`tg://`）链接拥有自己的行，显示真实名称而非通用占位名
- [外观自定义](#appearance-customization)

## 兼容性

| 订阅模板版本 | 面板版本 |
| --- | --- |
| `v2` | `v3`（此分支） |
| 其他版本 | `v2`、`v1` |

## 快速安装（推荐）

运行安装脚本（选择默认语言）：

```sh
curl -fsSL https://raw.githubusercontent.com/Free-Guy-IR/subscription-template/main/install.sh | sudo bash -s -- --lang zh
```

`--lang` 支持：`en`、`fa`、`zh`、`ru`
`--version` 支持：`latest`（默认）或像 `v2.0.0` 这样的发布标签
如需安装指定版本，请添加 `--version <tag>`。

## 手动安装

1. 下载模板：

```sh
sudo mkdir -p /var/lib/pasarguard/templates/subscription
sudo wget -O /var/lib/pasarguard/templates/subscription/index.html \
https://github.com/Free-Guy-IR/subscription-template/releases/latest/download/zh.html
```

2. 在 `/opt/pasarguard/.env` 中配置 PasarGuard：

```dotenv
CUSTOM_TEMPLATES_DIRECTORY="/var/lib/pasarguard/templates/"
SUBSCRIPTION_PAGE_TEMPLATE="subscription/index.html"
```

3. 重启：

```sh
pasarguard restart
```

## 从源码构建

```sh
git clone https://github.com/Free-Guy-IR/subscription-template.git
cd subscription-template
bun install
bun run build
```

使用生成的文件：

```sh
sudo cp dist/index.html /var/lib/pasarguard/templates/subscription/index.html
```

<a id="appearance-customization"></a>

## 外观自定义

在 `.env` 中设置下面的值，然后重新构建：

```dotenv
VITE_PRIMARY_COLOR_LIGHT=oklch(0.48 0.11 250)
VITE_PRIMARY_COLOR_DARK=oklch(0.60 0.12 250)
VITE_BORDER_RADIUS=0.65rem
```

## 其他语言

- [English](README.md)
- [فارسی (Persian)](README.fa.md)
- [Русский (Russian)](README.ru.md)

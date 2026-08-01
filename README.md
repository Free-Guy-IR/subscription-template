# PasarGuard Subscription Template

Responsive subscription page template for PasarGuard.

> **Note:** This is the [Free-Guy-IR](https://github.com/Free-Guy-IR) fork of the original [PasarGuard subscription-template](https://github.com/PasarGuard/subscription-template), extended to support the fork's extra core types: an **OpenVPN Config** row (download + copy, matching the WireGuard presentation) and an **MTProto (Telegram proxy)** row (`tg://` links, copy-only - no QR code, since these links aren't meant to be scanned).

<p align="center">
  <img src="https://raw.githubusercontent.com/PasarGuard/subscription-template/refs/heads/main/screenshots/en.png" alt="English UI" width="40%">
  <img src="https://raw.githubusercontent.com/PasarGuard/subscription-template/refs/heads/main/screenshots/fa.png" alt="Persian UI" width="30%">
</p>

## Features

- Languages: `en`, `fa`, `zh`, `ru`
- User can switch language in UI
- Responsive layout
- Dark mode
- QR code for connection links
- Copy links/configs in one click, with Base64 copy available only in the QR modal
- WireGuard links can be copied as native config or downloaded as `.conf`
- OpenVPN gets a dedicated config row (download `.ovpn` or copy) instead of a generic link
- MTProto (Telegram proxy, `tg://`) links get their own row with a real name instead of a generic fallback
- [Appearance customization](#appearance-customization)

## Compatibility

| Subscription Template | Panel |
| --- | --- |
| `v2` | `v3` (this fork) |
| Other versions | `v2`, `v1` |

## Quick Start (Recommended)

Run installer script (choose your fallback language):

```sh
curl -fsSL https://raw.githubusercontent.com/Free-Guy-IR/subscription-template/main/install.sh | sudo bash -s -- --lang fa
```

Supported values for `--lang`: `en`, `fa`, `zh`, `ru`
Supported values for `--version`: `latest` (default) or a release tag like `v2.0.0`
To install a specific release, add `--version <tag>`.

## Manual Install

1. Download template:

```sh
sudo mkdir -p /var/lib/pasarguard/templates/subscription
sudo wget -O /var/lib/pasarguard/templates/subscription/index.html \
https://github.com/Free-Guy-IR/subscription-template/releases/latest/download/index.html
```

2. Configure PasarGuard in `/opt/pasarguard/.env`:

```dotenv
CUSTOM_TEMPLATES_DIRECTORY="/var/lib/pasarguard/templates/"
SUBSCRIPTION_PAGE_TEMPLATE="subscription/index.html"
```

3. Restart:

```sh
pasarguard restart
```

## Build From Source

```sh
git clone https://github.com/Free-Guy-IR/subscription-template.git
cd subscription-template
bun install
bun run build
```

Use the built file:

```sh
sudo cp dist/index.html /var/lib/pasarguard/templates/subscription/index.html
```

<a id="appearance-customization"></a>

## Appearance Customization

Set these in `.env` and build again:

```dotenv
VITE_PRIMARY_COLOR_LIGHT=oklch(0.48 0.11 250)
VITE_PRIMARY_COLOR_DARK=oklch(0.60 0.12 250)
VITE_BORDER_RADIUS=0.65rem
```

## Other Languages

- [فارسی (Persian)](README.fa.md)
- [Русский (Russian)](README.ru.md)
- [中文 (Chinese)](README.zh.md)

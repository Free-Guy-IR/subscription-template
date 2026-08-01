# Шаблон подписки PasarGuard

Адаптивный шаблон страницы подписки для PasarGuard.

> **Примечание:** Это форк [Free-Guy-IR](https://github.com/Free-Guy-IR) оригинального [шаблона подписки PasarGuard](https://github.com/PasarGuard/subscription-template), расширенный для поддержки дополнительных типов ядра этого форка: строка **OpenVPN Config** (скачивание + копирование, как у WireGuard) и строка **MTProto (Telegram-прокси)** (ссылки `tg://`, только копирование - без QR, так как эти ссылки не предназначены для сканирования).

<p align="center">
  <img src="https://raw.githubusercontent.com/PasarGuard/subscription-template/refs/heads/main/screenshots/en.png" alt="English UI" width="40%">
  <img src="https://raw.githubusercontent.com/PasarGuard/subscription-template/refs/heads/main/screenshots/fa.png" alt="Persian UI" width="30%">
</p>

## Возможности

- Языки: `en`, `fa`, `zh`, `ru`
- Пользователь может менять язык в интерфейсе
- Адаптивная верстка
- Темный режим
- QR-код для ссылок подключения
- Копирование ссылок и конфигов в один клик, а Base64 доступен только в QR-модальном окне
- Ссылки WireGuard можно копировать как нативный конфиг и скачивать в формате `.conf`
- У OpenVPN отдельная строка конфига (скачать `.ovpn` или скопировать) вместо обычной ссылки
- Ссылки MTProto (Telegram-прокси, `tg://`) получают свою строку с реальным именем вместо общего запасного варианта
- [Настройка внешнего вида](#appearance-customization)

## Совместимость

| Версия шаблона подписки | Версия панели |
| --- | --- |
| `v2` | `v3` (этот форк) |
| Остальные версии | `v2`, `v1` |

## Быстрый старт (рекомендуется)

Запустите скрипт установки (выберите язык по умолчанию):

```sh
curl -fsSL https://raw.githubusercontent.com/Free-Guy-IR/subscription-template/main/install.sh | sudo bash -s -- --lang ru
```

Поддерживаемые значения `--lang`: `en`, `fa`, `zh`, `ru`
Поддерживаемые значения `--version`: `latest` (по умолчанию) или тег релиза, например `v2.0.0`
Чтобы установить конкретный релиз, добавьте `--version <tag>`.

## Установка вручную

1. Скачайте шаблон:

```sh
sudo mkdir -p /var/lib/pasarguard/templates/subscription
sudo wget -O /var/lib/pasarguard/templates/subscription/index.html \
https://github.com/Free-Guy-IR/subscription-template/releases/latest/download/ru.html
```

2. Настройте PasarGuard в `/opt/pasarguard/.env`:

```dotenv
CUSTOM_TEMPLATES_DIRECTORY="/var/lib/pasarguard/templates/"
SUBSCRIPTION_PAGE_TEMPLATE="subscription/index.html"
```

3. Перезапустите:

```sh
pasarguard restart
```

## Сборка Из Исходников

```sh
git clone https://github.com/Free-Guy-IR/subscription-template.git
cd subscription-template
bun install
bun run build
```

Используйте собранный файл:

```sh
sudo cp dist/index.html /var/lib/pasarguard/templates/subscription/index.html
```

<a id="appearance-customization"></a>

## Настройка Внешнего Вида

Укажите это в `.env` и соберите заново:

```dotenv
VITE_PRIMARY_COLOR_LIGHT=oklch(0.48 0.11 250)
VITE_PRIMARY_COLOR_DARK=oklch(0.60 0.12 250)
VITE_BORDER_RADIUS=0.65rem
```

## Другие языки

- [English](README.md)
- [فارسی (Persian)](README.fa.md)
- [中文 (Chinese)](README.zh.md)

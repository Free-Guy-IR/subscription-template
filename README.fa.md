# قالب اشتراک PasarGuard

قالب صفحه اشتراک واکنش‌گرا برای PasarGuard.

> **توجه:** این فورک [Free-Guy-IR](https://github.com/Free-Guy-IR) از [قالب اشتراک اصلی PasarGuard](https://github.com/PasarGuard/subscription-template) است که برای پشتیبانی از هسته‌های اضافه‌ی این فورک گسترش داده شده: یک ردیف **کانفیگ OpenVPN** (دانلود + کپی، مشابه نمایش WireGuard) و یک ردیف **MTProto (پروکسی تلگرام)** (لینک‌های `tg://`، فقط کپی - بدون QR، چون این لینک‌ها قرار نیست اسکن بشن).

<p align="center">
  <img src="https://raw.githubusercontent.com/PasarGuard/subscription-template/refs/heads/main/screenshots/en.png" alt="English UI" width="40%">
  <img src="https://raw.githubusercontent.com/PasarGuard/subscription-template/refs/heads/main/screenshots/fa.png" alt="Persian UI" width="30%">
</p>

## امکانات

- زبان‌ها: `en`، `fa`، `zh`، `ru`
- امکان تغییر زبان توسط کاربر
- طراحی واکنش‌گرا
- حالت تاریک
- QR برای لینک‌های اتصال
- کپی لینک و کانفیگ با یک کلیک، با امکان کپی Base64 فقط در مودال QR
- لینک‌های WireGuard به صورت کانفیگ اصلی هم قابل کپی و دانلود با فرمت `.conf` هستند
- OpenVPN یک ردیف کانفیگ اختصاصی داره (دانلود فایل `.ovpn` یا کپی) به‌جای یه لینک عمومی
- لینک‌های MTProto (پروکسی تلگرام، `tg://`) ردیف اختصاصی خودشون رو با اسم واقعی دارن، نه یه نام پیش‌فرض عمومی
- [شخصی‌سازی ظاهر](#appearance-customization)

## سازگاری

| نسخه قالب اشتراک | نسخه پنل |
| --- | --- |
| `v2` | `v3` (این فورک) |
| سایر نسخه‌ها | `v2`، `v1` |

## نصب سریع (پیشنهادی)

اجرای اسکریپت نصب (با انتخاب زبان پیش‌فرض):

```sh
curl -fsSL https://raw.githubusercontent.com/Free-Guy-IR/subscription-template/main/install.sh | sudo bash -s -- --lang fa
```

مقادیر معتبر `--lang`: `en`، `fa`، `zh`، `ru`
مقادیر معتبر `--version`: `latest` (پیش‌فرض) یا یک تگ انتشار مثل `v2.0.0`
برای نصب یک نسخه مشخص، `--version <tag>` را اضافه کنید.

## نصب دستی

1. دانلود قالب:

```sh
sudo mkdir -p /var/lib/pasarguard/templates/subscription
sudo wget -O /var/lib/pasarguard/templates/subscription/index.html \
https://github.com/Free-Guy-IR/subscription-template/releases/latest/download/index.html
```

2. تنظیم PasarGuard در فایل `/opt/pasarguard/.env`:

```dotenv
CUSTOM_TEMPLATES_DIRECTORY="/var/lib/pasarguard/templates/"
SUBSCRIPTION_PAGE_TEMPLATE="subscription/index.html"
```

3. راه‌اندازی مجدد:

```sh
pasarguard restart
```

## ساخت از سورس

```sh
git clone https://github.com/Free-Guy-IR/subscription-template.git
cd subscription-template
bun install
bun run build
```

استفاده از فایل ساخته‌شده:

```sh
sudo cp dist/index.html /var/lib/pasarguard/templates/subscription/index.html
```

<a id="appearance-customization"></a>

## شخصی‌سازی ظاهر

این مقادیر را در `.env` تنظیم کنید و دوباره build بگیرید:

```dotenv
VITE_PRIMARY_COLOR_LIGHT=oklch(0.48 0.11 250)
VITE_PRIMARY_COLOR_DARK=oklch(0.60 0.12 250)
VITE_BORDER_RADIUS=0.65rem
```

## زبان‌های دیگر

- [English](README.md)
- [Русский (Russian)](README.ru.md)
- [中文 (Chinese)](README.zh.md)

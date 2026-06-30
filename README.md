# Routing VPN Iran

**VPN روشن، سایت‌ها و بانک‌های ایرانی بدون دردسر.**

این repo یک لیست آماده برای V2Box و V2Box Pro دارد تا سایت‌ها، بانک‌ها، درگاه‌های پرداخت و سرویس‌های مهم ایرانی به جای Proxy از مسیر `direct` باز شوند. نتیجه این است که لازم نیست برای ورود به بانک، پرداخت، دیجی‌کالا، آپارات، اسنپ و سرویس‌های مشابه مدام VPN را خاموش و روشن کنید.

> English guide is below.

## فایل‌های آماده

- [`rules/iran-direct-v2box.txt`](rules/iran-direct-v2box.txt): نسخه آماده copy/paste برای V2Box و V2Box Pro
- [`rules/iran-direct-readable.txt`](rules/iran-direct-readable.txt): همان Ruleها به صورت دسته‌بندی‌شده و قابل خواندن

## آموزش اضافه کردن در V2Box Pro

1. V2Box Pro را باز کنید.
2. وارد بخش **Routing** شوید.
3. روی **Add Rule** بزنید.
4. در بخش **Remarks** بنویسید:

```text
Iran Direct
```

5. مقدار **Outbound Tag** را روی این گزینه بگذارید:

```text
direct
```

6. محتوای فایل [`rules/iran-direct-v2box.txt`](rules/iran-direct-v2box.txt) را کامل کپی کنید.
7. آن را در بخش **Domain (comma separated)** قرار دهید.
8. روی **Save** بزنید.
9. اگر VPN روشن است، یک بار خاموش و دوباره روشنش کنید.

## ترتیب Ruleها

ترتیب Ruleها مهم است. Rule مربوط به ایران باید قبل از Rule عمومی Proxy پردازش شود.

پیشنهاد:

```text
1. Iran Direct  -> direct
2. Other rules  -> proxy / block / ...
```

اگر یک سایت خارجی مثل LinkedIn، YouTube، GitHub یا Google بعد از اضافه کردن این Rule مشکل پیدا کرد، آن سایت را داخل Rule ایران نگذارید. این لیست فقط برای سرویس‌هایی است که باید مستقیم و بدون Proxy باز شوند.

## نکته مهم درباره geosite

در بعضی نسخه‌های V2Box Pro، استفاده از این Rule باعث خطای `geosite.dat` می‌شود:

```text
geosite:ir
```

برای همین در این repo از `geosite:ir` استفاده نشده و به جای آن از این Rule عمومی استفاده شده است:

```text
regexp:.*\.ir$
```

## چه چیزهایی پوشش داده شده؟

- سایت‌های `.ir`
- بانک‌های مهم ایرانی
- درگاه‌های پرداخت و شاپرک
- فروشگاه‌ها و مارکت‌پلیس‌ها
- ویدیو، ورزش و رسانه
- تاکسی، غذا، سفر و پست
- اپراتورها و سرویس‌های اینترنت
- چند وب‌اپ بانکی و وابستگی‌های ضروری آن‌ها

## مشارکت

اگر دامنه‌ای جا افتاده یا یک سرویس ایرانی با VPN روشن درست کار نمی‌کند، یک Issue یا Pull Request باز کنید و این اطلاعات را بنویسید:

- نام سرویس
- آدرس سایت یا وب‌اپ
- خطا یا رفتار مشکل‌دار
- دامنه‌هایی که فکر می‌کنید باید اضافه شوند

---

# Routing VPN Iran

**Keep your VPN on while Iranian websites and banking services stay reachable.**

This repository provides copy-ready routing rules for V2Box and V2Box Pro. The rules send major Iranian websites, banking apps, payment gateways, marketplaces, media services, operators, and local services through `direct` instead of `proxy`.

The practical goal is simple: avoid turning your VPN off and on every time you need to use an Iranian bank, payment gateway, marketplace, or local service.

## Files

- [`rules/iran-direct-v2box.txt`](rules/iran-direct-v2box.txt): copy-ready V2Box / V2Box Pro rule
- [`rules/iran-direct-readable.txt`](rules/iran-direct-readable.txt): categorized readable version

## How to add the rule in V2Box Pro

1. Open V2Box Pro.
2. Go to **Routing**.
3. Click **Add Rule**.
4. Set **Remarks** to:

```text
Iran Direct
```

5. Set **Outbound Tag** to:

```text
direct
```

6. Copy the full content of [`rules/iran-direct-v2box.txt`](rules/iran-direct-v2box.txt).
7. Paste it into **Domain (comma separated)**.
8. Click **Save**.
9. Restart the VPN connection once.

## Rule order

Rule order matters. The Iran direct rule should be evaluated before broad proxy rules.

Recommended order:

```text
1. Iran Direct  -> direct
2. Other rules  -> proxy / block / ...
```

Do not add foreign services such as LinkedIn, YouTube, GitHub, or Google to the Iran direct rule. Those services should usually continue using your proxy route.

## Why there is no geosite:ir

Some V2Box Pro setups fail with `geosite.dat` errors when this rule is used:

```text
geosite:ir
```

This repository avoids `geosite:ir` and uses this safer rule instead:

```text
regexp:.*\.ir$
```

## Covered categories

- `.ir` domains
- Iranian banks
- Payment gateways and Shaparak-related domains
- Marketplaces and shopping services
- Video, sport, and media services
- Taxi, food, travel, and postal services
- Mobile operators and ISPs
- Selected banking web apps and required dependencies

## Contributing

If a domain is missing or an Iranian service still fails while VPN is on, open an Issue or Pull Request with:

- Service name
- Website or web app URL
- The error or broken behavior
- Suggested domains to add

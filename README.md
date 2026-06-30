# Routing VPN Iran

Keep your VPN on while Iranian websites, banks, and payment gateways use a direct route.

[![Persian Guide](https://img.shields.io/badge/Persian_Guide-%D8%A2%D9%85%D9%88%D8%B2%D8%B4_%D9%81%D8%A7%D8%B1%D8%B3%DB%8C-1f7a8c?style=for-the-badge)](docs/fa.md)
[![English Guide](https://img.shields.io/badge/English_Guide-Open-2563eb?style=for-the-badge)](docs/en.md)
[![Copy Rule](https://img.shields.io/badge/Copy_V2Box_Rule-Direct_Routing-f97316?style=for-the-badge)](rules/iran-direct-v2box.txt)

## Why

Many users in Iran have to turn their VPN off for local websites, banking apps, payment gateways, marketplaces, and streaming services. This repository provides copy-ready routing rules for **V2Box** and **V2Box Pro** so Iranian services can use `direct` while the rest of your traffic can keep using `proxy`.

## Quick Start

1. Open **V2Box** or **V2Box Pro**.
2. Go to **Routing**.
3. Add a new rule named `Iran Direct`.
4. Set **Outbound Tag** to `direct`.
5. Paste the content of [`rules/iran-direct-v2box.txt`](rules/iran-direct-v2box.txt) into **Domain (comma separated)**.
6. Save the rule and restart the VPN connection once.

For the full walkthrough, use:

- [آموزش فارسی](docs/fa.md)
- [English Guide](docs/en.md)

## Files

- [`rules/iran-direct-v2box.txt`](rules/iran-direct-v2box.txt): copy-ready one-line rule for V2Box / V2Box Pro
- [`rules/iran-direct-readable.txt`](rules/iran-direct-readable.txt): readable categorized version of the same domains

## Rule Order

Put the Iran direct rule before broad proxy rules:

```text
1. Iran Direct  -> direct
2. Other rules  -> proxy / block / ...
```

Do not add unrelated foreign services to the Iran direct rule. Those services should usually continue using your proxy route.

## No geosite:ir

Some V2Box Pro setups fail with `geosite.dat` errors when `geosite:ir` is used. This repository avoids `geosite:ir` and uses this safer rule instead:

```text
regexp:.*\.ir$
```

## Covered Categories

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

## License

MIT

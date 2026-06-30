# English Guide

[Back to README](../README.md)

This rule lets you keep your VPN on while Iranian websites, banks, payment gateways, and local services use a `direct` route.

## Copy-Ready Rule

Use this file:

[`rules/iran-direct-v2box.txt`](../rules/iran-direct-v2box.txt)

## Add the Rule in V2Box or V2Box Pro

1. Open **V2Box** or **V2Box Pro**.
2. Select the V2Ray / VLESS / VMess config that you already use.
3. Go to **Routing**.
4. Click **Add Rule**.
5. Set **Remarks** to:

```text
Iran Direct
```

6. Set **Outbound Tag** to:

```text
direct
```

7. Copy the full content of [`rules/iran-direct-v2box.txt`](../rules/iran-direct-v2box.txt).
8. Paste it into **Domain (comma separated)**.
9. Click **Save**.
10. Turn the VPN off and on once.

## Rule Order

Rule order matters. Put the Iran direct rule before broad proxy rules:

```text
1. Iran Direct  -> direct
2. Other rules  -> proxy / block / ...
```

## If a Foreign Website Breaks

Do not add unrelated foreign services to the Iran direct rule. Those services should usually continue using your proxy route.

## Why There Is No geosite:ir

Some V2Box Pro setups fail with `geosite.dat` errors when this rule is used:

```text
geosite:ir
```

This repository avoids `geosite:ir` and uses this safer rule instead:

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

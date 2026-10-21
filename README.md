# conf — ECH-tuned Cloudflare v2ray configs

Daily clone of 4 public subscription sources, keeping only
Cloudflare-fronted entries and rewriting them for ECH.

- **Import (base64)**: <https://raw.githubusercontent.com/Phnx28/conf/main/sub.txt>
- **Readable list**: [`configs-ech.txt`](configs-ech.txt)
- **Report**: [`report.json`](report.json) · **sources**: [`sources.json`](sources.json)

## Method

| field | value |
|---|---|
| address | Cloudflare anycast IP (pool rotation) |
| `fp` | `chrome` |
| `ech` | `cloudflare-ech.com+udp://1.1.1.1` |
| `cs` / `fm` | removed (cipherSuites / finalMask cleared) |
| `alpn` | `http/1.1` (ws/h2/http), `h2,http/1.1` (grpc) |

Preserved per entry: uuid/password, port, path, host, sni, transport.
REALITY entries are never ECH-able and are skipped.

## Sources

| # | type | links | url |
|---|---|---|---|
| 1 | `raw` | 5134 | https://raw.githubusercontent.com/Delta-Kronecker/V2ray-Config/main/config/all_configs.txt |
| 2 | `raw` | 1129 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs.txt |
| 3 | `b64` | 1625 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/verified/configs_base64.txt |
| 4 | `b64` | 1129 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs_base64.txt |

Total 9017 links, 6153 unique.

## Last run

| metric | value |
|---|---|
| date | 2026-10-21 |
| scanned | 6151 |
| Cloudflare-fronted selected | 649 |
| emitted | 635 |

Dropped after selection: no hostname for sni × 13, duplicate link × 1 (649 − 14 = 635).
Not Cloudflare: 3467 parsed + 1995 unparsable.

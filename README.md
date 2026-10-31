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
| 1 | `raw` | 4294 | https://raw.githubusercontent.com/Delta-Kronecker/V2ray-Config/main/config/all_configs.txt |
| 2 | `raw` | 1247 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs.txt |
| 3 | `b64` | 1730 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/verified/configs_base64.txt |
| 4 | `b64` | 1247 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs_base64.txt |

Total 8518 links, 5420 unique (2 of which are upstream `#` comment lines).

## Last run

| metric | value |
|---|---|
| date | 2026-10-31 |
| scanned | 5418 |
| Cloudflare-fronted selected | 420 |
| emitted | 452 |

Composition: 210 vless + 172 trojan + 70 vmess — all 452 distinct.

Full accounting: 5418 scanned = 4928 skipped before selection
(2934 not-CF parsed + 1992 not-CF/unparsable,
the latter including upstream-corrupted credentials and malformed-vmess groups
+ 2 malformed vmess query links) +
420 query-shaped selected + 70 vmess rewritten = 490 rewritten,
of which 13 dropped after selection for no recoverable hostname and 25 removed
as identical duplicate lines → 382 query lines + 70 vmess = 452 emitted.

### Known limitations

- ECH is TLS-only. 51 entries are plaintext on Cloudflare ports 80/8080
  (`security=none`/absent, or vmess `tls: none`) — 40 vless/trojan + 11 vmess.
  They are routed and importable, but the ECH parameter is inert for them. The
  remaining 401 entries are TLS and ECH-active.
- Cloudflare ranges came from `cloudflare.com/ips-v4` (14 ranges, rc 0) this run;
  the GitHub mirror is only a fallback when that host is SNI-blocked.

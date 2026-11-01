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
| 1 | `raw` | 4399 | https://raw.githubusercontent.com/Delta-Kronecker/V2ray-Config/main/config/all_configs.txt |
| 2 | `raw` | 1247 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs.txt |
| 3 | `b64` | 1841 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/verified/configs_base64.txt |
| 4 | `b64` | 1247 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs_base64.txt |

Total 8734 links, 5660 unique (2 of which are upstream `#` comment lines).

## Last run

| metric | value |
|---|---|
| date | 2026-11-01 |
| scanned | 5658 |
| Cloudflare-fronted selected | 575 |
| emitted | 578 |

Composition: 232 vless + 251 trojan + 95 vmess — all 578 distinct.

Full accounting: 5658 scanned = 4988 skipped before selection
(3004 not-CF parsed + 1981 not-CF/unparsable,
the latter including upstream-corrupted credentials and malformed-vmess groups
+ 3 malformed vmess query links) +
575 query-shaped selected + 95 vmess rewritten = 670 rewritten,
of which 25 dropped after selection for no recoverable hostname and 67 removed
as identical duplicate lines → 483 query lines + 95 vmess = 578 emitted.

### Known limitations

- ECH is TLS-only. 44 entries are plaintext on Cloudflare ports 80/8080
  (`security=none`/absent, or vmess `tls: none`) — 32 vless + 12 vmess.
  They are routed and importable, but the ECH parameter is inert for them. The
  remaining 534 entries are TLS and ECH-active.
- Cloudflare ranges came from `cloudflare.com/ips-v4` (14 ranges, rc 0) this run;
  the GitHub mirror is only a fallback when that host is SNI-blocked.

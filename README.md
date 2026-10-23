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
| 1 | `raw` | 5249 | https://raw.githubusercontent.com/Delta-Kronecker/V2ray-Config/main/config/all_configs.txt |
| 2 | `raw` | 1221 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs.txt |
| 3 | `b64` | 1663 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/verified/configs_base64.txt |
| 4 | `b64` | 1221 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs_base64.txt |

Total 9354 links, 6300 unique.

## Last run

| metric | value |
|---|---|
| date | 2026-10-23 |
| scanned | 6298 |
| Cloudflare-fronted selected | 585 |
| emitted | 592 |

Composition: 448 vless + 106 trojan + 38 vmess.

Full accounting: 6298 scanned = 5675 skipped before selection (3644 not-CF
parsed + 2031 not-CF/unparsable, the latter including upstream-corrupted
credentials and malformed-vmess groups) + 585 query-shaped selected + 38 vmess
rewritten = 623 rewritten, of which 10 dropped after selection for no
recoverable SNI and 21 removed as identical duplicate lines = 592 emitted, all
distinct.

### Known limitations

- ECH is TLS-only. 90 entries are plaintext on Cloudflare ports 80/8080
  (`security=none`/absent, or vmess `tls: none`) — 81 vless + 9 vmess. They are
  routed and importable, but the ECH parameter is inert for them. The remaining
  502 entries are TLS and ECH-active.
- Cloudflare ranges came from `cloudflare.com/ips-v4` (14 ranges, rc 0) this run;
  the GitHub mirror is only a fallback when that host is SNI-blocked.

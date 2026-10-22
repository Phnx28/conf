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
| 1 | `raw` | 5708 | https://raw.githubusercontent.com/Delta-Kronecker/V2ray-Config/main/config/all_configs.txt |
| 2 | `raw` | 1413 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs.txt |
| 3 | `b64` | 1888 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/verified/configs_base64.txt |
| 4 | `b64` | 1413 | https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs_base64.txt |

Total 10422 links, 6993 unique.

## Last run

| metric | value |
|---|---|
| date | 2026-10-22 |
| scanned | 6991 |
| Cloudflare-fronted selected | 733 |
| emitted | 728 |

Full accounting: 6991 scanned = 6215 skipped before selection (4117 not-CF
parsed + 2098 not-CF/unparsable, the latter now including upstream-corrupted
credentials and malformed-vmess groups) + 11 dropped after selection for no
recoverable SNI + 765 rewritten (722 query-shaped + 43 vmess) − 37 identical
duplicate lines = 728 emitted, all distinct.

### Known limitations

- ECH is TLS-only. 9 vmess entries (port 80, `tls: none`) and 66 vless entries
  with `security=none`/absent (Cloudflare port 80/8080 plaintext WebSocket) ship
  and route, but the ECH parameter is inert for them.
- Cloudflare ranges came from `cloudflare.com/ips-v4` (14 ranges, rc 200) this run;
  the GitHub mirror is only a fallback when that host is SNI-blocked.

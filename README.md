# CF ECH subscription — 2026-10-15

ECH-tuned Cloudflare-fronted v2ray configs, rebuilt daily.
Import `sub.txt` (base64 link list) into your client.

## Sources
- [raw] https://raw.githubusercontent.com/Delta-Kronecker/V2ray-Config/main/config/all_configs.txt — 6343 links
- [raw] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs.txt — 920 links
- [b64] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/verified/configs_base64.txt — 1265 links
- [b64] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs_base64.txt — 920 links
- total fetched: 9448, unique: 6987

## Rewrite
- scanned: 6985
- selected (CF-fronted): 522
- emitted (ECH variants): 509
- schemes: vless 317, trojan 166, vmess 26
- CF hostnames learned: 79
- skipped: not CF 4556, not CF / unparsable 1876, no hostname for sni 16, malformed vmess query link 5

## Files
- `sub.txt` — base64 subscription (import this)
- `configs-ech.txt` — readable link list
- `report.json`, `sources.json` — build metadata

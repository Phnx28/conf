# CF ECH subscription — 2026-10-18

ECH-tuned Cloudflare-fronted v2ray configs, rebuilt daily.
Import `sub.txt` (base64 link list) into your client.

## Sources
- [raw] https://raw.githubusercontent.com/Delta-Kronecker/V2ray-Config/main/config/all_configs.txt — 6588 links
- [raw] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs.txt — 1374 links
- [b64] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/verified/configs_base64.txt — 1836 links
- [b64] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs_base64.txt — 1374 links
- total fetched: 11172, unique: 7800

## Rewrite
- scanned: 7798
- selected (CF-fronted): 642
- emitted (ECH variants): 648
- schemes: vless 453, trojan 149, vmess 46
- CF hostnames learned: 69
- skipped: not CF 5078, not CF / unparsable 2025, no hostname for sni 12, malformed vmess query link 7

## Files
- `sub.txt` — base64 subscription (import this)
- `configs-ech.txt` — readable link list
- `report.json`, `sources.json` — build metadata

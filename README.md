# CF ECH subscription — 2026-10-11

ECH-tuned Cloudflare-fronted v2ray configs, rebuilt daily.
Import `sub.txt` (base64 link list) into your client.

## Sources
- [raw] https://raw.githubusercontent.com/Delta-Kronecker/V2ray-Config/main/config/all_configs.txt — 6472 links
- [raw] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs.txt — 1071 links
- [b64] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/verified/configs_base64.txt — 1498 links
- [b64] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs_base64.txt — 1071 links
- total fetched: 10112, unique: 7354

## Rewrite
- scanned: 7352
- selected (CF-fronted): 896
- emitted (ECH variants): 735
- schemes: vless 569, trojan 166
- CF hostnames learned: 184
- skipped: not CF 4603, not CF / unparsable 1846, malformed vmess query link 7, no hostname for sni 126

## Files
- `sub.txt` — base64 subscription (import this)
- `configs-ech.txt` — readable link list
- `report.json`, `sources.json` — build metadata

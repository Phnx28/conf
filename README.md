# CF ECH subscription — 2026-10-20

ECH-tuned Cloudflare-fronted v2ray configs, rebuilt daily.
Import `sub.txt` (base64 link list) into your client.

## Sources
- [raw] https://raw.githubusercontent.com/Delta-Kronecker/V2ray-Config/main/config/all_configs.txt — 4891 links
- [raw] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs.txt — 1030 links
- [b64] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/verified/configs_base64.txt — 1473 links
- [b64] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs_base64.txt — 1030 links
- total fetched: 8424, unique: 5768

## Rewrite
- scanned: 5766
- selected (CF-fronted): 519
- emitted (ECH variants): 525
- schemes: vless 338, trojan 149, vmess 38
- CF hostnames learned: 66
- skipped: not CF 3187, not CF / unparsable 2015, no hostname for sni 13, malformed vmess query link 7

## Files
- `sub.txt` — base64 subscription (import this)
- `configs-ech.txt` — readable link list
- `report.json`, `sources.json` — build metadata

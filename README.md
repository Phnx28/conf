# CF ECH subscription — 2026-10-16

ECH-tuned Cloudflare-fronted v2ray configs, rebuilt daily.
Import `sub.txt` (base64 link list) into your client.

## Sources
- [raw] https://raw.githubusercontent.com/Delta-Kronecker/V2ray-Config/main/config/all_configs.txt — 6717 links
- [raw] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs.txt — 1336 links
- [b64] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/verified/configs_base64.txt — 1717 links
- [b64] https://raw.githubusercontent.com/0xRadikal/Free-v2ray-Configs/main/secure/configs_base64.txt — 1336 links
- total fetched: 11106, unique: 7804

## Rewrite
- scanned: 7802
- selected (CF-fronted): 644
- emitted (ECH variants): 639
- schemes: vless 425, trojan 181, vmess 33
- CF hostnames learned: 81
- skipped: not CF 5139, not CF / unparsable 1981, no hostname for sni 16, malformed vmess query link 5

## Files
- `sub.txt` — base64 subscription (import this)
- `configs-ech.txt` — readable link list
- `report.json`, `sources.json` — build metadata

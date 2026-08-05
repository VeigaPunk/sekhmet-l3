# chatgpt.site paste pack — sekhmet-l3

Target: https://sekhmet-l3.jpveiga.chatgpt.site/

## Hero blurb

**Sekhmet L3** — always-on swarm substrate for xbgst / xbrd-sol-ultra.  
Up to **64** concurrent namespaced Codex Titanium sparks. No worktrees. Distill above.

## Default command

```bash
. ~/.xbgst/env.l3-sekhmet.sh
ROOT=$(mktemp -d)
XBRD_SPARK_MODEL=gpt-5.6-luna \
XBRD_SPARK_FALLBACK_MODEL=none \
XBRD_SPARK_SERVICE_TIER=fast \
sekhmet swarm --direct -j 64 --ro --timeout 180 --no-keep \
  --tasks-file tasks.txt --root "$ROOT"
```

## Verified pin

- spark_id: `sp-e6354307-422f-4e97-8dc3-08aa138ce9f3`
- model: `gpt-5.6-luna` · service_tier **fast** · status **ok** (3055 ms)

## Links

- https://github.com/VeigaPunk/sekhmet-l3
- https://github.com/VeigaPunk/xbrd-spark
- https://github.com/VeigaPunk/ds4cc-marketplace
- https://github.com/VeigaPunk/xbrd-sol-ultra

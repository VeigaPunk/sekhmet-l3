# USAGE — sekhmet L3 under xbgst / sol-ultra

PATH `xask` is protocol xbreed (`xbreed ask`); the thin sekhmet shim is installed as `xask-l3`. Preflight with `command -v sekhmet xask-l3 codex-titanium` — do not treat PATH `xask` as the L3 shim.

## Preflight

```bash
. ~/.xbgst/env.l3-sekhmet.sh
command -v sekhmet xask-l3 codex-titanium
sekhmet --version   # expect 0.1.1+
echo "$XBRD_SPARK_JOBS $XBRD_SPARK_SERVICE_TIER $XBRD_SPARK_MODEL"   # 64 fast gpt-5.6-luna (host L3 fanout)
# resolve: CODEX_BIN → codex-titanium → skip omarchy npx codex stub; never symlink titanium→codex
# xask-l3 = thin sekhmet run shim (Titanium default; clap has --no-direct only); PATH xask is protocol xbreed ask
codex-titanium login status   # ChatGPT OAuth (live blocked if Not logged in)
```

## L2 pulse (offline gate)

```bash
# from an xbrd-spark checkout
scripts/l2-pulse.sh --dry-run
```

This runs one dry spark and never fans out.

## Dry swarm (offline gate)

```bash
. ~/.xbgst/env.l3-sekhmet.sh
seq 1 64 | sed 's/^/dry-task-/' > /tmp/tasks64.txt
ROOT=$(mktemp -d)
sekhmet swarm --dry-run -j 64 -f /tmp/tasks64.txt --root "$ROOT" --no-keep
```

A 64-wide dry or live campaign is coordinator-owned and is not an L2 pulse.

## Live luna + fast (required pin)

Do **not** use a `-fast` model id. OAuth wants:

- model: `gpt-5.6-luna`
- `service_tier=fast` via env `XBRD_SPARK_SERVICE_TIER=fast`
- reasoning low (sekhmet default for titanium exec)

```bash
export XBRD_SPARK_MODEL=gpt-5.6-luna
export XBRD_SPARK_FALLBACK_MODEL=none
export XBRD_SPARK_SERVICE_TIER=fast
ROOT=$(mktemp -d)
sekhmet run --ro --timeout 90 --no-keep \
  --task 'Reply with exactly: SEKHMET_LUNA_FAST_OK' --root "$ROOT"
```

Coordinator-owned sol-ultra / xbgst campaigns may specify a wider wave.
An L2 pulse must not start `sekhmet swarm -j 64` without an explicit coordinator
request. Never nest swarms.

## Marketplace

```bash
codex plugin marketplace add VeigaPunk/ds4cc-marketplace
codex plugin add sekhmet@ds4cc --json
```

## Collect / status / gc

```bash
sekhmet status <spark-id> --root "$ROOT"
sekhmet collect <spark-id> --root "$ROOT"
sekhmet gc --max-age 0 --root "$ROOT"
```

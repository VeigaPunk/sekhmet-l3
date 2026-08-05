# USAGE — sekhmet L3 under xbgst / sol-ultra

## Preflight

```bash
. ~/.xbgst/env.l3-sekhmet.sh
command -v sekhmet xbgst-l3-orch tmux-orch codex-titanium
sekhmet --version
echo "$XBRD_SPARK_JOBS $XBRD_SPARK_SERVICE_TIER"   # expect: 64 fast
tmux has-session -t sekhmet || tmux-orch ensure
codex-titanium login status   # ChatGPT OAuth
```

## Dry swarm (offline gate)

```bash
. ~/.xbgst/env.l3-sekhmet.sh
seq 1 64 | sed 's/^/dry-task-/' > /tmp/tasks64.txt
ROOT=$(mktemp -d)
sekhmet swarm --dry-run -j 64 -f /tmp/tasks64.txt --root "$ROOT" --no-keep
```

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
sekhmet run --direct --ro --timeout 90 --no-keep \
  --task 'Reply with exactly: SEKHMET_LUNA_FAST_OK' --root "$ROOT"
```

Sol-ultra / xbgst wave shape: **exactly one** `sekhmet swarm --direct -j 64` per round.
Never nest swarms. Never silently lower `-j 64` for the sol-ultra contract.

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

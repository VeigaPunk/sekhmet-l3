# sekhmet-l3

**Public face of the xbreed / xbgst layer-3 swarm substrate** ([Sekhmet](https://github.com/VeigaPunk/xbrd-spark) / `xbrd-spark`).

Durable usage + evidence pack for operators and for paste into
[sekhmet-l3.jpveiga.chatgpt.site](https://sekhmet-l3.jpveiga.chatgpt.site/) (ChatGPT sign-in gated from unauthenticated curl).

## What it is

| Layer | Role |
| --- | --- |
| L1 | xbgst / xbrd-sol-ultra judge (Pareto, ship) |
| L2-select | xbrd-selector (optional model/agent catalog; ds4cc; may be absent) |
| L2-loop | prime-agent (optional; persistent REPL + /refine; user-level binary; xbgst-stack adapter) |
| **L3 / Sekhmet** | **namespaced sparks, no worktrees, up to 64 concurrent** |

Binaries (Rust only): `sekhmet`, `xbrd-spark`, `xbgst-l3-orch`  
Install: `cargo install --git https://github.com/VeigaPunk/xbrd-spark --locked`

## Host always-on

```bash
. ~/.xbgst/env.l3-sekhmet.sh
# XBRD_SPARK_JOBS=64
# XBRD_SPARK_SERVICE_TIER=fast
# XBRD_SPARK_MODEL=gpt-5.3-codex-spark
# XBRD_SPARK_FALLBACK_MODEL=gpt-5.6-luna
```

This file is the **substrate default**: 64 concurrent L3 sparks. Do not drop it
to 1. An L2 *pulse* may pin `XBRD_SPARK_JOBS=1` **inside the pulse wrapper only**.

## Repeating bounded L2 pulse

Run one pulse on each 10-minute lane heartbeat:

```bash
# from an xbrd-spark checkout
scripts/l2-pulse.sh
```

The wrapper sources `~/.xbgst/env.l3-sekhmet.sh`, forces
`XBRD_SPARK_JOBS=1`, and invokes `sekhmet run --ro --timeout 90`. It keeps the
namespace under `~/.xbgst/evidence/sekhmet-l3-pulses` for inspection. If OAuth
preflight is blocked, it emits one clearly labeled `--dry-run` pulse instead.
Pass `--dry-run` to request the offline path directly.

Each heartbeat stops after that one terminal result. Copy its Route ID, spark
ID, status, exit code, and artifact path into
[`evidence/L3-PULSE.md`](evidence/L3-PULSE.md). Use the request and receipt
shape in [`evidence/HANDOFF.md`](evidence/HANDOFF.md).

## Coordinator-only wide campaign

Host env stays `XBRD_SPARK_JOBS=64`. An L2 pulse must **never** rewrite that
file or start `sekhmet swarm -j 64` on its own. A coordinator must explicitly
own any wide campaign:

```bash
. ~/.xbgst/env.l3-sekhmet.sh
ROOT=$(mktemp -d)
XBRD_SPARK_MODEL=gpt-5.3-codex-spark \
XBRD_SPARK_FALLBACK_MODEL=gpt-5.6-luna \
XBRD_SPARK_SERVICE_TIER=fast \
sekhmet swarm --direct -j 64 --ro --timeout 180 --no-keep \
  --tasks-file tasks.txt --root "$ROOT"
```

Manual one-spark pulse (does not change the host env file):

```bash
. ~/.xbgst/env.l3-sekhmet.sh
export XBRD_SPARK_JOBS=1
ROOT="$HOME/.xbgst/evidence/sekhmet-l3-pulses"
sekhmet run --ro --timeout 90 \
  --task 'Reply with exactly: SEKHMET_L3_PULSE_OK | godspeed' --root "$ROOT"
```

## Proven live oneshot (prior host, 2026-08-05)

Historical (vgpnk1337). plazir27 2026-08-20: PATH + dry j=64 GATE_OK; live blocked until ChatGPT OAuth.

| Field | Value |
| --- | --- |
| status | `ok` |
| model | `gpt-5.6-luna` |
| duration_ms | `3055` |
| spark_id | `sp-e6354307-422f-4e97-8dc3-08aa138ce9f3` |
| exit_code | `0` |
| cmdline | `codex-titanium exec -m gpt-5.6-luna -c model_reasoning_effort=low -c service_tier=fast --ephemeral --skip-git-repo-check --color never --sandbox read-only -c approval_policy=never Reply with exactly: SEKHMET_LUNA_FAST_OK` |

See [USAGE.md](USAGE.md), [EVIDENCE.md](EVIDENCE.md), [chatgpt-site-paste.md](chatgpt-site-paste.md).

## Related

- Substrate: https://github.com/VeigaPunk/xbrd-spark
- Marketplace plugin: https://github.com/VeigaPunk/ds4cc-marketplace (`sekhmet`)
- Sol Ultra judge skill: https://github.com/VeigaPunk/xbrd-sol-ultra
- xbgst hub: https://veigapunk.github.io/xbgst-site/

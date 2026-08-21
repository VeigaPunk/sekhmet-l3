# STATUS — GATE_OK

## L2 bounded-pulse refresh 2026-08-21 (host vgpnk@plazir27)

| Check | Result |
| --- | --- |
| host L3 env | `XBRD_SPARK_JOBS=64` · model `gpt-5.6-luna` · tier `fast` · fallback `none` |
| L2 pulse override | `l2-pulse.sh` pins `JOBS=1` per call only; does not rewrite the host env |
| binaries | `sekhmet` / `xbrd-spark` **0.1.1** · `codex-titanium` **0.146.0-alpha.10.1+titanium.1** |
| OAuth | **Logged in using ChatGPT** |
| live pulse | **ok**, exit `0`, 6156ms, read-only, timeout `90s` |
| route / spark | `L2-L3-20260821T170654Z` / `sp-pulse-20260821T170654Z` |
| recurring lane | active 10-minute heartbeat · exactly one spark · no swarm |
| handoff | four-field request: Route ID, goal, write-scope, stop |

Current evidence: [`evidence/L3-PULSE.md`](evidence/L3-PULSE.md) and
[`evidence/HANDOFF.md`](evidence/HANDOFF.md). Installed `sekhmet 0.1.1` uses
direct Titanium by default and rejects an explicit `--direct`; the working L2
command is `sekhmet run --ro --timeout 90` and records `direct=true`.

The 2026-08-20 OAuth block below is retained as historical host state and is no
longer current.

## Refresh 2026-08-20 (host vgpnk@plazir27)

| Check | Result |
| --- | --- |
| host | **plazir27** · `vgpnk` · date 2026-08-20 |
| PATH install | `~/.local/bin/sekhmet` **0.1.1** · `codex-titanium` · `xask` thin `sekhmet --direct` shim |
| resolve | `CODEX_BIN` → `codex-titanium` → skip omarchy npx `codex` stub · **never** symlink titanium→`codex` |
| crate pin | model **`gpt-5.6-luna`** · effort **low** · `service_tier=fast` · fallback **none** · swarm **-j 64** |
| dry j=64 | **GATE_OK** (dry; no live claim on this host) |
| live | **blocked** — ChatGPT OAuth **Not logged in** (do not claim live j=64 here) |

Prior-host evidence below (vgpnk1337 / 2026-08-05–06) kept as historical; not re-run on plazir27.

Stamp: 2026-08-20 · host: plazir27 · docs pin reconcile

---

## Prior host — Refresh 2026-08-06 (xbgst sekhmet priority)

| Check | Result |
| --- | --- |
| dry j=64 re-gate | **64/64 GATE_OK** · `~/.xbgst/evidence/sekhmet-l3-dry64-20260806T171455Z` (+ labrat twin `...T171447Z`) |
| cargo test (sekhmetalt) | **pass** (labrat) |
| PATH install | `cargo install --path ~/Projects/sekhmetalt` · sekhmet **0.1.1** |
| tmux session `sekhmet` | **ensured** (substrate + orch) |
| plugin README pin | default **-j 64** (marketplace + grok + codex caches) |
| env | JOBS=64 · TIER=fast · MODEL default gpt-5.6-luna |

Stamp: 2026-08-06T17:17Z UTC · judge: xbgst sekhmet priority round

---

**xbgst judge (Grok):** working path verified 2026-08-05T21:09Z

| Check | Result |
| --- | --- |
| sekhmet binary | 0.1.1 on PATH |
| env | XBRD_SPARK_JOBS=64 · SERVICE_TIER=fast |
| OAuth | ChatGPT logged in |
| live oneshot luna+fast | ok |
| live j=8 luna+fast | **8/8 ok · gpt-5.6-luna** |
| dry j=64 | 64 lines |
| marketplace unittests | 27 OK |
| cli-parity dry | 18/18 PASS |
| sekhmet-l3 public | https://github.com/VeigaPunk/sekhmet-l3 |
| code_mode_host | disabled (not required for L3 sekhmet) |

Evidence: `/home/vgpnk1337/.xbgst/evidence/sekhmet-l3-xbgst-make-work-20260805T210844Z`

Canonical pin:
```bash
. ~/.xbgst/env.l3-sekhmet.sh
export XBRD_SPARK_MODEL=gpt-5.6-luna XBRD_SPARK_FALLBACK_MODEL=none XBRD_SPARK_SERVICE_TIER=fast
sekhmet swarm --direct -j 64 --ro --timeout 180 --no-keep -f tasks.txt --root "$(mktemp -d)"
```

## Live j=64 xbgst GATE (2026-08-06)

| Check | Result |
| --- | --- |
| live oneshot | ok |
| live j=8 luna+fast | **8/8 ok · gpt-5.6-luna** |
| live j=64 luna+fast | **64/64 ok · gpt-5.6-luna** |
| evidence | `~/.xbgst/evidence/sekhmet-l3-live-xbgst-j64-20260806T172514Z` |
| crate default model | **gpt-5.6-luna** (xbgst pin) |
| crate default jobs | **64** |
| env always-on | JOBS=64 · TIER=fast · MODEL=gpt-5.6-luna · FALLBACK=none |


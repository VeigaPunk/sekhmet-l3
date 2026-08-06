# STATUS — GATE_OK

## Refresh 2026-08-06 (xbgst sekhmet priority)

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


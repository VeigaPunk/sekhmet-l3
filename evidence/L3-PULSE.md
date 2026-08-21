# L3 pulse evidence

## Contract

- Cadence: once per 10-minute L2 lane heartbeat while the lane is active.
- Fan-out: exactly one spark per heartbeat. Never use `swarm` in this lane.
- Bound: `sekhmet run --ro --timeout 90`.
- Offline fallback: use one `--dry-run` only when OAuth or the dispatcher is blocked, and label it `dry-run` rather than live.
- Durable namespace: `~/.xbgst/evidence/sekhmet-l3-pulses`.
- Runner: `/home/vgpnk/Projects/xbgst/xbrd-spark/scripts/l2-pulse.sh`.
- Stop: after the first terminal record. Do not retry or fan out in the same heartbeat.

The active L2 session installed a 10-minute follow-up heartbeat labeled
`sekhmet-l3-pulse`. The wrapper also forces `XBRD_SPARK_JOBS=1`, independent of
any wider substrate capacity.

## Pulse log

| UTC | Route ID | Spark ID | Mode | Status / exit | Bound | Model / tier | Result | Artifact |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2026-08-21T17:06:54Z | `L2-L3-20260821T170654Z` | `sp-pulse-20260821T170654Z` | live, read-only | `ok` / `0` | `90s` (6156ms) | `gpt-5.6-luna` / `fast` | `SEKHMET_L3_PULSE_OK` + `godspeed` | `~/.xbgst/evidence/sekhmet-l3-pulses/sp-pulse-20260821T170654Z/out/result.json` |
| 2026-08-21T17:09:23Z | `L2-L3-20260821T170923Z-3eff` | `sp-pulse-20260821T170923Z-3eff` | requested dry-run, read-only | `ok` / `0` | `90s` (0ms; no model spawned) | `gpt-5.6-luna` pin / not called | `dry-run` | `~/.xbgst/evidence/sekhmet-l3-pulses/sp-pulse-20260821T170923Z-3eff/out/result.json` |

> The result cell's separator is the literal pipe character (`|`):
> `SEKHMET_L3_PULSE_OK | godspeed`.

## Verified provenance for the first pulse

- `sekhmet 0.1.1`
- dispatcher: `/home/vgpnk/.local/bin/codex-titanium`
- dispatcher version: `codex-cli 0.146.0-alpha.10.1+titanium.1`
- OAuth preflight: `Logged in using ChatGPT`
- `ro=true`, `direct=true`, `dry_run=false`, `timeout_secs=90`
- `usage_tokens=10704`
- content hash: `977128950fb9ecf61c559089721dff9f872353f005613fd7af638ed182b6553b`

The full result and `meta.json` are in the durable namespace above. This file
keeps only bounded evidence and spark identifiers.

# Tiny L2 -> L3 handoff

L2 remains the coordinator. L3 executes one bounded spark and does not judge,
select, persist PrimeAgent state, retry, or create more work.

## Request envelope

Use these four lines:

```text
Route ID: <unique L2 route, for example L2-L3-20260821T170654Z>
Goal: <exact task and expected one-line return>
Write-scope: read-only (`--ro`); no `--scope` unless an explicit directory is named
Stop: first terminal result or 90 seconds; one spark; no retry; no swarm
```

`Route ID` is an L2 correlation key. Sekhmet returns a separate `spark_id`.
Write only inside the spark namespace unless `Write-scope` explicitly grants a
scope. A broad or missing scope does not grant write access.

## Receipt

Return only the fields needed to audit the call:

```text
Route ID: <same value>
Spark ID: <sp-...>
Result: <live|dry-run> <ok|fail|timeout> exit=<code>
Artifact: <.../out/result.json>
```

A dry result proves the dispatch shape, not model availability. It must never be
reported as a live L3 result.

## Example

```text
Route ID: L2-L3-20260821T170654Z
Goal: Read-only callability pulse; return `SEKHMET_L3_PULSE_OK | godspeed`
Write-scope: read-only (`--ro`); namespace artifacts only
Stop: first terminal result or 90 seconds; one spark; no retry; no swarm
```

Receipt:

```text
Route ID: L2-L3-20260821T170654Z
Spark ID: sp-pulse-20260821T170654Z
Result: live ok exit=0
Artifact: ~/.xbgst/evidence/sekhmet-l3-pulses/sp-pulse-20260821T170654Z/out/result.json
```

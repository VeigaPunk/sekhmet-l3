# EVIDENCE — sekhmet-l3 ship 2026-08-05T21:06Z

Host evidence dir: `/home/vgpnk1337/.xbgst/evidence/sekhmet-l3-sol-ultra-20260805T210312Z`

## Live oneshot (luna + fast)

```json
{
  "spark_id": "sp-e6354307-422f-4e97-8dc3-08aa138ce9f3",
  "content_hash": "7d1ae712a608ce3db2305901a7fbf5ee355bc3990e731fb2ff038432f5db171b",
  "status": "ok",
  "result_path": "/tmp/tmp.sCN2pGSGuT/sp-e6354307-422f-4e97-8dc3-08aa138ce9f3/out/result.json",
  "artifacts": [
    "/tmp/tmp.sCN2pGSGuT/sp-e6354307-422f-4e97-8dc3-08aa138ce9f3/out/artifacts/fc43c812c710b38a6f366e42bb127e1addf4868b6805ec4b5e8efefaa3382469",
    "/tmp/tmp.sCN2pGSGuT/sp-e6354307-422f-4e97-8dc3-08aa138ce9f3/out/artifacts/bc99b5d5bfc1c8f41460cd889f948e1ad0def106c7f4233b65f728903e6cc8c4",
    "/tmp/tmp.sCN2pGSGuT/sp-e6354307-422f-4e97-8dc3-08aa138ce9f3/out/artifacts/2bd7ec14799610c1b0971d1f250191edcaf819e4f194005307480a635b7826df",
    "/tmp/tmp.sCN2pGSGuT/sp-e6354307-422f-4e97-8dc3-08aa138ce9f3/out/artifacts/2e8faad2abed1f42d78ef714749cf7235807eddf95c07a8ab90d3a1d7f58c5ed"
  ],
  "usage_tokens": 9811,
  "provenance": {
    "spark_id": "sp-e6354307-422f-4e97-8dc3-08aa138ce9f3",
    "started_at": "2026-08-05T21:03:12.906404046+00:00",
    "finished_at": "2026-08-05T21:03:15.961667381+00:00",
    "duration_ms": 3055,
    "model": "gpt-5.6-luna",
    "cmdline": [
      "/home/vgpnk1337/.local/bin/codex-titanium",
      "exec",
      "-m",
      "gpt-5.6-luna",
      "-c",
      "model_reasoning_effort=low",
      "-c",
      "service_tier=fast",
      "--ephemeral",
      "--skip-git-repo-check",
      "--color",
      "never",
      "--sandbox",
      "read-only",
      "-c",
      "approval_policy=never",
      "Reply with exactly: SEKHMET_LUNA_FAST_OK"
    ],
    "status": "ok",
    "exit_code": 0,
    "content_hash": "7d1ae712a608ce3db2305901a7fbf5ee355bc3990e731fb2ff038432f5db171b",
    "task_hash": "fc59d2686f8b132d0b7809433708cde09c076c9a2d481637ace94913bbbef3bd",
    "invoker": "vgpnk1337",
    "scope": null,
    "ro": true,
    "timeout_secs": 120,
    "direct": true,
    "dry_run": false,
    "root": "/tmp/tmp.sCN2pGSGuT/sp-e6354307-422f-4e97-8dc3-08aa138ce9f3",
    "usage_tokens": 9811
  }
}
```

### Claims verified

- status=`ok`, exit_code=`0`
- model=`gpt-5.6-luna` (gpt-5.6-luna)
- cmdline includes `-c service_tier=fast` and `-c model_reasoning_effort=low`
- `--direct` + read-only sandbox (sekhmet `--ro`)
- duration_ms=`3055`

## Dry swarms

- 8-wide dry: dry_lines=8
- 64-wide dry: dry64_lines=64

## Live multi (j=4)

- summary: live4_lines=4
- models: 4 gpt-5.6-luna

## Prior 64/64 campaign

Host file: `sekhmet-luna-j64-fast-luna_oauth_fast_20260805T020337Z-summary.json`

## Marketplace local gates (this session)

- unittest discover → **OK** (27)
- cli-parity dry-run → **18/18 PASS**
- validate-agent-payloads → **15 the-* payloads**
- sekhmet skill: default **64**, luna+fast pin

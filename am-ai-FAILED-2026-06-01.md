# AM-AI Morning Briefing — FAILED (2026-06-01)

**Run date:** 2026-06-01 (UTC)

## What happened

The `digg-pp-cli` binary was installed successfully from source (`v1.0.0`). However, the `digg-pp-cli sync --agent` command failed at the data-fetching step with an HTTP 403 error from the Digg API:

```
fetching /ai ...
Error: fetching /ai: HTTP 403 for https://di.gg/ai
```

Without a successful sync, the local cluster store is empty and neither `digg-pp-cli top` nor `digg-pp-cli rising` can return data. No briefing was produced.

## Possible causes

- The Digg API (`di.gg`) is blocking requests from this IP or environment (rate limit, geo-block, or bot detection).
- The API endpoint may be temporarily down or require authentication that was not provided.
- Network egress from this execution environment may be restricted.

## Next steps

Retry the briefing once the API is accessible, or investigate whether the execution environment's network policy permits outbound requests to `di.gg`.

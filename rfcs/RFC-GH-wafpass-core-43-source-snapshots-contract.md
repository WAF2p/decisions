# RFC-GH-wafpass-core-43: Source Snapshots — Ingestion Contract and Reliable Upload Path

| Field | Value |
|---|---|
| **RFC ID** | RFC-GH-wafpass-core-43 |
| **Status** | open |
| **Category** | tooling |
| **Author** | lewandos |
| **Opened** | 2026-07-18 |
| **Repository** | wafpass-core |
| **GitHub issue** | [#43](https://github.com/WAF2p/wafpass-core/issues/43) |

---

## Summary

Dashboard local preview and auto-fix rely on `Run.source_snapshot`, a JSONB map of relative IaC file paths to raw file contents. Today it is only captured when the CLI is invoked with both `--output json` and `--upload-source`. This RFC defines a reliable ingestion contract and upload path.

## Status

Tracked as an open GitHub issue in `WAF2p/wafpass-core` (to be renamed `WAF2p/wafpass-core`). This file is a mirror for the decisions registry; the canonical discussion is on GitHub.

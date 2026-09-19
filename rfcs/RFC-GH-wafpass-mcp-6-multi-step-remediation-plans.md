# RFC-GH-wafpass-mcp-6: Multi-step remediation plans (apply with rollback)

| Field | Value |
|---|---|
| **RFC ID** | RFC-GH-wafpass-mcp-6 |
| **Status** | open |
| **Category** | tooling |
| **Author** | lewandos |
| **Opened** | 2026-08-14 |
| **Repository** | wafpass-mcp |
| **GitHub issue** | [#6](https://github.com/WAF2p/wafpass-mcp/issues/6) |

---

## Summary

Users can classify and preview patches, but applying them requires a separate auto-fix call with a filesystem path. There is no safe "apply this classify result to this run and record what changed." Proposal: extend `/api/v1/auto-fix/classify` with an apply step that records changes and supports rollback.

## Status

Tracked as an open GitHub issue in `WAF2p/wafpass-mcp`. This file is a mirror for the decisions registry; the canonical discussion is on GitHub.

# RFC-GH-wafpass-mcp-5: Streaming/paginated tool results for large runs

| Field | Value |
|---|---|
| **RFC ID** | RFC-GH-wafpass-mcp-5 |
| **Status** | open |
| **Category** | tooling |
| **Author** | lewandos |
| **Opened** | 2026-08-14 |
| **Repository** | wafpass-mcp |
| **GitHub issue** | [#5](https://github.com/WAF2p/wafpass-mcp/issues/5) |

---

## Summary

Runs with thousands of findings return huge JSON blobs. The current proxy loads everything into one TextContent block, which is slow and can hit MCP message size limits. Proposal: add cursor-based pagination helpers to the bridge for list and detail calls.

## Status

Tracked as an open GitHub issue in `WAF2p/wafpass-mcp`. This file is a mirror for the decisions registry; the canonical discussion is on GitHub.

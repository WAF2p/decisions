# RFC-GH-wafpass-mcp-4: MCP resource-level read-only endpoints

| Field | Value |
|---|---|
| **RFC ID** | RFC-GH-wafpass-mcp-4 |
| **Status** | open |
| **Category** | tooling |
| **Author** | lewandos |
| **Opened** | 2026-08-14 |
| **Repository** | wafpass-mcp |
| **GitHub issue** | [#4](https://github.com/WAF2p/wafpass-mcp/issues/4) |

---

## Summary

The MCP bridge currently exposes only tools. Users cannot ask "what controls failed in this run?" or "show me the source snapshot" without making multiple tool calls and stitching JSON together. Proposal: add MCP Resource definitions for `run://{run_id}`, `control://{id}`, etc.

## Status

Tracked as an open GitHub issue in `WAF2p/wafpass-mcp`. This file is a mirror for the decisions registry; the canonical discussion is on GitHub.

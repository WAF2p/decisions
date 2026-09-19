# RFC-GH-wafpass-mcp-3: Auto-fix default templates for WAFpass controls

| Field | Value |
|---|---|
| **RFC ID** | RFC-GH-wafpass-mcp-3 |
| **Status** | open |
| **Category** | tooling |
| **Author** | lewandos |
| **Opened** | 2026-08-14 |
| **Repository** | wafpass-mcp |
| **GitHub issue** | [#3](https://github.com/WAF2p/wafpass-mcp/issues/3) |

---

## Summary

`auto-fix/classify` returns zero active patches for many controls because assertions like `not_empty`, `attribute_exists`, `is_true` have no registered default value. Proposal: add a fix block to control YAMLs (or a central provider registry) that declares default patches per assertion.

## Status

Tracked as an open GitHub issue in `WAF2p/wafpass-mcp`. This file is a mirror for the decisions registry; the canonical discussion is on GitHub.

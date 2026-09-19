# RFC-GH-wafpass-mcp-7: Role-aware natural tool aliasing

| Field | Value |
|---|---|
| **RFC ID** | RFC-GH-wafpass-mcp-7 |
| **Status** | open |
| **Category** | tooling |
| **Author** | lewandos |
| **Opened** | 2026-08-14 |
| **Repository** | wafpass-mcp |
| **GitHub issue** | [#7](https://github.com/WAF2p/wafpass-mcp/issues/7) |

---

## Summary

Tool names are long and auto-generated (e.g. `api_auto_fix_classify_api_v1_auto_fix_classify_post`). The LLM has to match long operation IDs, and descriptions embed role/category, making prompts noisy. Proposal: allow curated aliases for tools so LLMs can invoke them more naturally.

## Status

Tracked as an open GitHub issue in `WAF2p/wafpass-mcp`. This file is a mirror for the decisions registry; the canonical discussion is on GitHub.

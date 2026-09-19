# RFC-GH-wafpass-core-40: Dashboard UX Overhaul

| Field | Value |
|---|---|
| **RFC ID** | RFC-GH-wafpass-core-40 |
| **Status** | open |
| **Category** | tooling |
| **Author** | lewandos |
| **Opened** | 2026-07-18 |
| **Repository** | wafpass-core |
| **GitHub issue** | [#40](https://github.com/WAF2p/wafpass-core/issues/40) |

---

## Summary

The dashboard exposes 46 pages through a bloated 700px-wide mega-menu. Navigation logic is duplicated across `Sidebar.tsx` and `MobileMenu.tsx`. This RFC proposes a guided onboarding flow, role-based landing pages, and progressive disclosure to reduce cognitive load.

## Status

Tracked as an open GitHub issue in `WAF2p/wafpass-core` (to be renamed `WAF2p/wafpass-core`). This file is a mirror for the decisions registry; the canonical discussion is on GitHub.

# RFC-0004: Documentation migration to AsciiDoc / Antora

| Field | Value |
|---|---|
| **RFC Number** | 0004 |
| **Status** | implemented |
| **Category** | docs |
| **Author** | t1murl |
| **Opened** | 2026-02-20 |
| **Decided** | 2026-02-26 |
| **Implemented** | 2026-02-26 |
| **Repository** | framework |
| **PR** | 4 |

---

## Summary

Migrates all framework documentation from Markdown to AsciiDoc and establishes Antora as the documentation build system with component versioning (v1.0).

## Decision

Use AsciiDoc for framework content and Antora for site generation. Version the framework as an Antora component.

## Related records

- ADR-002 — Two-branch docs model
- RFC-0011 — CI/CD pipeline

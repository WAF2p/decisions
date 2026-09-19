# ADR-001: The wafpass-result.json Contract

| Field | Value |
|---|---|
| **ADR Number** | 001 |
| **Title** | The wafpass-result.json Contract |
| **Status** | accepted |
| **Date** | 2026-09-17 |
| **Authors** | Sascha Lewandowski |
| **Audience** | Engine, server, dashboard, and integration maintainers |

---

## Context

WAF++ has multiple independently released components: `wafpass-core` produces scan results; `wafpass-server` ingests and queries them; `wafpass-dashboard` visualises them; PDF reporters and observability exporters consume them. Without a single contract every component would invent its own format, making integration fragile.

## Decision

All scan results, findings, waivers, risk acceptances, and run metadata are exchanged through **one JSON document: `wafpass-result.json`**.

The contract is normatively defined by the Pydantic model in `wafpass-core` (`wafpass/schema.py`) and exposed as an OpenAPI schema by `wafpass-server`. The schema version is carried inside the document itself (`version`).

## Core sections

| Section | Purpose |
|---|---|
| `version` | Schema version of the document. |
| `generator` | Tool, version, and plugin that produced the result. |
| `run` | Identity, timestamps, project, stage, and source paths. |
| `summary` | Aggregated counts: passed, failed, total, score, tier. |
| `findings` | Per-control, per-resource evaluation results. |
| `waivers` | Active waivers applied during evaluation. |
| `risks` | Risk acceptances linked to findings. |
| `metadata` | Tags, environment, CI context, source snapshot hash. |

## Consequences

- **Positive**: one integration surface; dashboards and exporters can rely on a stable schema; golden-file tests are possible.
- **Negative**: any schema change must be coordinated across components; breaking changes require a new major schema version.
- **Neutral**: optional sections are allowed; unknown fields should be preserved (round-tripped) by consumers.

## Related records

- ADR-000 — Umbrella architecture
- RFC-0008 — Controls schema v1
- RFC-0013 — WAFPass support for Pillar-8 Agentic

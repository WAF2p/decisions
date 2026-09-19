# ADR-002: Two Long-Lived Branches for German and English Framework Documentation

| Field | Value |
|---|---|
| **ADR Number** | 002 |
| **Title** | Two Long-Lived Branches for German and English Framework Documentation |
| **Status** | accepted |
| **Date** | 2026-09-17 |
| **Authors** | Sascha Lewandowski |
| **Audience** | Docs maintainers, translators, release managers |

---

## Context

WAF++ is developed in Germany and targets both German-speaking and international users. The framework documentation must ship in German and English, but the two language editions do not mature at the same pace and are not word-for-word translations.

## Decision

Use two long-lived branches in the same repository:

- `main-de` — checked out as `framework/` — German Antora component.
- `main-en` — checked out as `framework-en/` — English Antora component.

Each branch has its own `antora.yml` with a language-tagged version (`1.0.2-de`, `1.0.2-en`). The website repository (`waf2p.github.io`) lists both directories as Antora content sources.

## Why two branches, not one?

- **Independent release cadence**: A German content update can ship without waiting for English translation.
- **Clean diffs and reviews**: A German-only change never pollutes the English history and vice versa.
- **Cherry-pick friendliness**: A fix made in one language can be cherry-picked to the other branch if it applies.
- **Tooling simplicity**: Antora natively treats each branch as a separate component version.
- **Future-language scalability**: Additional languages can be added as further long-lived branches without restructuring.

## Consequences

- **Positive**: translators can work asynchronously; release managers control per-language versions explicitly.
- **Negative**: structural changes (new modules, nav files, controls) must usually be mirrored across both branches.
- **Neutral**: the same repository is cloned twice in the umbrella directory, which is a deliberate local convenience, not a fork.

## Related records

- ADR-000 — Umbrella architecture
- RFC-0004 — Documentation migration to AsciiDoc / Antora

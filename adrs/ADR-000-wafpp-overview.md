# ADR-000: WAF++ Federated Repository Architecture & Onboarding Overview

| Field | Value |
|---|---|
| **ADR Number** | 000 |
| **Title** | WAF++ Umbrella Architecture & Onboarding Overview |
| **Status** | accepted |
| **Date** | 2026-09-17 |
| **Authors** | Artem Lajko, Sascha Lewandowski, Sebastian Meyer, Tim Urlaub |
| **Audience** | New team members, contributors, architects, reviewers |

---

## 1. Abstract

This Architecture Decision Record (ADR-000) is the **master onboarding document** for the WAF++ (Well-Architected Framework++) ecosystem. It explains the overall architecture, the role of every included git repository, how the repositories interact, and the conventions a new team member needs to become productive.

WAF++ is a community-driven, cloud-agnostic framework for sovereign, secure, and sustainable cloud architectures. It combines written framework guidance with a concrete compliance engine (`wafpass-core`) that scans Infrastructure-as-Code (IaC), persists results, and visualises them in a browser dashboard.

---

## 2. What is WAF++?

- **8 pillars**: Security, Cost, Performance Efficiency, Reliability, Operational Excellence, Sustainability, Sovereign, Agentic.
- **Machine-readable controls**: YAML control definitions checked automatically against Terraform, AWS CDK, Pulumi, and (planned) Bicep.
- **Compliance engine**: `wafpass-core` parses IaC, evaluates controls, and produces a standardised result.
- **Server + Dashboard**: A FastAPI/PostgreSQL server stores scan results; a React dashboard visualises compliance posture.
- **CI/CD integration**: GitHub Action, pre-commit hook, and CLI for pipeline gating.
- **AI bridge**: An MCP (Model Context Protocol) bridge lets authenticated AI assistants query WAF++ data.

---

## 3. Repository Landscape

The umbrella directory is the parent folder that contains multiple independent git repositories.

| Repository | Short name | Technology | Purpose |
|---|---|---|---|
| `framework` (`main-de`) | German framework docs | Antora / AsciiDoc | German edition of the WAF++ framework documentation |
| `framework-en` (`main-en`) | English framework docs | Antora / AsciiDoc | English edition of the WAF++ framework documentation |
| `waf2p.github.io` | Website | Jekyll + Antora | Public website (`https://waf2p.dev`), marketing pages, blog, integrated docs |
| `wafpass-core` | WAFPass Core | Python 3.11+ | IaC compliance engine, CLI, result schema, PDF reporting |
| `wafpass-server` | Server | Python / FastAPI / SQLAlchemy / PostgreSQL | REST API for persisting and querying scan results |
| `wafpass-dashboard` | Dashboard | React 18 / TypeScript / Vite | Browser SPA that consumes the server API |
| `wafpass-mcp` | MCP bridge | Python / FastAPI / MCP SDK | Model Context Protocol bridge for AI assistants |
| `wafpass-action` | GitHub Action | Python composite action | GitHub Action to run WAFPass scans in CI/CD |

`framework` and `framework-en` are the same repository cloned twice, each checked out at a different branch (`main-de` and `main-en`). See ADR-002 for the rationale.

---

## 4. High-Level Architecture

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│                              WAF++ Ecosystem                                │
├─────────────────────────────────────────────────────────────────────────────┤
│  Public surface                                                             │
│   • waf2p.github.io  → Jekyll marketing site + Antora docs (framework)     │
├─────────────────────────────────────────────────────────────────────────────┤
│  Compliance platform                                                        │
│   • wafpass-core     → CLI / library / CI scanner                          │
│   • wafpass-action   → GitHub Actions wrapper                              │
│   • wafpass-server   → FastAPI + PostgreSQL persistence layer              │
│   • wafpass-dashboard → React SPA visualisation                            │
│   • wafpass-mcp      → MCP bridge for AI assistants                        │
└─────────────────────────────────────────────────────────────────────────────┘
```

The central data contract is **`wafpass-result.json`** produced by `wafpass-core`. It is consumed by the server, dashboard, PDF reporter, and observability exports. See ADR-001.

---

## 5. Conventions & Decisions

1. **Single result schema**: `wafpass-result.json` is the only contract between engine, server, dashboard, and exports.
2. **Versioned API**: All server endpoints live under `/api/v1`; unversioned paths were removed.
3. **Umbrella layout**: Each component is a separate git repo under a common umbrella directory.
4. **Docs separate from site**: Framework content lives in `framework` / `framework-en` (same repository, branches `main-de` / `main-en`); the website consumes them as Antora sources.
5. **Controls as data**: WAF++ controls are YAML files, not code, and can be updated independently of the engine.
6. **SSO-ready**: The server supports OIDC/SAML2 SSO; production brings its own IdP.
7. **ADR/RFC home**: All architecture decisions and RFCs live in `WAF2p/decisions` so they evolve independently of component releases.

---

## 6. Getting Started Checklist

- [ ] Read this ADR (ADR-000).
- [ ] Read ADR-001 (the `wafpass-result.json` contract) and ADR-002 (two-branch docs).
- [ ] Start `wafpass-server` and `wafpass-dashboard` locally by following their `README.md` files.
- [ ] Run `wafpass check ./dummy_code --summary` from the `wafpass-core` repo to see the CLI in action.
- [ ] Push a result to the local server and view it in the dashboard.
- [ ] Read the per-repo `README.md` and `TECH.md` / `AGENTS.md` for the component you will work on.

---

## 7. References

- WAF++ website: https://waf2p.dev
- English docs: https://waf2p.dev/docs/wafpp/1.0.2-en/
- German docs: https://waf2p.dev/docs/wafpp/1.0.2-de/
- `decisions` registry: `./registry.yml`

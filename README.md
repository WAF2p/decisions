# WAF++ Decisions

Single source of truth for Architecture Decision Records (ADRs) and Requests for Comments (RFCs) across the WAF++ ecosystem.

- **Live view**: open [`index.html`](./index.html) in a browser for a standalone showcase.
- **Machine-readable index**: [`registry.yml`](./registry.yml).
- **Website integration**: `https://waf2p.dev/rfc/` consumes this registry.

---

## Why a separate decisions repo?

ADRs and RFCs are cross-cutting: a decision about `wafpass-result.json` affects `wafpass-core`, `wafpass-server`, and the dashboard. Keeping them in one repository means:

- **Decision velocity** is independent of component release velocity.
- **No duplication** across the two framework language branches (`main-de` / `main-en`).
- **Traceability**: every significant change has a stable URL and a documented lifecycle.
- **Website decoupled**: marketing site redesigns do not rewrite decision history.

---

## Repository layout

```text
decisions/
├── README.md                          # This file
├── registry.yml                       # Machine-readable index of all ADRs/RFCs
├── index.html                         # Standalone HTML showcase (no build needed)
├── templates/
│   ├── adr-template.md                # Template for new ADRs
│   └── rfc-template.md                # Template for new RFCs
├── adrs/
│   ├── ADR-000-wafpp-overview.md
│   ├── ADR-001-wafpass-result-json.md
│   └── ADR-002-two-branch-docs.md
└── rfcs/
    ├── RFC-0001-*.md … RFC-0017-*.md  # Canonical RFCs
    └── RFC-GH-*-*.md                  # Open proposals tracked as GitHub issues
```

---

## Conventions

### ADRs

- Filename: `adrs/ADR-NNNN-kebab-title.md`
- Lifecycle: `proposed` → `accepted` → `deprecated` | `superseded`
- Each ADR records a decision that is hard to change or expensive to undo.

### RFCs

- Filename: `rfcs/RFC-NNNN-kebab-title.md` for canonical RFCs
- Filename: `rfcs/RFC-GH-{repo}-{number}-kebab-title.md` for proposals that live as GitHub issues
- Lifecycle: `draft` → `open` → `accepted` / `rejected` / `withdrawn` → `implemented`

### Registry

Every ADR and RFC is listed in `registry.yml`. The website and the standalone HTML view read from this file.

When you add or update a record:

1. Create the markdown file.
2. Add the entry to `registry.yml`.
3. Update `index.html` by running the generator (or manually keep the embedded JSON in sync).

---

## How to propose a new ADR or RFC

1. Copy the appropriate template from `templates/`.
2. Name the file following the convention above.
3. Fill in the frontmatter and the required sections.
4. Add the record to `registry.yml`.
5. Open a pull request in this repository.
6. For RFCs: also open a GitHub Discussion in the relevant component repo if community review is required.

---

## What needs an RFC?

| Change type | RFC needed? |
|---|---|
| New or removed pillar | Yes |
| Scoring model changes | Yes |
| Breaking change to controls schema or IDs | Yes |
| New working group proposal | Yes |
| Governance or role changes | Yes |
| New control (additive, non-breaking) | Recommended |
| Docs wording, typo fixes, translations | No — PR only |
| Website content, blog posts | No — PR only |

---

## License

CC-BY-4.0

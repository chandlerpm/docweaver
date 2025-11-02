# Architecture Overview


- **Config layer**: `config.yml` stores variables like `project_name`, `version`.
- **Template layer**: Markdown files with `{{variable}}` tokens.
- **Output layer**: Generated docs (README, guides) with variables resolved.

```mermaid
flowchart TD
    U[User] --> C[config.yml<br/>(variables)]
    C --> T[templates/<br/>(Markdown with placeholders)]
    T --> O[output/<br/>(woven docs)]

> This repository ships **example templates** only (no real generator).

---

## 🏗️ Repository Structure

```mermaid
graph TD
    A[📦 DocWeaver Repository] --> B[README.md<br/>Project overview]
    A --> C[docs/<br/>Documentation library]
    A --> D[examples/<br/>Sample templates]
    A --> E[.github/<br/>Actions & templates]
    A --> F[LICENSE]
    A --> G[CHANGELOG.md]
    A --> H[CONTRIBUTING.md]

    C --> C1[overview/<br/>Concepts & Architecture]
    C --> C2[guides/<br/>Tutorials]
    C --> C3[reference/<br/>YAML & CLI]
    C --> C4[troubleshooting/<br/>FAQ & errors]
    C --> C5[contributing/<br/>Content standards]

    E --> E1[ISSUE_TEMPLATE.md]
    E --> E2[PULL_REQUEST_TEMPLATE.md]
    E --> E3[workflows/<br/>docs-lint.yml]

    D --> D1[sample-readme.md]
    D --> D2[sample-config.yml]
    D --> D3[template-example.md]
```

**Figure 3:** Repository-level architecture showing documentation, examples, and automation layers.

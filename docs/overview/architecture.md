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

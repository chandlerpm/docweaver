# CLI Reference (Fictional)

> The CLI is illustrative; commands show how docs would be generated.

## Commands

```bash
docweaver init <path>
```
Create a starter folder with templates and a sample config.

```bash
docweaver weave --config config.yml --out ./docs
```
Render templates using variables and write output files.

```bash
docweaver lint
```
Check Markdown and links.

## Exit codes
| Code | Meaning |
|------|----------|
| `0` | success |
| `1` | validation or lint failure |

# Config File Reference (`config.yml`)

```yaml
project_name: "Acme Service"
version: "1.0.0"
author: "Team Acme"
links:
  homepage: "https://example.com"
  docs: "https://example.com/docs"
profiles:
  internal:
    audience: "Engineering"
  external:
    audience: "Customers"
```

**Required keys**
- `project_name` — string  
- `version` — semantic version number  

**Optional**
- `author` — string  
- `links.*` — URLs  
- `profiles.*` — nested objects for custom audiences  

> **Tip:** Keep keys lowercase with hyphens or underscores for readability.

---

## Related
- [Template Variables](template-variables.md) — how placeholders are defined and substituted

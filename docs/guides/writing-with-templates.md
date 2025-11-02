# Writing with Templates

This guide explains how to use **DocWeaver**’s Markdown templates and configuration system to create new documentation pages quickly and keep style and structure consistent across the project.

---

## 🧶 What Templates Are

A **template** is a pre-formatted Markdown file that includes standardized headings and placeholder variables. Templates help you:

- Maintain consistent tone and layout  
- Reduce formatting errors  
- Reuse common sections (prerequisites, steps, references)  
- Centralize project terms via variables from `config.yml`

---

## 🧩 Template Basics

Templates can include variables like `{{ project_name }}` or `{{ version }}` that are later substituted by values from `config.yml`.

**Skeleton template example**

```
# {{ project_name }} — {{ page_title }}

_Updated: {{ last_updated }}_

## Overview
{{ description }}

## Steps
1. {{ step_one }}
2. {{ step_two }}

## Related Pages
- [Overview](../overview/what-is-docweaver.md)
- [Configuration Reference](../reference/config-file.md)
```

---

## ⚙️ Defining Variables in `config.yml`

Declare variables once and reuse them across pages.

```yaml
project_name: DocWeaver
version: 0.3.0
author: Julie Chandler
last_updated: 2025-11-02
description: >
  A flexible documentation template system for small teams and solo developers.
step_one: Create a new documentation folder structure.
step_two: Customize templates with your own variables.
```

---

## ✍️ Authoring with a Template (Manual Workflow)

1. **Choose a template**  
   Browse the examples in the repo root:  
   - `examples/template-example.md` — full template  
   - `examples/sample-readme.md` — rendered sample  
   - `examples/sample-config.yml` — example variables

2. **Copy and rename**  
   Place the new page in the appropriate section:
   ```
   cp examples/template-example.md docs/guides/new-feature.md
   ```

3. **Replace placeholders**  
   Update `config.yml` with any new keys, then replace `{{ ... }}` placeholders in your new page (or render with the optional script below).

4. **Preview and link**  
   - Ensure internal links are **relative** (e.g., `../reference/config-file.md`).  
   - Add a short caption under any diagram: `**Figure X:** …`.

5. **Commit**  
   Keep commits focused; reference the page or section you touched.

---

## 🤖 Optional: Simple Local Renderer (for demonstration)

You can simulate variable substitution with a tiny Python script (useful as a portfolio demo):

```python
import yaml, re, sys
template_path = "examples/template-example.md"
output_path   = "docs/guides/generated.md"

with open("config.yml") as f:
    config = yaml.safe_load(f)

with open(template_path) as t:
    text = t.read()

for key, val in config.items():
    pattern = r"{{\s*" + re.escape(key) + r"\s*}}"
    text = re.sub(pattern, str(val), text)

# Remove any unresolved placeholders (optional tidy-up)
text = re.sub(r"{{\s*[^}]+\s*}}", "", text)

with open(output_path, "w") as out:
    out.write(text)

print(f"Wrote {output_path}")
```

Run:
```bash
python render_template.py
```

---

## 🧠 Writing Conventions (Quick Reference)

| Element | Guideline | Example |
|---|---|---|
| **Headings** | Sentence case; one `#` per page | “Writing with templates” |
| **Lists** | `1.` for steps, `-` for unordered | Clear, parallel phrasing |
| **Notes** | Use blockquotes | `> Note:` clarity over cleverness |
| **Code blocks** | Always set a language | ```yaml, ```bash |
| **Links** | Relative paths inside `docs/` | `../reference/config-file.md` |
| **Figures** | Caption below diagram | `**Figure 1:** Architecture overview` |

---

## 🧱 End-to-End Example

**Template (`examples/template-example.md`)**
```
# {{ project_name }} — {{ page_title }}

_Last updated: {{ last_updated }}_

## Purpose
{{ purpose }}

## Steps
1. {{ step_one }}
2. {{ step_two }}

## References
- [Overview](../overview/what-is-docweaver.md)
```

**Variables (`config.yml`)**
```yaml
project_name: DocWeaver
page_title: Write with Templates
last_updated: 2025-11-02
purpose: Demonstrate how to reuse documentation templates efficiently.
step_one: Identify a suitable template from /examples.
step_two: Replace placeholders with project-specific variables.
```

**Rendered result (`docs/guides/write-with-templates.md`)**
```
# DocWeaver — Write with Templates

_Last updated: 2025-11-02_

## Purpose
Demonstrate how to reuse documentation templates efficiently.

## Steps
1. Identify a suitable template from /examples.
2. Replace placeholders with project-specific variables.

## References
- [Overview](../overview/what-is-docweaver.md)
```

---

## ✅ Best Practices

- **Keep templates DRY:** factor recurring blocks (Prerequisites, Steps, References).  
- **Centralize terminology:** prefer `config.yml` keys over hard-coding product names.  
- **Avoid over-templating:** readers shouldn’t see raw placeholders in committed docs.  
- **Track changes:** log template additions or rewrites in `CHANGELOG.md`.  
- **CI friendly:** keep links relative; verify with the Docs Quality Check workflow.

---

> Templates are the backbone of sustainable documentation. Treat them like code: small, reusable, and clearly named.

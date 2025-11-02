# Content Standards for DocWeaver

DocWeaver maintains clear, consistent formatting to model professional documentation practices.

---

## 🧱 Structure
| Element | Rule |
|----------|------|
| Headings | Use sentence case (`Getting started`, not `Getting Started`) |
| Code blocks | Use triple backticks with a language tag (` ```yaml`, ` ```bash`) |
| Lists | Use hyphens `-` for unordered lists |
| Figures | Label as `**Figure X:**` below diagrams |
| Diagrams | Prefer [Mermaid](https://mermaid.js.org/) for all flow/architecture charts |

---

## ✍️ Style
- Be concise but complete.  
- Use the active voice.  
- Avoid filler words like *simply*, *just*, *basically*.  
- Define all acronyms on first use.  
- Use consistent terminology across guides.

---

## 📚 Example
```markdown
## Configure a new template

To define reusable variables, edit the `config.yml` file:

```yaml
project_name: "Acme Service"
author: "Team Acme"
```

**Figure 1:** Example YAML configuration for DocWeaver.
```

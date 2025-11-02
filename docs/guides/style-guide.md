# Style Guide for DocWeaver Documentation

This guide defines the editorial and visual standards that keep DocWeaver’s documentation clear, cohesive, and professional.

---

## ✏️ Tone and Voice
- Write in **second person** (“you”) when instructive.  
- Maintain a **neutral, confident, and concise** tone.  
- Avoid filler words like *just*, *simply*, *basically*.  
- Prefer plain language over jargon.

**Example:**
> ✅ “Run the command below to create your project.”  
> ❌ “Simply run the command to quickly create your awesome new project!”

---

## 🧭 Headings and Structure
- Use **sentence case** for headings (`Getting started`, not `Getting Started`).  
- One H1 (`#`) per page.  
- Keep headings descriptive and parallel in form.  
- Include a short one-line summary before major sections.

---

## 🧩 Lists and Code
- Use `-` for unordered lists, `1.` for ordered lists.  
- Always include a language identifier for code fences:

```bash
# good
git commit -m "Add templates"
```

- Wrap long commands or URLs to a new line for readability.

---

## 🧠 Figures and Diagrams
- Use [Mermaid](https://mermaid.js.org/) for flowcharts and architecture diagrams.  
- Place a bold caption immediately beneath the diagram, e.g.:

```markdown
**Figure 1:** Repository structure for DocWeaver.
```

---

## 🎨 Formatting and Symbols
| Element | Style |
|----------|-------|
| File names | `monospace` (e.g., `config.yml`) |
| Keyboard input | **Bold** (e.g., **⌘S**) |
| UI elements | *Italics* (e.g., *Source Control* panel) |
| Notes and tips | Use blockquotes `>`, not callouts |

---

## 💬 Consistency Checklist
- [ ] Sentence case headings  
- [ ] Code blocks labeled with language  
- [ ] Figures labeled with bold caption  
- [ ] Relative links used for internal references  
- [ ] One topic per file  

---

> Following this style guide keeps all DocWeaver documentation aligned with professional industry standards.

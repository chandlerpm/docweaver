# Getting Started with DocWeaver

Welcome to **DocWeaver** — a fictional but realistic toolkit for managing structured documentation.

This guide walks you through how to explore and customize the example templates to understand how DocWeaver works conceptually.

---

## 🪴 1. Understand the Repository Layout

```
DocWeaver/
├── README.md
├── docs/
│   ├── overview/
│   ├── guides/
│   ├── reference/
│   ├── troubleshooting/
│   └── contributing/
├── examples/
├── config.yml
└── .github/
```

Each directory models a real documentation system:
- `docs/` – Main documentation hierarchy  
- `examples/` – Sample Markdown and YAML templates  
- `.github/` – Actions, templates, and automation examples  

---

## ⚙️ 2. Explore the Example Templates

Open the [`examples/`](../../examples/) folder to see:
- `sample-readme.md` – the woven output example  
- `template-example.md` – the original Markdown template  
- `sample-config.yml` – the YAML configuration controlling placeholders  

These show how **variables** and **templates** can be combined for documentation consistency.

---

## ✍️ 3. Try Customizing the Configuration

Edit `config.yml`:

```yaml
project_name: "My Documentation Project"
author: "Your Name"
version: "1.0"
```

This file acts as your project-wide variable store. In a real generator, placeholders like `{{project_name}}` would resolve to these values when “woven.”

---

## 🧶 4. Render or Preview

While DocWeaver doesn’t actually run a generator, you can use this repository as a documentation starter kit:
- Duplicate the folder for your own projects  
- Use the structure and templates as your baseline  
- Integrate real generators like **MkDocs**, **Jinja**, or **Sphinx** later

---

## ✅ 5. Commit and Share

Once customized:
1. Update the README and changelog.  
2. Push to GitHub.  
3. Share your new repository as your own documentation system example!

---

> **Tip:** Treat DocWeaver as both a learning tool and a starting point for building documentation infrastructure.

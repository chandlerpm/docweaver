# Common Errors

This page lists common issues you may encounter while working with **DocWeaver**, along with their causes, solutions, and prevention tips.  
It’s meant as a quick troubleshooting guide for documentation authors and contributors.

---

## 🧩 Overview

Errors in DocWeaver projects generally fall into three categories:

| Category | Description | Typical Symptoms |
|-----------|--------------|------------------|
| **Linking** | Incorrect relative paths or missing files | Dead links, 404s in CI |
| **Linting** | Violations of Markdown style rules | Red ❌ in Docs Quality Check |
| **Variable Rendering** | Unreplaced `{{ variable }}` placeholders | Raw curly braces visible in output |

---

## 🔗 Linking Errors

### **Symptom**
```
[✖] ../examples/sample-readme.md → Status: 400
```

### **Cause**
The linked file doesn’t exist at the path given, or the relative path is incorrect.

### **Fix**
- Confirm that the target file exists in the repo.  
- Adjust the link based on file location:  
  - From `README.md` (root): `examples/sample-readme.md`  
  - From inside `docs/guides/`: `../../examples/sample-readme.md`

### **Prevention**
- Use relative links only (avoid absolute paths).  
- Run the **Docs Quality Check** workflow after each commit.  
- Avoid renaming or moving folders without updating all references.

---

## 🧱 Linting Errors

### **Symptom**
```
MD041/first-line-heading: First line in file should be a top-level heading
```

### **Cause**
Markdownlint found a formatting rule violation.

### **Fix**
- Follow the rule noted in the CI logs.  
- For this example, add a level-1 heading (`# Title`) at the top of the file.

### **Prevention**
- Keep a local Markdownlint plugin in VS Code for real-time feedback.  
- Review the project’s `.markdownlint.json` to understand enforced rules.  
- Commit frequently and let CI confirm your formatting.

---

## 🧶 Variable Errors

### **Symptom**
`{{ variable_name }}` appears visibly in a rendered file.

### **Causes**
- The variable isn’t defined in `config.yml`.  
- YAML formatting is invalid.  
- Template syntax has an extra space or curly brace.

### **Fix**
- Verify that the variable exists and matches the template spelling.  
- Ensure YAML spacing is correct (2 spaces per level).  
- Remove stray spaces inside the curly braces:  
  ✅ `{{ variable_name }}`  
  ❌ `{{  variable_name  }}`

### **Prevention**
- Keep all shared metadata in `config.yml`.  
- Run template rendering locally before committing.  
- Add variable definitions incrementally instead of en masse.

---

## ⚙️ CI / Workflow Failures

### **Symptom**
“Docs Quality Check” badge shows **No Status** or **Failed**.

### **Common Causes**
| Cause | Description |
|--------|-------------|
| Workflow name mismatch | File renamed (e.g., `docs.lint.yml` vs. `docs-lint.yml`) |
| Permissions error | Workflow token missing or expired |
| Path issue | `.github/workflows/` folder missing |
| Missing dependencies | Node modules not installed in job |

### **Fix**
1. Ensure the workflow file is named correctly:  
   `.github/workflows/docs-lint.yml`
2. Verify this header is present:
   ```yaml
   name: Docs Quality Check
   on:
     push:
       branches: [main]
     pull_request:
       branches: [main]
   ```
3. Re-run the workflow manually in **Actions → Rerun jobs**.

### **Prevention**
- Don’t rename workflow files after setup.  
- Commit workflows with lowercase, hyphenated filenames.  
- Keep minimal, consistent YAML indentation.

---

## 🧰 Git Sync Issues

### **Symptom**
```
! [rejected] main -> main (fetch first)
```

### **Cause**
Remote changes exist that aren’t in your local branch.

### **Fix**
```bash
git pull origin main --rebase
git push
```

### **Prevention**
- Always pull before starting a new edit session.  
- Avoid force-pushes unless cleaning history intentionally.  
- Use `git push --force-with-lease` instead of plain `--force` when rewriting commits.

---

## 🪄 Mermaid Rendering Problems

### **Symptom**
Raw diagram code displays instead of a chart.

### **Causes**
- Code fence missing `mermaid` language tag.  
- Syntax indentation broken inside code block.  
- Using unsupported syntax (e.g., `graph TD` with typos).

### **Fix**
- Ensure code block begins with triple backticks and `mermaid`:
  ```
  ```mermaid
  flowchart LR
      A --> B
  ```
  ```
- Remove extra leading spaces in diagram lines.

### **Prevention**
- Test Mermaid syntax using [Mermaid Live Editor](https://mermaid.live).  
- Keep diagrams simple—avoid deep nesting or overlapping arrows.

---

## 📁 Missing Folder Errors

### **Symptom**
CI reports:
```
ENOENT: no such file or directory, access '/github/workspace/examples'
```

### **Cause**
GitHub Action cannot locate the folder (e.g., `examples/` missing or nested incorrectly).

### **Fix**
- Move `examples/` to the repository root.  
- Verify correct capitalization (`examples/`, not `Examples/`).  
- Add a `.gitkeep` if the folder is empty.

### **Prevention**
- Maintain a consistent, flat directory layout.  
- Check the repository tree before commits.  
- Avoid creating duplicate subfolders with case differences.

---

## 🧾 Markdown Table Formatting

### **Symptom**
Tables render misaligned or fail to display borders.

### **Cause**
- Missing pipe (`|`) characters or uneven spacing.  
- Incorrect line breaks between header and body.

### **Fix**
```
| Column | Description |
|--------|--------------|
| A | Item A |
| B | Item B |
```

### **Prevention**
- Always include a separator row of dashes.  
- Use a Markdown table formatter (VS Code plugin: “Markdown All in One”).  

---

## 🧠 Summary

| Error Type | Common Cause | Quick Fix |
|-------------|---------------|------------|
| Dead links | Wrong relative paths | Adjust link depth |
| Lint failure | Markdown rule violation | Follow `.markdownlint.json` |
| Unresolved variables | Missing config entry | Add variable to `config.yml` |
| Mermaid not rendering | Wrong code fence | Use ```mermaid |
| Git sync error | Remote ahead of local | `git pull --rebase` |
| Missing folders | Directory renamed or moved | Confirm structure |

---

> Every error is an opportunity to refine your process. DocWeaver’s strength lies in its structure—when something breaks, the fix almost always reinforces consistency.

---

_See also: [FAQ](faq.md)_
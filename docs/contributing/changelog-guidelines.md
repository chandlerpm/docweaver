# Changelog Guidelines

**DocWeaver** follows the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format and uses [Semantic Versioning](https://semver.org/) for releases.  
This guide explains how to write clear changelog entries and maintain version discipline for a documentation-focused project.

---

## 🗂️ File Location

The changelog lives at the repository root as `CHANGELOG.md`.

---

## 🧭 Structure and Order

Each version entry includes these headings, in this order:

- **Added** – new pages, sections, or examples  
- **Changed** – reorganized content, revised diagrams, or improved explanations  
- **Fixed** – typos, broken links, rendering issues  
- **Deprecated** – discouraged content slated for removal  
- **Removed** – pages or sections fully removed  
- **Security** – notes related to vulnerabilities (rare for this project)

Example section:

```markdown
## [0.3.1] – 2025-11-02
### Added
- Docs: IA diagram on docs index
### Fixed
- README: correct examples links
```

Keep entries short and clear. Each bullet should describe one meaningful change.

---

## 🧱 Unreleased Section

Keep a section at the top of the file to track changes that haven’t been released yet:

```markdown
## [Unreleased]
### Added
- Docs: example branching and changelog guideline pages
### Fixed
- Broken relative links in README
```

When publishing a release, move these items under a new version heading and add a date.

---

## 🏷️ Version Headings

Use this format for each release:

```
## [x.y.z] – YYYY-MM-DD
```

- Use **semantic versioning**:
  - **MAJOR** – breaking structural or process changes  
  - **MINOR** – new pages, workflows, or major additions  
  - **PATCH** – small fixes, typos, link corrections
- Example:
  ```
  ## [0.3.0] – 2025-11-02
  ```

For portfolio releases, minor bumps are typical; patch versions are for corrections.

---

## ✍️ Writing Good Entries

- Be specific and action-oriented:  
  ✅ `Fixed broken link to /examples/sample-readme.md`  
  ✅ `Added Mermaid diagram for docs workflow`  
  ❌ `Updated docs`  
  ❌ `Minor edits`

- Reference PR numbers if available:  
  `Added: Contributing section for branching (#42)`

- Avoid internal shorthand or commit hashes.

---

## 🪶 Example Entry

```markdown
## [0.3.0] – 2025-11-02
### Added
- Complete documentation suite (overview, guides, reference, troubleshooting, contributing)
- CI workflow: markdownlint + link-check with badges
### Changed
- README reorganized with new badges and workflow diagram
### Fixed
- Examples links corrected and verified by CI
```

---

## 🚀 Release Workflow

1. Ensure CI (Docs Quality Check) passes.
2. Finalize `CHANGELOG.md`:
   - Move `[Unreleased]` items under a new version heading with today’s date.
3. Commit:
   ```bash
   git add CHANGELOG.md
   git commit -m "chore(release): prepare v0.3.1 changelog"
   ```
4. Tag and push:
   ```bash
   git tag -a v0.3.1 -m "v0.3.1 – changelog + docs polish"
   git push origin v0.3.1
   ```
5. (Optional) Create a GitHub Release and paste the new changelog section as release notes.

---

## ❓ FAQ

**Q: Should small typo fixes be logged?**  
A: Yes, if they affect published docs or examples. Group them under **Fixed**.

**Q: What about multiple small PRs toward one feature?**  
A: Summarize them as a single bullet describing the final visible outcome.

**Q: Should I include compare links?**  
A: Optional. For a portfolio project, clarity is preferred over clutter. Include links only if they add context.

---

> A consistent changelog is an extension of your documentation quality—it proves you document your documentation.

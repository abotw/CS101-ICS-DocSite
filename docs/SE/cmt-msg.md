---
title: Commit Message
date: 2025-11-11T11:08:00
---

# 🧾 Practical Guide: Writing Good Commit Messages for Doc Sites

---

## 💡 1. General Principles

**Good commit messages should:**

1. Explain **what changed** and **why**
    
2. Use the **imperative mood** (“Add”, “Fix”, “Update”)
    
3. Optionally include a **scope** in parentheses:
    
    - `docs(site)`, `feat(navbar)`, `fix(link)`
        
4. Be **short but meaningful** (50 chars for title, optional longer body)
    
5. Group related commits logically — avoid “misc changes”
    

**Example format:**

```
<type>(<scope>): <short summary>

<body explaining the change and reason, optional>
```

---

## 🧩 2. Common Commit Types (for doc sites)

|Type|Meaning|Example|
|---|---|---|
|**docs**|Documentation or content changes|`docs(readme): add setup guide for macOS`|
|**feat**|Add a new feature to the site or tooling|`feat(search): enable full-text search with Lunr.js`|
|**fix**|Correct a bug or broken link|`fix(nav): correct sidebar link for "Getting Started"`|
|**style**|Formatting, spacing, or style change (no content change)|`style(css): adjust font size for code blocks`|
|**refactor**|Reorganize structure without changing content|`refactor(docs): move Python tutorials into /python/ folder`|
|**chore**|Maintenance tasks|`chore: update mkdocs-material to v9.5.0`|
|**ci**|CI/CD configuration|`ci: fix GitHub Pages deploy workflow`|
|**build**|Build system or tooling|`build: add script to auto-generate sitemap`|

---

## 🧠 3. Practical Examples (by scenario)

### 📄 A. Updating Content

You’re adding or revising documentation pages.

```bash
docs(python-env): add section on virtual environments
docs(opencv): rewrite introduction and add examples
docs(ai101): clarify explanation of neural networks
docs(ics): update course list and fix broken references
```

👉 _Tip:_ Always mention **which topic or file** you changed.

---

### 🎨 B. Improving Site Layout or Styling

```bash
style(theme): adjust heading colors for better contrast
style(navbar): fix alignment on mobile
refactor(layout): move footer component to base.html
feat(ui): add dark mode toggle button
```

👉 _Tip:_ These commits affect **appearance** or **HTML/CSS structure**.

---

### ⚙️ C. Tooling and Build System

```bash
chore(deps): bump mkdocs-material to 9.4.14
build(script): add auto-deploy to GitHub Pages
ci: add build check for broken links
chore: remove unused plugin `mkdocs-minify-plugin`
```

👉 _Tip:_ Use these for **configuration**, **CI/CD**, or **dependencies**.

---

### 🧭 D. Fixing Errors or Links

```bash
fix(link): correct typo in Python tutorial URL
fix(image): update broken image path in OpenCV doc
fix(yaml): correct site_nav indentation in mkdocs.yml
```

👉 _Tip:_ Use `fix()` when the change repairs something broken.

---

### 📚 E. Structural or Organizational Changes

```bash
refactor(structure): reorganize docs by topic
refactor(nav): simplify sidebar structure
refactor(project): merge AI101 and CS101 doc folders
```

👉 _Tip:_ Use `refactor()` when reorganizing without changing meaning.

---

### 🧰 F. Meta and Configuration Files

```bash
docs(readme): add instructions for local preview
chore(.gitignore): ignore .DS_Store and build output
chore(config): update site_name and copyright
```

👉 _Tip:_ Keep commit messages about config clean and focused.

---

### 🧪 G. Experiments and Temporary Updates

```bash
feat(experiment): test new plugin for syntax highlighting
docs(test): add placeholder section for new feature
```

👉 _Tip:_ For experiments, make it clear that it’s _temporary or testing_.

---

## 📘 4. Example Commit History (Good Practice)

```
feat(navbar): add dropdown menu for course selection
docs(ics): add CPU and memory hierarchy overview
fix(link): correct reference in digital logic section
style(theme): unify heading levels and spacing
refactor(structure): split AI101 docs into subfolders
chore(deps): update mkdocs-material to 9.4.15
ci: enable auto-deploy on push to main
```

👉 This kind of history is:

- **Readable**
    
- **Chronological**
    
- **Meaningful**
    
- Easy to **filter** (you can run `git log --grep=docs` to see doc-related commits)
    

---

## 🧾 5. Writing Multi-line Commit Messages

When a change is significant, use a longer message:

```
docs(python-env): expand environment setup guide

Added sections on:
- Installing Python via Homebrew
- Managing multiple versions with pyenv
- Creating and activating virtual environments

Also corrected typos and improved formatting.
```

👉 _Why:_ The body explains the context, so future you (or collaborators) can understand the reasoning behind the change.

---

## 🔐 6. Bonus Tips for Maintaining Clean History

- Use `git add -p` to stage changes selectively
    
- Use `git commit --amend` to fix the last commit instead of making a new one
    
- Use `git rebase -i` to squash small commits before merging
    
- Write commits **as if explaining to your future self**
    

---

## 🧭 7. Template (You Can Copy This)

```
<type>(<scope>): <short summary>

[optional body]
- Explain what changed
- Explain why it changed
- Add context if helpful
```

**Example:**

```
docs(opencv): add section on cv2.imread() and cv2.imshow()

Expanded OpenCV introduction with two new examples showing
how to read and display images in Python. This improves the
clarity for beginners using Homebrew-installed Python.
```

---

## 🪄 8. Suggested Commit Scopes for Your Doc Sites

|Project|Example Scopes|
|---|---|
|**AI101**|intro, ai-basics, vision, nlp, project-setup|
|**CS101-ICS**|cpu, io, memory, assembly, linux|
|**Doc-Sol**|office, iworks, markdown, latex, comparison|
|**General**|theme, site, config, nav, readme|

Use consistent scopes to help future searches and automated changelogs.

---

### ✅ Final Tip

> Think of each commit as a **micro blog post** that documents your project’s evolution.  
> A year later, good commit messages will read like a **clear timeline** of your learning and progress.

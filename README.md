# Line Ending Standardization (CRLF → LF)

This project enforces **LF (Line Feed)** line endings to ensure consistency across all environments (Linux servers, Docker containers, CI/CD pipelines, etc.).  
By default, Windows may use **CRLF (Carriage Return + Line Feed)**, which can cause unnecessary diffs in Git and break scripts.

---

## 1. Editor Configuration

Create a file named `.editorconfig` at the root of the project:

```ini
root = true

[*]
end_of_line = lf
charset = utf-8
insert_final_newline = true

## 2. Git Configuration

To prevent Git from committing files with CRLF endings:

---

# Configure for current project
git config core.autocrlf input

---

# Or configure globally (recommended)
git config --global core.autocrlf input

---

Normalize existing files in the repository:

git rm --cached -r .
git reset --hard

This will re-checkout files with LF endings.

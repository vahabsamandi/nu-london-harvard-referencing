# Contributing

Thank you for helping improve the NU London Harvard referencing style.

## Report an issue

Open a GitHub Issue and include:

- The entry type (for example `@book`, `@misc`, `@report`) and the smallest `.bib` entry that demonstrates the problem.
- The expected output and actual output (screenshot or text).
- The page/section of the July 2025 NU London referencing guide that supports the expected format.
- Your TeX setup, if relevant (Overleaf, BibLaTeX, Biber).

Do not publish personal correspondence or identifying student information.

## Propose a change

1. Fork the repository and create a branch such as `fix/proquest-format`.
2. Make the smallest change needed in the `.bbx`, `.cbx`, or HTML helper.
3. If possible, add a sample entry to `tests/references.bib` and compile `tests/main.tex` with Biber.
4. Open a Pull Request explaining what changed and why.

Updates are reviewed before merging; suggestions do not automatically become university policy.
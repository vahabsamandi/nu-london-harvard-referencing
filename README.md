# NU London Harvard Referencing for BibLaTeX

**Author and maintainer:** [Vahab Samandi](https://github.com/vahabsamandi)

An **unofficial** BibLaTeX/Biber author–date style based on Northeastern University London's *Apprenticeship Guide to Harvard Referencing* (July 2025), accompanied by an offline HTML reference generator.

> **Not an official university release.** Check all entries and output against the university referencing guide before submission. The source guide is not bundled in this repository.

## Files to download

| File | Purpose |
| --- | --- |
| `nulondon-harvard.bbx` | Formats the bibliography |
| `nulondon-harvard.cbx` | Formats in-text citations |
| `references.bib` | Sample source entries; replace these with your own, or retain your existing `.bib` |
| `Harvard_Reference_Helper.html` | Offline form to prepare BibLaTeX for less common sources |

## Add the style to an existing Overleaf project

1. On GitHub choose **Code → Download ZIP** and extract the archive.
2. Upload **`nulondon-harvard.bbx`** and **`nulondon-harvard.cbx`** to the same directory as your main `.tex` file.
3. Create a `references.bib` file, or upload the provided example. **Do not overwrite a `.bib` file that already contains your references.**
4. Add the following to your LaTeX preamble (before `\begin{document}`):

```latex
\usepackage[british]{babel}
\usepackage{csquotes}
\usepackage{xurl}
\usepackage[
    backend=biber,
    style=nulondon-harvard,
    sortcites=true
]{biblatex}
\addbibresource{references.bib}
```

5. Cite sources using `\parencite{yourkey}` for **(Author, Year)** or `\textcite{yourkey}` for **Author (Year)**.
6. Before `\end{document}`, add:

```latex
\clearpage
\printbibliography[title={References}]
```

7. Recompile in Overleaf. If entries do not appear, check your citation keys and use **Recompile from scratch**.

**Compatibility:** This package uses **BibLaTeX with Biber**, not traditional BibTeX `.bst`/`natbib`. If your project already loads another bibliography framework, remove conflicting configuration.

## How to get `.bib` entries

For standard journal articles, conference papers and books, first try **Google Scholar → Cite → BibTeX** or **ZoteroBib**. Check all metadata. For less common sources (YouTube, films, government reports, white papers, etc.), or when it is difficult to obtain a working BibTeX entry, open `Harvard_Reference_Helper.html` locally in your web browser. Select the type, **manually enter the correct details**, then copy the generated BibLaTeX entry into `references.bib`. The generator does **not** fetch or verify metadata.

## Special cases

### Corporate / organisation authors

Use **double braces** to prevent the organisation being parsed as a person's name:

```bibtex
@book{apm2025,
  author    = {{Association for Project Management}},
  date      = {2025},
  title     = {{APM} body of knowledge},
  edition   = {8},
  publisher = {Association for Project Management}
}
```

### YouTube video

```bibtex
@misc{economist2022,
  entrysubtype = {youtube},
  author       = {{The Economist}},
  date         = {2022},
  title        = {How will businesses use the metaverse?},
  organization = {{YouTube}},
  url          = {https://www.youtube.com/watch?v=LEgHRAQ1HmE},
  urldate      = {2022-12-03}
}
```

Use your **actual** access date. Verify video metadata directly with the publisher.

### Government white paper

```bibtex
@report{moj2021,
  entrysubtype = {whitepaper},
  author       = {{Ministry of Justice}},
  date         = {2021-12-07},
  title        = {Prisons Strategy White Paper},
  number       = {CP 581},
  institution  = {{UK Government}},
  url          = {https://www.gov.uk/government/publications/prisons-strategy-white-paper},
  urldate      = {2026-10-28}
}
```

**Note:** CP 581 is the 2021 white paper; CP 686 identifies a separate 2022 consultation response. Check the correct source and enter your actual access date.

### ProQuest e-books

For an e-book downloaded from ProQuest, use `entrysubtype = {ebook}` and add `keywords = {proquest}`. The bibliography will use **Retrieved from https://ebookcentral.proquest.com/** instead of the usual **Available at:** line.

```bibtex
@book{sampleProquest,
  author       = {Example, Ann},
  date         = {2020},
  title        = {An example e-book title},
  publisher    = {Example Press},
  entrysubtype = {ebook},
  keywords     = {proquest},
  urldate      = {2026-10-28}
}
```

*This last citation is fictional, for demonstrating fields only.*

## Contributing

Found a formatting discrepancy or have a suggestion? Please **open a GitHub Issue**, or fork the repo and submit a **Pull Request**. See [CONTRIBUTING.md](CONTRIBUTING.md).

Include your `.bib` entry, the relevant university-guide rule/page, and expected versus actual output. Please do not upload private student work.

## Development and known limitations

- The style follows common cases in the July 2025 guide and has example categories for specialist sources; exact output may vary for edge cases and unusual combinations of fields.
- *et al.* is italicised per the guide; four or more named authors are shortened to first author + *et al.* in citations and bibliography.
- Bibliography entries are sorted alphabetically; cited works are printed by default (avoid `\nocite{*}` unless intended).
- The example `references.bib` contains teaching/reference samples rather than a fully verified database; validate before reusing.
- A licensing decision has not yet been made by the repository owner. No open-source licence is included at this stage.

See `tests/` for a small LaTeX/Biber smoke test.
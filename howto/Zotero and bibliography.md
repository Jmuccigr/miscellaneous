---
title: Zotero + Pandoc
author: John D. Muccigrosso
date: 27 February 2017
---

# Adding Bibliography to markdown

## Start with Zotero

- Export your library to a text file from Zotero.
    -  Right click on your library and chose `Export Library...` or...
    -  Select your library and choose `Export Library...` from the File menu.
    -  Choose your preferred format.
    -  Give it a name without spaces.
    -  Remember where you saved the file.

## Include citations in your paper

- When you have a paper you want to cite, read its Citation Key from Zotero.
- Prefix `@` to the key and enclose it in square brackets to use it: `[@Mellor2005]`

## Tell pandoc about it

pandoc will read your bibliography file and turn your ugly citations into well formatted text and notes. Just add a flag to your command:

- `pandoc --bibliography="/path/to/file"`

. . .

Really it's using a filter called `pandoc-citeproc`, but when you use the `--bibliography` flag, pandoc automatically applies the filter.

## Change the citation style

By default pandoc uses the Chicago Manual of Style format. If you need another one:

- Get the style via Zotero's preferences:
    - On the Cite pane, choose the Styles tab and click on "Get additional styles..."
    - Search for and download the one you want.
    - Go back to Zotero and click on the `+` button to find that file that was just downloaded and have Zotero store it in its data folder.
- Tell pandoc to use that style: `pandoc --csl=/path/to/file.csl`

## In your paper

Depending on the style you choose, pandoc will insert your citation in-line, like this, `(Mellor 2005)`, or as a footnote.

. . .

pandoc will also insert a bibliography at the end of your document, so if you put a header at the end, it will follow that header:

```
## Works cited

[End of markdown file. pandoc-inserted bibliography will be inserted here.]
```

## Useful stuff

- [Better BibTeX](https://github.com/retorquere/zotero-better-bibtex/wiki/Installation) is a utility for Zotero. It can:

    - automate bibliography export
    - export better bibliography files
    - make easier-to-remember citation keys

- Zotero has a wiki with info on [citation styles](https://www.zotero.org/support/styles), among other things.

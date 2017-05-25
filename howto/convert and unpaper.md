---
title: convert & unpaper
author: John D. Muccigrosso
date: 3 May 2017
---

# Using convert & unpaper on PDFs

## convert

- Convert the PDF to pgm.
    -  Use the convert_pdf.sh script to maintain correct dpi.
    -  Use `-depth 8` to create pgm that unpaper can read.

## unpaper

- Split double-layout pages with `--layout double --output-pages 2`.
- Create multiple documents for multi-page input: `filename-%02d.pgm` where the 2 indicates the number of digits in the output filenames.

## img2pdf

- Create a pdf from images (like those produced by convert and unpaper) to give to ocrmypdf: `img2pdf files*.pgm | ocrmypdf - output.pdf`

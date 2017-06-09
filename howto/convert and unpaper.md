---
title: convert & unpaper
author: John D. Muccigrosso
date: 3 May 2017
---

# Using convert & unpaper on PDFs

Rather than using one of the packages to handle scanned documents, it can be done in pieces (which could be scripted together, of course)

1. Convert the PDF to images
    - `convert`
        -  Use the convert_pdf.sh script to maintain correct dpi.
        -  Use `-depth 8` to create pgm that unpaper can read.
        - Create multiple documents for multi-page input: `filename-%02d.pgm` where the 2 indicates the number of digits in the output filenames.
        -  `-despeckle` and `-deskew` are good options, if needed
1. Clean up scan
    - Use `unpaper` though several options don't seem to work, so it mainly servers to split double-layout pages with `--layout double --output-pages 2`.
       - **NB**: unpaper doesn't see files where the numbering starts at `00`, but instead it starts looking at `01`.
   - Clean up margins manually, or where possible using:
        - `convert -gravity SIDE -chop 0x100 -splice SIDE 0x100 input output`
   - Trim and put text area onto a clean background:
       - Create bg file: `convert -size 1600x2300 xc:#ffffff white.pgm`
       - Trim existing: `convert -white-threshold 99.9% -trim +repage input.pgm output.pgm`
       - Create new doc: `convert white.pgm trimmed.pgm -gravity center -composite output.pgm`
   - Tips
       - `unpaper --layout double` will center and deskew the separate sheets somewhat, while keeping them on the same output page, which can make it easier for it to subsequently split them into two output pages, so use two steps instead of one, if this is a problem.
1. Back to PDF
    1. `img2pdf` and `ocrmypdf`
        - Create a pdf from images (like those produced by convert and unpaper) to give to ocrmypdf: `img2pdf files*.pgm | ocrmypdf - output.pdf`
    1. `tesseract` can also do this itself, though it's currently converting pgm to jpeg, so
        - Convert to png first (converting dpi if needed): `convert -units PixelsPerInch input.pgm -density 150 output.png`
        - `ls *.png | xargs -I {} tesseract {} {} pdf`
        - Use `pdfunite` to combine resultant files into single pdf

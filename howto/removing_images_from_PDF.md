---
title: Method for removing images from a PDF
author: John D. Muccigrosso
---

## Ghostscript

This method relies on gs to remove different kinds of images in a PDF file. You have three options, which can be combined:

1. -dFILTERIMAGE: produces an output where all raster images are removed.
1. -dFILTERTEXT: produces an output where all text elements are removed.
1. -dFILTERVECTOR: produces an output where all vector drawings are removed

Replace "-option" in the following command with any of the three (or a combination of them) that you prefer. For example, to get rid of raster images:

```
gs -o output.pdf -sDEVICE=pdfwrite -option input.pdf
```


- This approach can be found [here](https://askubuntu.com/questions/477663/how-to-remove-images-from-a-pdf-file).

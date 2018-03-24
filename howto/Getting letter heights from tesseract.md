---
title: Getting letter heights from tesseract
author: John D. Muccigrosso
date: 22 October 2017
---

Tesseract's makebox option will process an image, outputting one line per character.

1. Get bbox for each character  
  `tesseract text_image_file output_file_name makebox`

1. Process output to get letter height, where `$a` contains a line of the makebox output (e.g., `C 261 2453 285 2480 0`)  
  ```echo `expr ${a[4]} - ${a[2]}` ```

1. Get letter heights  
  ```echo `expr ${a[4]} - ${a[2]}` ```

1. Read heights into an array.

1. Sort the array.

1. Grab middle value of array.

1. Scale image by enough to make median letter height at least 20 px.

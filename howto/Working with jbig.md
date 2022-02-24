---
title: Working with jbig files
date:  2022-02-19
author: John D. Muccigrosso
...

## Converting from jbig

`jbig2enc` generally does the job

- For .jb2e use jbig2dec: `jbig2dec -o outputfile.ext filename.jb2g filename.jb2e`
    - if there is no .jp2g file, use `/dev/null`

## Converting to jbig

`jbig2 -s filename.tif > outputfile.jb2`

## Put everything right into a PDF

`jbig2 -b output_basename -d -p -s input_files; PDF.py output_basename > output.pdf`

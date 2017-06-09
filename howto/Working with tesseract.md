---
title: Working with tesseract
author: John D. Muccigrosso
---

- When tesseract is updated (via homebrew), make sure to
    1. Update the `TESSDATA_PREFIX` env variable to be the directory that **contains** the `tessdata` directory. A new version number will break this.
    1. Symlink all the files from the github install of the `tessdata` repo into the tessdata directory inside the homebrew tesseract install.

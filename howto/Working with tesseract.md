---
title: Working with tesseract
author: John D. Muccigrosso
---

- When tesseract is updated (via homebrew), make sure to
    1. Update the `TESSDATA_PREFIX` env variable to be the directory that **contains** the `tessdata` directory. A new version number will break this.
    1. Symlink all the files from the github install of the `tessdata` repo into the tessdata directory inside the homebrew tesseract install: `ln -s -i Documents/github/local/tessdata/*.traineddata $TESSDATA_PREFIX`
- To install version 3 instead of 4 ([This](https://danepowell.com/blog/homebrew-formula-versions) was helpful.):
        - Unlink the newer version, if installed: `brew unlink tesseract`
        - Find the commit and its raw link and install it directly: `brew install https://github.com/Homebrew/homebrew-core/raw/5df6eb919506a097b2efb1df34a16e3a147c8731/Formula/tesseract.rb`
        - `brew list --versions` to see that both versions are installed
        - `brew pin tesseract` will prevent updates
        - Get 3.04-tagged branch of tessdata since new training data won't work; copy it into the 3.05 tessdata dir

---
title: Adding Metadata to your markdown
author: John D. Muccigrosso
date: 27 February 2017
---

# Metadata

## Data about stuff

There's a lot of data that's used to describe things:

- Author
- Title
- Date

. . .

It's called **metadata** ("data *about* data")

-----

In academic papers a lot of this information is usually simply written in at the top (or bottom). This is how you've been adding it to your papers so far:

. . .

```
Jane Roe

CLAS-260

27 February 2017

# Title of my paper

Lorem ipsum *dolor* sit amet, consectetur adipisicing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis 
nostrud exercitation ullamco laboris nisi ut **aliquip** ex ea commodo consequat. 
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore 
eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, 
sunt in culpa qui officia deserunt mollit anim id est laborum.
```

# Metadata in markdown

## YAML

- We're going to put the metadata in a special section at the start of the document.
- It's a fairly simple system, called *YAML*, in which the data are introduced by keys followed by a colon. Multiple values for one key can appear as a markdown list

. . .

```
---
title: Catchy paper title
author:
- Jane Roe
- John Doe
date: 27 February 2017
---
```

-----
 
pandoc will insert this metadata into your document

![Word doc with metadata automatically inserted.](/Users/john_muccigrosso/Dropbox/Screenshots/word_yaml.jpg)

# Pandoc-specific metadata

## Bibliography

Your bibliography file is another kind of metadata that you can add to a file:

. . .

```
---
title: Catchy paper title
author: Jane Roe
date: 27 February 2017
bibliography: "/home/jmuccigr/pandoc/muccigrosso/My Library.json"
---
```

-----

So is your citation style:

```
---
title: Catchy paper title
author: Jane Roe
date: 27 February 2017
bibliography: "/home/jmuccigr/pandoc/muccigrosso/My Library.json"
csl: /home/jmuccigr/pandoc/styles/modern-language-association.csl
---
```

. . .

If you do add this data to your YAML, make sure to tell pandoc to process the citations with the `--filter pandoc-citeproc` flag.

(Using `--bibliography=/file/name` on the command line invokes citeproc automatically.)

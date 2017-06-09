---
title: Jekyll pages
date: 25 May 2017
---

## Using Jekyll locally

- Local set up through gem; mirror to github
- Info
	- [Jekyll docs](https://jekyllrb.com/docs)
	- [GitHub tutorial](http://jmcglone.com/guides/github-pages/) (watch out for layouts)
	- [GitHub info pages](https://help.github.com/categories/github-pages-basics/)
- CLI
	- launch by going to directory and exectuing `bundle exec jekyll start [--detach]`
    	- Now aliased to `sj` ("start jekyll"), `kj` ("kill") for detached version.
- Themes
	- Check for [github.io-available gem-installed themes](https://pages.github.com/themes/)
    	- Add to file "Gemfile" in site dir: `gem "<themename>"`
    	- `bundle install` to install it
- Tips
    - Make sure all .md files have a YAML header or jekyll won't generate html from them.
    - [gems supported by github](https://pages.github.com/versions/)
    - If there are layout templates, makes sure that they include the necessary header material (e.g., css) for the them.

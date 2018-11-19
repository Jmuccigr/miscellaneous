---
title: Jekyll pages
date: 9 June 2017
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
	- RTFM! For example, css can often be included in a file in `/assets`.
- Custom 404
    - <https://hendrixjoseph.github.io/the_elusive_custom_github_404_page/>
- Tips
    - Make sure all .md files have a YAML header or jekyll won't generate html from them.
    - [gems supported by github](https://pages.github.com/versions/)
    - If there are layout templates, makes sure that they include the necessary header material (e.g., css) for the them.
- Updating
    - [Useful](https://jekyllrb.com/docs/upgrading/)
    - Update Jekyll with `bundle update jekyll`
    - Better: update all the gems with `bundle update`. [NB](https://bundler.io/v1.7/rationale.html#checking-your-code-into-version-control) "This will resolve dependencies from scratch, ignoring the Gemfile.lock."
    - Gemfile and Gemfile.lock may limit the version the update will go to. I've been matching the version of Jekyll that GitHub uses.

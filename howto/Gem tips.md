---
title: Gem tips
author: John D. Muccigrosso
date: Saturday, 24 March 2018
---

- To run geocollider: be in geocollider folder, then `bundle exec` desired .rb file in bin directory
    - `~/.rbenv/versions/2.5.0/lib/ruby/gems/2.5.0/bundler/gems/geocollider-something/`
    - Alternatively had to add these lines to the script and then `bundle update` to run via basic command:  
        `require 'rubygems'`  
        `require 'bundler/setup'`

- For the local Jekyll installation that mimics my personal github.io website, keep it updated by navigating to it at `/Users/john_muccigrosso/Documents/github/local/jmuccigr.github.io` and running `bundle update`.

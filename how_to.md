# How-to's

A collection of useful instructions.

## JSON

### CLI commands

- Where is this?
	- json_pp

- gem
	- json2csv
	- csv2json
	- ppjson [prettifies]

- npm
	- geojsonhint [validates]; `geojsonhint < file.geojson`

- brew
	- jq; [tutorial](http://programminghistorian.github.io/ph-submissions/lessons/json-and-jq.html)
	- quicklook-json: linked to Library/QuickLook
	- YAJL, which includes
		- json_reformat
		- json_verify

- python
	- `python -mjson.tool` [prettifies]

## Base maps

- MapBox
	- attibution: `Map data &copy; <a href="http://openstreetmap.org">OpenStreetMap</a> contributors, <a href="http://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="http://mapbox.com">Mapbox</a>`
	- URL: `https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token=` + token
	- ID: `mapbox.light`, `mapbox.dark`, `mapbox.streets`, `mapbox.outdoors`, `mapbox.satellite`
	- info: <https://www.mapbox.com/maps/>

- DARE
	- var attibution: `Powered by <a href="http://leafletjs.com/">Leaflet</a>. Map base: <a href="http://dare.ht.lu.se/" title="Digital Atlas of the Roman Empire, Department of Archaeology and Ancient History, Lund University, Sweden">DARE</a>, 2015 (cc-by-sa).`
	- URL: `http://dare.ht.lu.se/tiles/imperium/{z}/{x}/{y}.png'`
	- maxZoom: `11`

- AWMC
	- attibution: `Powered by <a href="http://leafletjs.com/">Leaflet</a> and <a href="https://www.mapbox.com/">Mapbox</a>. Map base by <a title="Ancient World Mapping Center (UNC-CH)" href="http://awmc.unc.edu">AWMC</a>, 2014 (cc-by-nc).`
	- URL: `https://api.tiles.mapbox.com/v4/isawnyu.map-knmctlkh/{z}/{x}/{y}.png?access_token=` + token
	- maxZoom: `12`
	- base map id: isawnyu.map-knmctlkh
	- info: <http://awmc.unc.edu/wordpress/tiles/map-tile-information>

- OpenStreetMap
	- Attribution: `OpenStreetMap`
	- URL: `http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png`

- Stamen
	- ID: `terrain`, `toner`, `watercolor`
	- maxZoom: 20 for `toner`
	- note: Import script `src="http://maps.stamen.com/js/tile.stamen.js?v1.3.0"`, then `new L.StamenTileLayer("ID")`
	- info: <http://maps.stamen.com/>
- Google
	- <https://gitlab.com/IvanSanchez/Leaflet.GridLayer.GoogleMutant#README>


## pandoc

- pip
    - pandocfilters
    - pandoc-fignos

- npm
    - pandoc-mermaid-filter

### Jekyll pages

- Local set up through gem
- Info
	- [Jekyll docs](https://jekyllrb.com/docs)
	- [GitHub tutorial](http://jmcglone.com/guides/github-pages/) (watch out for layouts)
	- [GitHub info pages](https://help.github.com/categories/github-pages-basics/)
- If there are layout templates, makes sure that they include the necessary header material (e.g., css) for the them.
- CLI
	- launch by going to directory and: `bundle exec jekyll start [--detach]`
- Themes
	- Add to Gemfile in site dir: `gem "<themename>"`

## MAMP, Apache, & php

- [Use files without php extension](http://wettone.com/code/clean-urls) (= clean URIs) via Apache's `mod_rewrite`
	1. Add regex rewrite rules according to link above.
	1. Make sure that in /Applications/MAMP/conf/apache/httpd.conf, find:
	
		```
		<Directory />
		    Options Indexes FollowSymLinks
		    AllowOverride ~None~ All
		</Directory>
		```
- Change log to usual place, which will show up in console.app
	- `ErrorLog "/Users/john_muccigrosso/Library/Logs/apache_error.log"`

## Other

- npm
    - mermaid
- rbenv (itself installed homebrew)
	- ruby
- manually
	- [pdfsandwich](http://www.tobias-elze.de/pdfsandwich/)
		- Required
			- pdfunite from poppler (installed via homebrew)
			- txt2man (via homebrew)

### For updating

- upall
	- aliased command in .bash_profile
	- performs updates for brew, pip, npm, gem
- pipUp
    - aliased command in .bash_profile
- npm 
	- npm -v
	- npm install -g npm [installs globally]
	- npm outdated -g
	- npm update -g <pkg>
- gem
	- gem update

### Using local mail server

- Set up postfix to use maildir system (1 file per message)
	- /etc/postfix/main.cf: `home_mailbox = Maildir/`
		- It would be nice to be able to have this in `/var/mail/<username>/`, but I didn't find an easy solution to that.
- Set up dovecot to look in that folder (installed via brew)
	- /usr/local/etc/dovecot/local.conf: `mail_location = maildir:/Users/%u/Maildir`
- Helpful (to a point): <https://xdeb.org/node/1607>
- Explained mailbox types: <http://unix.stackexchange.com/questions/132654/how-to-make-postfix-create-maildir>

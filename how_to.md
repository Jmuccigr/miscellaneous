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
	- info: <http://awmc.unc.edu/wordpress/tiles/map-tile-information>

- OpenStreetMap
	- Attribution: `OpenStreetMap`
	- URL: `http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png`

- Stamen
	- ID: `terrain`, `toner`, `watercolor`
	- maxZoom: 20 for `toner`
	- note: Import script `src="http://maps.stamen.com/js/tile.stamen.js?v1.3.0"`, then `new L.StamenTileLayer("ID")`
	- info: <http://maps.stamen.com/>

## pandoc

- pip
    - pandocfilters
    - pandoc-fignos

- npm
    - pandoc-mermaid-filter

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

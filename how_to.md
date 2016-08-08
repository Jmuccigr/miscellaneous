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

# pandoc

- pip
    - pandocfilters
    - pandoc-fignos

- npm
    - pandoc-mermaid-filter

# Other

- npm
    - mermaid
- rbenv (itself installed homebrew)
	- ruby
- manually
	- [pdfsandwich](http://www.tobias-elze.de/pdfsandwich/)
		- Required
			- pdfunite from poppler (installed via homebrew)
			- txt2man (via homebrew)

## For updating

- pipUp
    - aliased command in .bash_profile
- npm 
	- npm -v
	- npm install -g npm [installs globally]
	- npm outdated -g
	- npm update -g <pkg>
- gem
	- gem update

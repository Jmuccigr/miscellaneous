---
title: Basemaps for leaflet
date: 25 May 2017
---

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


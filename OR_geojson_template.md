---
title: OpenRefine geoJSON export values for templating
author: John Muccigrosso
date: 3 June 2021
---

## Prefix

```
{
"type": "FeatureCollection",
"features": [
```

## Row Template

```
    {
      "type": "Feature",
      "geometry": {
           "coordinates": [ {{cells["Longitude"].value}}, {{cells["Latitude"].value}} ],
           "type": "Point"
           },
      "properties": {
           "name": {{jsonize(cells["Name"].value)}}
           }
    }
```

## Row Separator

```
,

```

## Suffix

```

    ]
}
```

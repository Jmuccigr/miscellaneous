---
title: ImageMagick tips
author: John D. Muccigrosso
---

- Make a label out of text  
`convert -set option:text_string "hello" -pointsize 36 label:text_string`
- Blur everything and convert to blob to get bounding box:  
`convert -blur 0x8 -threshold 90% -trim input_image.png -format "%Wx%H %wx%h%X%Y" info:`
- Trim image to box containing content defined in previous action  
`magick input_image.png \( +clone -blur 0x8 -threshold 90% -trim -set option:trim_size "%wx%h%X%Y" +delete \) -crop %[trim_size] -resize x800 show:`
- Peel off a 1-pixel wide strip of the west side image  
`magick input_image.png -crop +%[fx:1-w]+0  +repage show:`
- Get max color value for an image  
`magick input_image.png -verbose info: | grep max:  | sed 's/[^0-9]/ /g' | perl -pe 's/^\s+//g' | perl -pe 's/\s.*$//'`
- Get max color value for an image much faster:  
`convert input_image.png - | identify -precision 5 -define identify:locate=maximum -define identify:limit=1 | set -- | echo $2`

Process:

1. Strip off 1-pixel-wide strips from whatever side is desired
2. Check strip for sufficiently dark pixel
3. Two methods:
    1. Use as trim: Continue until there is a dark enough pixel and then crop original image up to this strip
    2. Use to remove junk near edge: Continue past the dark pixel strip until a row without dark pixels is found, then keep going until another dark-pixel row is found. Crop original image up to this second row.




---
title: Methods for removing diffuse gray background on scanned images
author: John D. Muccigrosso
---

## Canny edges

1. Use canny edge detection to get edges of letters and punctuation, etc.
1. Use morphology to close the edges
1. Use compositing to divide the original by the new image

```
magick input.img \( +clone -canny 0x1+10%+30% -morphology Close:3 Disk:3.5 \) -compose Divide_Src -composite output.img
```

### Notes

- This uses a smaller-than-default disc. For larger text, use a large disk like 5.3, which is larger than default, or close multiple times.
- For darker background, this may leave unsatisfying dark color inside letters.

## Blur & Level

1. Use blur to create a cleaner version of the image
1. Use level to get rid of the light grays from the background and grab some of the darker grays
1. Use morphology to expand the black areas.
1. Use compositing to divide the original by the new image

```
magick input.img \( +clone -blur 3 -level 10%,75% -negate -morphology dilate disk:3.5 \) -compose divide_src -composite output.img
```

## Another way

```
magick -define tiff:preserve-compression=true -compose screen "$1" \( "$1" -negate -lat 30x30+10% -negate -threshold 90% \) -composite "$fname".clean."$fext"
```

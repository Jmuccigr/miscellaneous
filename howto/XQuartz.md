---
author: John D. Muccigrosso
title: Quartz
date: Thursday, 10 December 2020
...

https://www.xquartz.org/FAQs.html

## Don't launch xterm

- Quartz launches a default app, so make it just true:
    - `defaults write org.macosforge.xquartz.X11 app_to_run /usr/bin/true`

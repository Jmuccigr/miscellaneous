---
title: Working with python
author: John D. Muccigrosso
date: Monday, 10 March 2025
...

## pip

- install a package: `pip install <package>`
- install a specific version of a package: `pip install --force-reinstall -v '<package>==<version>'`
- update package: `pip install -U <package>`
- list out of date: `pip list --outdated`
- see package dependencies: `pipdeptree` (needs to be installed)
- save installed packages: `pip freeze > requirements.txt`
- restore from saved packages: `pip install -r requirements.txt`

## Virtual environments

- Create: `python3 -m venv <directory>`
- Use: `source ~/.<old dir>/bin/activate`
- Update python:
    - Activate; write packages; mv to new dir; create new venv in old spot; install packages from list
        - `source ~/.<old dir>/bin/activate`
        - `pip freeze > requirements.txt`
        - `deactivate`
        - `mv <old dir> <new dir>`
        - `python3 -m venv <old dir>`
        - `source ~/.<old dir>/bin/activate`
        - `pip install -r requirements.txt`

## Tips

- get result of system call:

```
import subprocess
output = subprocess.getoutput("ls -l")
print(output)
```

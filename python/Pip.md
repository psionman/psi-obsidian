---
aliases: [pip]
tags: "#pip"
---
## Reinstall pip in a virtualenv
```bash
python -m ensurepip --upgrade
```
## Force pip to install latest version
tag: #latest-version
```bash
pip install --upgrade --force-reinstall <package>
```
## Current version of package
tag: #current-version
```bash
pip show django
```
## All versions of a package
tag: #all-versions
```bash
pip index versions <package>
```
## To install a particular version of a package
tag: #particular-version
```bash
pip install django==3.1.5
```
## Delete a package
```bash
pip uninstall <package>
```
## To create a requirements.txt
```bash
pip freeze > requirements.txt
```
## To install from requirements.txt
```bash
pip install -r requirements.txt
```
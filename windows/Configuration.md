## Python

Go to command prompt

```bash
python
```

If it goes to Windows store:

Go to the [Python.org](https://www.python.org) *Downloads* and look for the *Windows* link.

Click on *Download Windows installer (64-bit)*

Double-click on the *exe* file. Check on *Use admin privileges when installing py.exe* and *Add python.exe to PATH* . Then *Install Now*. (Close and re-opem command prompt if necessary)

If it still goes to Windows store then search for *[App execution aliases](https://stackoverflow.com/questions/58754860/cmd-opens-windows-store-when-i-type-python)* and uncheck all the python entries

(might have to reboot)

## Change default python versions

[follow this link](https://superuser.com/a/1399546/776696)

## Docker

Download [Docker Desktop](https://www.docker.com/products/docker-desktop/)

Double click to install (answer all the questions)

## Git

Download snd install [Git](https://git-scm.com/download/win)

## pyenv

In PS


```bash
Invoke-WebRequest -UseBasicParsing -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"
```

Restart PS (might have to restart Windows)

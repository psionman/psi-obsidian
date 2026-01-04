
```bash
pipx install poetry
```

## New virtual env

cd to \<projects> directory

```bash
poetry new <package name>
```

e.g. running the command

```bash
poetry new abc
```

in the directory *projects* will create

```
.
└─projects
    └─abc
        ├── abc
        │   └── __init__.py
        ├─── tests 
        │   └── __init__.py
        ├── pyproject.toml
        └── README.md
```

## Add a dependency

```bash
poetry add termcolor
```

If the dependency is in the *pyproject.toml* file run

```bash
poetry update package
```

## To use requirements.txt

```bash
Get-Content requirements.txt | ForEach-Object { poetry add $_ }
```

## Add poetry to existing projects

```bash
poetry init
```

## To start shell

<!-- (in the directory below the one with pyproject.toml) -->

```bash
poetry shell
```

## List environments with path to shell

```bash
poetry env list --full-path
```

## Delete environment

```bash
poetry env remove <full path to python>
```

## Clean environment and start again

See [this answer](https://stackoverflow.com/a/78337294/3070181)

Sample command:

```bash
poetry env use C:\Users\jeffw\.pyenv\pyenv-win\versions\3.11.8\python.exe
```

NB in *pyproject.toml*

```bash
[tool.poetry.dependencies]
python = "3.11.8"
```

Get rid of any dependencies and add them again through poetry

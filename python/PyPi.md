---
aliases: [pypi]
tags: "#pypi"
---
## Using uv
#uv
```
[project]
name = "bridgeobjects"
version = "0.1.32"
requires-python = '==3.13.*'
description = "blurb."
authors = [{name = "Jeff", "email" = "<jeffwatkins2000@gmail.com>"}]
readme = "README.md"
include = ["HISTORY.md"]

dependencies = [
"iniconfig>=2.1.0",
"packaging>=25.0",
"pluggy>=1.6.0",
"pygments>=2.19.2",
]

[dependency-groups]
dev = ['pytest']
  
[build-system]
requires = ['uv-build']
build-backend = 'uv_build'
```

See *build.py* in the *projects* project.
```
def _upload(project: Project, test_build: bool = False) -> int:
    """
        The PyPi token is stored in the environmental variable UV_PUBLISH_TOKEN
        the value is kept in Documents/pypi folder
    """
    try:
        with chdir(str(project.base_dir)):
            if test_build:
                proc = subprocess.Popen(['uv', 'publish', '--dry-run'])
            else:
                proc = subprocess.Popen(['uv', 'publish'])
        proc.wait()
        (stdout, stderr) = proc.communicate()
        del stdout, stderr
```

## Using poetry
In root of the project
```bash
poetry build
```
```bash
poetry publish
```
## Using twine
1. Create *wheel*
    ```bash
    python setup.py sdist bdist_wheel
    ```
2. Add *dist*, *build* and *\<appname>.egg-info* to *.gitignore*
3. Upload using (use *__token__* as username and the upload token from Bitwarden)
    ```bash
    twine upload dist/*
    ```
4. Combined
    ```bash
    python setup.py sdist bdist_wheel && twine upload dist/*
    ```
### To update
Remove the *whl* and *tar.gz* files related to any previous version.
### Necessary Packages
These packages need to be installed
1. *setuptools* and *wheel*
    ```bash
    pip install --user --upgrade setuptools wheel
    ```
2. *twine*
    ```bash
    pip install --user --upgrade twine
    pip install twine --ignore-installed
    ```
### To include data files
In *setup.py*
```python
if __name__ == '__main__':
    setup(
        package_data={
            'bfgbidding':['comment_data/*.json']
        },
        include_package_data=True,
        **setup_args,
        install_requires=install_requires
        )
```
In this case *comment_data* is at the same level as *src* in the project.
### Setting up a package for PyPi
These web-pages have good descriptions of the stages:
* [thucnc](https://medium.com/@thucnc/how-to-publish-your-own-python-package-to-pypi-4318868210f9)
* [python-in-plain-english (covers tests and tokens)](https://medium.com/python-in-plain-english/how-to-publish-a-project-into-pypi-f845f1cc4b36)
### Necessary Files
#### *README.md*
    ```text
    # Name of project
        A collection of modules ....
        ## Installation
        ```bash
        pip install project_name
        ```
    ```
#### *HISTORY.md*
    ```text
    Version 0.0.0
    Created and uploaded 30 July 202
    ```
#### *license.txt*
    ```text
    Copyright 2020 jeff Watkins
    Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
    The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
    ```
#### *setup.py*
    ```python
    import re
    from setuptools import setup, find_packages
    with open('README.md') as readme_file:
        README = readme_file.read()
    with open('HISTORY.md') as history_file:
        HISTORY = history_file.read()
    VERSION_FILE="psionapp/_version.py"
    with open(VERSION_FILE, 'r') as f_version:
        version_string = f_version.read()
    VSRE = r"^__version__ = ['\"]([^'\"]*)['\"]"
    mo = re.search(VSRE, version_string, re.M)
    if mo:
        version_string = mo.group(1)
    else:
        raise RuntimeError(f'Unable to find version string in {VERSION_FILE}.')
    setup_args = dict(
        name='psionapp',
        version=version_string,
        description='"""A basic application class which other applications can inherit."""',
        long_description_content_type="text/markdown",
        long_description=README + '\n\n' + HISTORY,
        license='MIT',
        packages=find_packages(),
        author='jeff watkins',
        author_email='support@bidforgame.com',
        keywords=['Application, User'],
        url='https://psionman@bitbucket.org/psionman/psionapp.git',
        download_url='https://pypi.org/project/psionapp/'
    )
    install_requires = [
        'username', 'nose'
    ]
    if __name__ == '__main__':
        setup(**setup_args, install_requires=install_requires)
    ```
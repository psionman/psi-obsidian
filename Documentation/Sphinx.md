[Sphinx](https://www.sphinx-doc.org/en/master/usage/quickstart.html) is a a documentation builder that creates html documents from Restructured  or Markdown text.
## Installing Sphinx
1. Install
    ```bash
    pip install -U Sphinx
    ```
## Start a Sphinx project
1. Navigate to your *docs* directory and enter:
    ```bash
    sphinx-quickstart
    ```
    Sphinx will then run through the questions it needs a to create the project.
### Under uv

```
uv add sphinx, sphinx_bootstrap_theme, recommonmark, sphinx_markdown_tables, sphinx_copybutton
```
```
uv run make html
```
### Under pyenv

Various modules to install
```bash
sudo pip install recommonmark &&
pip install sphinx-markdown-tables &&
pip install sphinx-copybutton &&
pip install sphinx-bootstrap-theme &&
pip install guzzle_sphinx_theme &&
pip install jupyter-sphinx
# pip install pylons-sphinx-themes
# pip install mozilla-sphinx-theme
```

```
# Basic conf.py
```python
# -- Imports -----------------------------------------------------------------
from recommonmark.parser import CommonMarkParser
import sphinx_bootstrap_theme
import os, re
import clipboard
# -- Get version -------------------------------------------------------------
version_string = ''
VERSION_FILE="versions.md"
with open(VERSION_FILE, 'r') as f_version:
    version_string = f_version.read()
VSRE = r"^__version__ = ['\"]([^'\"]*)['\"]"
mo = re.search(VSRE, version_string, re.M)
if mo:
    version_string = mo.group(1)
# -- Project information -----------------------------------------------------
project = '<project name>'
copyright = '202x, Jeff Watkins'
author = 'Jeff Watkins'
release = version_string
html_favicon = 'favicon.ico'
# -- General configuration ---------------------------------------------------
html_path = os.sep.join(['build', 'html', 'index.html'])
local_index_page = os.getcwd().replace('source', html_path)
print('-'*len(local_index_page))
print(local_index_page)
clipboard.copy(local_index_page)
print('-'*len(local_index_page))
html_favicon = 'favicon.ico'
extensions = [
    'recommonmark',
    'sphinx_markdown_tables',
    'sphinx_copybutton',
]
source_parsers = {'.md': 'recommonmark.parser.CommonMarkParser',}
source_suffix = {
    '.rst': 'restructuredtext',
    '.txt': 'markdown',
    '.md': 'markdown',
}
numfig = True
exclude_patterns = []
# -- Options for HTML output -------------------------------------------------
html_theme = 'bootstrap'
html_theme_path = sphinx_bootstrap_theme.get_html_theme_path()
html_static_path = ['_static']
html_css_files = [
    'css/custom.css',
]
```
To pick up version
```python
# version.py
__version__ = '0.0.0'
```
## Use css with Sphinx
1. In *conf.py*
    ```python
    html_static_path = ['_static']
    html_css_files = [
        'css/custom.css',
    ]
    ```
2. Create *.../build/html/_static/css/custom.css*
    ```css
    h1 {
        font-size: 28px;
        color: green;
    }
    h2 {
        font-size: 22px;
        color: green;
    }
    h3 {
        font-size: 18px;
        color: green;
    }
    a {
        color: darkgreen;
    }
    ```
<!-- ## conf.py
3. Imports
    ```python
    # -- Imports -----------------------------------------------------------------
    from recommonmark.parser import CommonMarkParser
    import sphinx_bootstrap_theme
    import os
    ```
4. General configuration
    ```python
    # -- General configuration ---------------------------------------------------
    html_path = os.sep.join(['build', 'html', 'index.html'])
    local_index_page = os.getcwd().replace('source', html_path)
    print(local_index_page)
    extensions = [
        'recommonmark',
        'sphinx_markdown_tables',
        'sphinx_copybutton',
    ]
    source_parsers = {'.md': 'recommonmark.parser.CommonMarkParser',}
    source_suffix = {
        '.rst': 'restructuredtext',
        '.txt': 'markdown',
        '.md': 'markdown',
    }
    numfig = True
    ```
5. Bootstrap Theme
    ```python
    html_theme = 'bootstrap'
    html_theme_path = sphinx_bootstrap_theme.get_html_theme_path()
    ```
6. To remove blank pages from LaTeX documents:
    in *conf.py*:
    ```python
    latex_elements = { 'classoptions': ',openany,oneside'}
    ``` -->
## Themes
1. Read The Docs
    ```python
    html_theme = "sphinx_rtd_theme"
    ```
2. Bootstrap
    ```bash
    pip install sphinx_bootstrap_theme
    ```
    ```python
    import sphinx_bootstrap_theme
    ...
    html_theme = 'bootstrap'
    html_theme_path = sphinx_bootstrap_theme.get_html_theme_path()
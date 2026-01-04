See [Sphinx pages](https://www.sphinx-doc.org/en/master/usage/markdown.html)
Good document on [best practices](https://www.markdownguide.org/basic-syntax)
To install
```bash
pip install --upgrade recommonmark
```
If necessary
```bash
pip install sphinx-markdown-tables
```
## Internal links
1. If the link is to a heading on this page, lower-case and hyphenise (use the script (*md-convert*) the heading to create the link, e.g.
```text
[Get directory from path](#get-directory-from-a-file-path)
...
## Get directory from a file path
```
1. If the heading is on another page in the same document
```text
[Get directory from path](instruction.html#get-directory-from-a-file-path)
```
1. To create an arbitrary link
source:
```bash
[text to display](#name-of-link)
```
target:
```bash
<span id="name-of-link"></span>
```
## External links
source:
```bash
[text to display](name_of_page.html#name-of-link)
```
target:
```bash
<span id="name-of-link"></span>
```
## Images
```bash
![Alt text](images/image_file.png)
```
More control over the image might be had with the html *img* target
```html
<img style="
        display: block;
        margin-left: auto;
        margin-right: auto;
        width: 30%;
        "
    src="_images/main_menu.png"
    alt="Main menu">
</img>
```
To centre the image
```bash
<img src="_images/registration.png" alt="Registration" width="400" class="centred">
```
add this to */build/html/_static/css/custom.css*
```bash
.centred {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
  }
```
(might have to add to */source/_static/css/custom.css*)
### To adjust size of image
```bash
<img src="_images/image_file.png" alt="Alt text" width="300">
```
(The file needs to be in *html/_images*)
## Tables
(Set up tables in conf.py.)
```bash
|To obtain|Use|Centred|Numbers|
| --- | --- | :---: | ---:|
|Two decimal places | {:.2d}|Y|300|
|Right fill 20 spaces | {:<20}|N|24|
```
Produces:
|To obtain|Use|Centred|Numbers|
| --- | --- | :---: | ---:|
|Two decimal places | {:.2d}|Y|300|
|Right fill 20 spaces | {:<20}|N|24||
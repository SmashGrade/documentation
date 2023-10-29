# Introduction
This is the technical documentation for the SmashGrade Application written in Markdown and served by Material for MkDocs.

# How to run/view the documentation locally
You can edit and view the markdown files in any editor or on GitHub directly. However, to access extended markdown features such as tabs and "Wiki Functionality" for navigation and search, you must serve the documentation with [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/).

## Prerequisites
### Python & pip
If you do not yet have Python and its package Manager "pip" installed (you can check with `pip --version` in any terminal) please do so. Either via Browser https://www.python.org/downloads/ or your favorite package manager, for example on windows `winget install -e --id Python.Python.3.10`

### Material for MkDocs
Next you need to install the Python Package Material for MkDocs with [pip](https://pip.pypa.io/en/stable/) by running: `pip install mkdocs-material` This will install all necessary dependencies. Make sure to re-open all terminals/code editors after the installation to make sure the newly installed MkDocs is available in Path.

### Serve the documentation locally
In the root folder of this repository enter `mkdocs serve` then you can access the live preview of the documentation at http://127.0.0.1:8000/ 

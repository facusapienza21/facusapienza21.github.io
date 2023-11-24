---
layout: post
title: Creating a single stadarized bibliography file from a bunch of bibliography and latex files
date: 2023-11-22 15:09:00
description: Bored of formating bibliography files in latex manually? Solve this for good.
tags: computing scientific-writing
categories: posts
featured: false
---

Tired of formating you bibliography files in latex? Are you a little bit obsessed about the format of your text files, including author, title, year, ... ordering or spacing/tabulation (that will be me)? Do you have a bunch of different bibliography and latex files that all combine to compule one single manuscript and you would like to unify them all under a single `bibliography.bib` file? Then you will find this post useful. 

Maybe you latex project looks like this, 
```
.
|- main.tex
|- main.pdf
|- chapters
   |- intro.tex
   |- chp_1.tex
   |  ...
   |- chp_19.tex
|- biblography
   |- bib1.bib
   |- ...
   |- bib11.bib
```
and you spend quite some time curating you bibliography files so they look complete and well organize, but instead they look like this: 
```
# bib1.bib

@incollection{key1,
title = {A cool paper},
author = {My collegue},
booktitle = {Advances in Neural Information Processing Systems 24},
pages = {1899--1907},
year = {2011},
}

@article {key2,
    AUTHOR = {other authors},
     TITLE = {Some title},
   JOURNAL = {Ann. Appl. Probab.},
}
```

If well in `biblatex` we can add multiple bibliography files with the `\addbibresource` command in the preamble, it could be useful to manipulate your bibliography entries in a more convenient way. Fortunately for us, the Python library `pybtex` allow us to do this. Let's see this with one example. We start with the following imports. 
```python
import re
import glob, os
import warnings

from pybtex.database.input import bibtex
from pybtex.database import BibliographyData

import pybtex.errors
# This is so we can ignore duplicated entries
pybtex.errors.set_strict_mode(False)
```

Let's suppose you have many latex `.tex` files that you are using in a project (and for example are included with the `\include` command in `main.tex`), but you also have multiple sources or references, `bib1.bib`, `bib2.bib`, etc. Given a working directy, we can find all the files in that directory and its subfolders with the right extensiosn with the following function.
```python
def find_extension(extention, path):
    """
    Find all files with required extension in path system
    """

    res = []   

    for root, dirs, files in os.walk(path):
        for file in files:
            if(file.endswith(extention)):
                res.append(os.path.join(root,file))
                
    return res

tex_files = find_extension(".tex", ".")
bib_files = find_extension(".bib", ".")
```
Now, we can just read all the `.tex` files and merge them in one single string, and then parse it so it identifies all the entries that match the patern `\cite{...}` inside any of the `.tex` files:
```python
# Attach all the text in files to a single string
latex = ""

for file in tex_files:
    # with open("tex/sections/adjoint-state.tex", 'r') as f:
    with open(file, 'r') as f:
        latex += f.read()

# Parser
rx = re.compile(r'''(?<!\\)%.+|(\\(?:no)?citep?\{((?!\*)[^{}]+)\})''')
rx.finditer(latex)

authors = []

authors_unformated = [m.group(2) for m in rx.finditer(latex) if m.group(2)]

# Format author entries for cases like \cite{author1, author2}
for author_ref in authors_unformated:
    new_authors = author_ref.split(',')
    new_authors = [x.strip() for x in new_authors]
    authors += new_authors
```
Now the list `authors` contains all the reference entries used in at least one of the `.tex` files in our working directory. The next step is to use these as keys to find the corresponding bibliography entry and store them in a new bibliography file. We do this by parsing the different bibliography files and store them all together in one single list. 
```python
bib_data = []

for file in bib_files:
    parser = bibtex.Parser()
    bib_data.append(parser.parse_file(file))
```
We can finally create a new black bibliography file with `pybtex` that add the corresponding bibliography entries based on the contents of your latex files:
```python
filtered_bib_data = BibliographyData()

for entry in authors: 
    ref_founded = False
    for bib_source in bib_data:
        try:
            if not ref_founded:
                filtered_bib_data.add_entry(entry, bib_source.entries[entry])
                ref_founded = True
                print("Reference found {}".format(entry))
        except:
            pass
        if not ref_founded:
            warnings.warn("Reference not found: {}".format(entry))
```
and finally export a new `.bib` file with the references in a nice format: 
```python
filtered_bib_data.to_file("bib_test.bib", bib_format="bibtex")
```

Here is a single [Python script](https://github.com/facusapienza21/DiffEqSensitivity-Review/blob/main/.utils/biblatex_merger.py) that does all this work and you can directly execute from the terminal to produce an unified and formated `.bib` file. Why to stop here? You can further create a [GitHub Action](https://github.com/facusapienza21/DiffEqSensitivity-Review/blob/main/.github/workflows/biblatex.yml) that does this for you automatically every time you make changes to your `.bib` and `.tex` files!  
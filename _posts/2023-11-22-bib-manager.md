---
layout: distill
title: Creating a single and beautiful `.bib` file from a bunch of `.bib`s and `.tex`
description: Bored of formating bibliography files in latex manually? Solve this for good.
tags: computing scientific-writing
giscus_comments: true
date: 2023-11-22
featured: true

authors:
  - name: Facundo Sapienza
    # url: "https://en.wikipedia.org/wiki/Albert_Einstein"
    affiliations:
      name: UC Berkeley

bibliography: 2018-12-22-distill.bib

# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
_styles: >
  .fake-img {
    background: #bbb;
    border: 1px solid rgba(0, 0, 0, 0.1);
    box-shadow: 0 0px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 12px;
  }
  .fake-img p {
    font-family: monospace;
    color: white;
    text-align: left;
    margin: 12px 0;
    text-align: center;
    font-size: 16px;
  }

---

Tired of formating you bibliography files in latex? Are you a little bit obsessed about the format of your text files, including author, title, year, ... ordering or spacing/tabulation (that will be me)?,Do you have a bunch of different bibliography and latex files that all combine to compule one single manuscript and you would like to unify them all under a single `bibliography.bib` file? Then you will find this post useful. 

If well in `biblatex` we can add multiple bibliography files with the `\addbibresource` command in the preamble, it could be useful to manipulate your bibliography entries in a more convenient way. Fortunately for us, the Python library `pybtex` allow us to do this. Let's see this with one example. We start with the following imports. 
<d-code block language="python">
import re
import glob, os
import warnings

from pybtex.database.input import bibtex
from pybtex.database import BibliographyData

import pybtex.errors
# This is so we can ignore duplicated entries
pybtex.errors.set_strict_mode(False)

rx = re.compile(r'''(?<!\\)%.+|(\\(?:no)?citep?\{((?!\*)[^{}]+)\})''')
</d-code>

Let's suppose you have many latex `.tex` files that you are using in a project (and for example are included with the `\include` command in `main.tex`), but you also have multiple sources or references, `bib1.bib`, `bib2.bib`, etc. Given a working directy, we can find all the files in that directory and its subfolders with the right extensiosn with the following function.
<d-code block language="python">
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
</d-code>
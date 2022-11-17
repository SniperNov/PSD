## Dependencies

The original program uses the following dependencies, which can be found in the file `prototype.py`.
However, the whole list of dependencies can be found in the `requirements.txt` file. 

1. distutils (python standard library | imported but not used | deprecated)

The distutils package provides support for building and installing additional modules into a Python installation. 
The new modules may be either 100%-pure Python, or may be extension modules written in C, or may be collections of 
Python packages which include modules coded in both Python and C.

2. pdf2docx

Open source Python library converting pdf to docx. The main features of the library are:
- Extract data from PDF with PyMuPDF, e.g. text, images and drawings.
- Parse layout with rule, e.g. sections, paragraphs, images and tables.
- Generate docx with python-docx.

Can be installed via: `pip install pdf2docx` or `conda install -c conda-forge python-docx`

3. [docx](https://python-docx.readthedocs.io/en/latest/index.html) 

python-docx is a Python library for creating and updating Microsoft Word (.docx) files.

Can be installed via: `pip install python-docx`

4. [simplify_docx](https://pypi.org/project/simplify-docx/)

A utility for simplifying python-docx document objects.

Can be installed via: `pip install simplify-docx`

5. [json](https://docs.python.org/3/library/json.html) (python standard library)

JSON encoder and decoder.

6. [spacy](https://spacy.io/)

Industrial-Strength Natural Language Processing.

Can be installed via:
[code]
pip install -U pip setuptools wheel
pip install -U spacy
python -m spacy download en_core_web_md
[code]

7. [os](https://docs.python.org/3/library/os.html) (python standard library):

Miscellaneous operating system interfaces.

8. [sqlite3](https://docs.python.org/3/library/sqlite3.html) 

DB-API 2.0 interface for SQLite databases.

9. [openpyxl](https://openpyxl.readthedocs.io/en/stable/)

A Python library to read/write Excel 2010 xlsx/xlsm files.

Can be installed via: `pip install openpyxl`

10. [pathlib](https://docs.python.org/3/library/pathlib.html) (python standard library)

Object-oriented filesystem paths.

11. [prompt_toolkit](https://github.com/prompt-toolkit/python-prompt-toolkit)

Library for building powerful interactive command line applications in Python.

Can be installed via: `pip install prompt_toolkit`

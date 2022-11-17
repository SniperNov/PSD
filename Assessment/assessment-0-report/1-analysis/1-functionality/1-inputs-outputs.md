## Input

- Index.xlsx: The index.xlsx will be opened by openpyxl. 
The paper pdf name and the paper name will be read and stored in the future execution.

- Papers folder: The pdf files in Papers folder are read by pdf2docx package to transform pdf files into docx files, 
leading to better processing data.

## Output 

- Docs folder: 56 .docx documents transformed from the original pdf documents in the Paper folder. 
The name of each XXX.docx file is in the format of XXX.pdf.docx.

- Ents folder: 56 .json documents includes entities extracted from corresponding .docx documents. 
The name of each XXX.json file is in the format of XXX.pdf.json.

- JSON folder: 56 .json documents. The content in .docx files is all resolved and parsed to the .json documents. 
Those .json files recognise what specific sections those paragraphs or sentences are, e.g. Title or Abstract. 
The name of each XXX.json file is in the format of XXX.pdf.json.

- data folder: There is a single file in the data folder named test_db.sqlite. 
This file is an SQLite database created by the program which sorted out all the information resolved 
by the mean of Natural Language Processing. Those pieces of information are collected from those documents preserved 
in the Docs, Ents and JSON folders. 

- history.PSD.text: The program built a REPL(read-eval-print loop). This history.PSD.text file take the record all 
the user input histories.

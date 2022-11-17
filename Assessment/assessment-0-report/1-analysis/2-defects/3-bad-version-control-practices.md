## Redundant readme steps

Readme.md guide us to do the following:

> Create directories Docs, Ents, JSON, data in the source directory
 
These steps are redundant and can be managed via git.

## Unwanted files can be added into git by mistake

Readme.md tell us to do the following:

> Extract contents of papers.zip to the source directory - unarchiving Papers/ and index.xlsx
 
Those files, together with files created during the program execution, can be by mistake be added to git. 
This is unwanted behaviour as those files are program artifacts and must not be in git.


## No configuration available

All paths and names are hardcoded inside the program. Some examples here:

```python
xlsx_file = Path(".", "index.xlsx")
#... 
index = wb_obj['Sheet1']
#... 
source_path = "Papers/"
docs_path = "Docs/"
json_path = "JSON/"
ents_path = "Ents/"
# …
row_dictionary['paper_docx'] = os.path.join(docs_path,      row_dictionary['paper_pdf'] + '.docx')
row_dictionary['paper_json'] = os.path.join(json_path, row_dictionary['paper_pdf'] + '.json')
row_dictionary['paper_entities'] = os.path.join(ents_path, row_dictionary['paper_pdf'] + '.json')
# …
nlp = spacy.load("en_core_web_md")
# … 
QuestionWorkCompleter = WordCompleter(['get', 'one', 'all', 'papers', 'that', 'mention', 'person', 
                                       'organisation', 'work', 'and', 'or'],
                             ignore_case=True)
# … 
conn = get_connection("data/test_db.sqlite")
# …
history=FileHistory('historyPSD.txt'),
```

Problems, this approach creates:
1. Configuration code is mixed with our business logic. This leads to possible bugs when changing this code. 
2. Configuration code is spread across the code. It makes it unobvious to understand all parameters the program 
depends on.
3. Configuration code is under git. This makes it extremely difficult for our program to support different environments
and leads to code changes in git every time we need to change some configuration.

## No option to change the output format
	
The code, provided in assessment uses direct `print` statements. This approach is good enough for local development, 
but this is not production approach. Ideally we would like to have an option to add timestamp, some env variables, 
program name, etc. Also, for debug purpose we may need separate our log information into loggging levels as it is said 
in the following rfc document: https://datatracker.ietf.org/doc/html/rfc5424#section-6.2.1.

## Business logic is mixed with technical layer SQL

The prototype.py contains not only python code but also SQL commands. In order to encapsulate code to make it readable, 
the SQL commands can be removed to a new file and the prototype.py can call the file containing SQL commands when 
necessary.

## Low readability

The total number of lines in the prototype.py code is 216, which will take much time to read. Some codes are cumbersome 
and can be simplified. For instance, as the figure [] shows, all the if command contains one same condition: 
“current_index < len(query_string_array)”. These lines of this condition can be simplified and mentioned on the first 
if condition.

Example of the jumbled if-condition lines:

```python
    if current_index < len(query_string_array) and query_string_array[current_index] == 'get':
        current_index+=1
        if current_index < len(query_string_array) and query_string_array[current_index] == 'one':
            current_index+=1
            query_parts['limit'].append(' Limit 1')
        elif current_index < len(query_string_array) and query_string_array[current_index] == 'all':
            current_index+=1
        if current_index < len(query_string_array) and query_string_array[current_index] == 'papers':
            current_index+=1
            query_parts['select'].append('*')
            query_parts['from'].append('papers')
        if current_index < len(query_string_array) and query_string_array[current_index] == 'that':
            current_index+=1
            if current_index < len(query_string_array) and query_string_array[current_index] == 'mention':
                current_index+=1
```

In addition, the code is not well-organized. The code should mention package importing at the beginning of the code, 
instead of in the middle. Some codes can be divided into different functions, which can increase the readability.

## Unused dependencies

Unused/unnecessary dependencies, found in prototype.py:
- Distutils.command.build
- from sqlite3 import Error

Unused/unnecessary dependencies, found in requirements.txt are not so easy to demonstrate.
By using special tools we can find out all the dependencies that are not necessary for our project. 
By running a special tool [pip-extra-reqs](https://github.com/r1chardj0n3s/pip-check-reqs) we can see the following 
list:

```bash
Extra requirements:
fonttools in requirements.txt
click-repl in requirements.txt
marshmallow in requirements.txt
threadpoolctl in requirements.txt
itypes in requirements.txt
six in requirements.txt
coreschema in requirements.txt
botocore in requirements.txt
django-filter in requirements.txt
backports-zoneinfo in requirements.txt
scipy in requirements.txt
boto3 in requirements.txt
googleapis-common-protos in requirements.txt
kombu in requirements.txt
requests in requirements.txt
preshed in requirements.txt
filetype in requirements.txt
django-health-check in requirements.txt
pyasn1-modules in requirements.txt
google-resumable-media in requirements.txt
pypdf2 in requirements.txt
sqlalchemy in requirements.txt
dj-rest-auth in requirements.txt
opencv-python in requirements.txt
python-dotenv in requirements.txt
jmespath in requirements.txt
click in requirements.txt
inflection in requirements.txt
spacy-legacy in requirements.txt
urllib3 in requirements.txt
typer in requirements.txt
sqlparse in requirements.txt
spacypdfreader in requirements.txt
google-crc32c in requirements.txt
ruamel-yaml in requirements.txt
celery in requirements.txt
seqeval in requirements.txt
django-celery-results in requirements.txt
pyexcel-io in requirements.txt
coreapi in requirements.txt
tqdm in requirements.txt
et-xmlfile in requirements.txt
lxml in requirements.txt
colorama in requirements.txt
filelock in requirements.txt
joblib in requirements.txt
cryptography in requirements.txt
defusedxml in requirements.txt
scikit-learn in requirements.txt
rsa in requirements.txt
django-cors-headers in requirements.txt
pyyaml in requirements.txt
fire in requirements.txt
en-core-web-trf in requirements.txt
doccano in requirements.txt
pdfminer-six in requirements.txt
langcodes in requirements.txt
environs in requirements.txt
regex in requirements.txt
django-polymorphic in requirements.txt
pandas in requirements.txt
google-cloud-storage in requirements.txt
chardet in requirements.txt
pycparser in requirements.txt
cachetools in requirements.txt
orderedmultidict in requirements.txt
smart-open in requirements.txt
pyparsing in requirements.txt
texttable in requirements.txt
djangorestframework in requirements.txt
vine in requirements.txt
pyasn1 in requirements.txt
google-cloud-core in requirements.txt
django-storages in requirements.txt
shortuuid in requirements.txt
google-auth in requirements.txt
waitress in requirements.txt
djangorestframework-xml in requirements.txt
pymupdf in requirements.txt
click-plugins in requirements.txt
django in requirements.txt
gunicorn in requirements.txt
cymem in requirements.txt
certifi in requirements.txt
cffi in requirements.txt
django-drf-filepond in requirements.txt
numpy in requirements.txt
asgiref in requirements.txt
click-didyoumean in requirements.txt
uritemplate in requirements.txt
idna in requirements.txt
python-dateutil in requirements.txt
lml in requirements.txt
charset-normalizer in requirements.txt
wcwidth in requirements.txt
spacy-transformers in requirements.txt
wasabi in requirements.txt
typing-extensions in requirements.txt
protobuf in requirements.txt
commonmark in requirements.txt
transformers in requirements.txt
pyexcel in requirements.txt
termcolor in requirements.txt
pathy in requirements.txt
murmurhash in requirements.txt
ruamel-yaml-clib in requirements.txt
blis in requirements.txt
packaging in requirements.txt
s3transfer in requirements.txt
en-core-web-md in requirements.txt
pyexcel-xlsx in requirements.txt
greenlet in requirements.txt
rich in requirements.txt
jinja2 in requirements.txt
django-cleanup in requirements.txt
pygments in requirements.txt
torch in requirements.txt
pydantic in requirements.txt
amqp in requirements.txt
dj-database-url in requirements.txt
furl in requirements.txt
srsly in requirements.txt
spacy-loggers in requirements.txt
google-api-core in requirements.txt
markupsafe in requirements.txt
en-core-web-sm in requirements.txt
spacy-alignments in requirements.txt
whitenoise in requirements.txt
catalogue in requirements.txt
pytz in requirements.txt
django-rest-polymorphic in requirements.txt
thinc in requirements.txt
tokenizers in requirements.txt
huggingface-hub in requirements.txt
billiard in requirements.txt
drf-yasg in requirements.txt
```

All of these dependencies are redundant for our program. However, the code and functionality has to be carefully 
tested after those lines would have removed. 

## Duplicated database connection 

We see code duplication for database access. This can be seen on line 41 and 199. This is something unnecessary, 
and we must avoid this in our program as can lead to huge performance problems in the future. 

## Tests 

There is no tests written. It is very risky to change the program as this can lead to some unwanted bugs and 
problems. 



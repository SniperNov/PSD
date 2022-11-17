## Unnecessary dependencies

We can improve our code by deleting those dependencies from `prototype.py`. Also, we can clear up our `requirements.txt` 
by deleting everything redundant using `pip-extra-reqs` output . This will speed up the pip install time, reduce 
installation complexity and make the resulting size of our program smaller.

## No configuration available

According to [https://12factor.net/config](https://12factor.net/config) the best place to store our configs is in 
environment variables. Therefore it is good option to put all our config variables in one place and refactor our 
code to support getting variables from an environment. Also, it is a good practice to have .env.example and .env to 
get rid of complexity working with such approach on local machine. 

## No option to change the output format

The solution could be to use some popular log libraries, or we can write our simple OOP alternative that will suit 
our basic needs. However, writing logs and output is quite simple and popular topic. Therefore, using some popular
log libraries is more preferable. 

## Business layer is mixed with Application layer

Service layer related to database queries, work with files, work with output/logs has to be separated from the main
program logic. We can apply OOP principles to get the best result here. This will allow us to reduce the complexity of
the program, will make it easier to read and make things like unit tests possible.

As long as this point is done we can cover our code with unit tests and build CI pipelines to measure our code metrics
such as code coverage, vulnerabilities, dependencies, etc.  

## Low readability

Many parts of the code written without any guidance, structure, or in mind of best practices. 
Some examples are:
- Module import parts are spread across the whole program. 
- Function declaration  are spread across the whole program. 
- SQL code inserted straight into the business logic. 
- Complicated if, else structures.  
- The same code is responsible for migrations and db queries. 
- Interactive component makes it difficult to measure the performance of the code. 

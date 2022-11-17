# POC Requirements Engineering 

TODO: Proper place for this block!
For the prototype our team decided to follow agile project management approach. We don't want to 
be very strict here, so, instead of scrum and sprints, we are going to use Kanban approach
with several milestones and 

Theme/Initiative:

Develop a system that would be able to understand a special, easy to work with and simple
query language and return results of that queries in different graphical and textual formats.    

Epics: 
1. Develop a query language that is able to handle different analytical queries. 
2. Develop a module to visualize different queries in different formats.
[Link to Epics visualisation](assessment-1-design-and-planning/1-high-level-design-of-the-end-to-end-solution/3-approached-ui-design.md)

## Query language requirements

- All the queries has to be done in English language
- The query language has to be close/similar to the human language query
- The same query can have some slight differences as in real world the same word
  can have different synonyms. However, the query structure has to remain the same.
- Each query has to support the structure that allows it to be split into 3 parts: 
Category (ex.: show), Subcategory (ex: links between), Parameters (author A and author B).

Query language example:
`show links between author A and author B`

## Visualization module requirements
#### Standard Technique
- The module has to be able to get an abstract syntax tree(AST) from query language parsing module, determine 
the target processor for the query, process it, determine the proper visualiser for the query, and visualise
it. 
- System has to have a list of processors that can handle different query types.
- The communication between a processor and the system has to be done via interface. 
- The system has to have a list of visualisers to support different visualisation types.
- The system has to be able to get a processor result and pass it to a proper visualiser.
- The communication between a visualiser and the system has to be done via interface.
### Further Maintainance
- The system has to support an extensible architecture. 
- New processors can be easily introduced in the future. 



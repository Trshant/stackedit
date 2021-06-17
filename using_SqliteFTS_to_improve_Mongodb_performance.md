We quantify unstructured text data at Anzyz. We use MongoDb as our daily database. However we found that searching for text was extremely slow and while our customers are very patient people, we arent ! At the end, I used SqliteFTS to create an in-memory database, and inserted the text and the text id. Whe we need to search for text, we search in the in-memory database to get data and return the ids
his post documents our trying to get past the bottlenecks and getting to the final solution

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbODQ3Njk4NDI4LC0xOTQxMjA1MjA5LC0zNz
IxMjQxNTEsMjI1NzkwOTI2LDczMDk5ODExNl19
-->
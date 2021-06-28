We quantify unstructured text data at Anzyz. We use MongoDb as our daily database. However we found that searching for text was extremely slow and while our customers are very patient people, we arent ! At the end, I used SqliteFTS to create an in-memory database, and inserted the text and the text id. When we need to search for text, we search in the in-memory database to get data and return the ids in a list, and this list goes into the mongodb for further processing in the aggregation pipeline.



Our next steps are to get persistence for sqlite so that we can speed up the updates/rollouts and for performance/security.

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUyMjUwODk5MCwxNzMxMjg4MzE3LDMyNj
U4ODM4LC0xOTQxMjA1MjA5LC0zNzIxMjQxNTEsMjI1NzkwOTI2
LDczMDk5ODExNl19
-->
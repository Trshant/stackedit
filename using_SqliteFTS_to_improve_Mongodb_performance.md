We quantify unstructured text data at Anzyz. We use MongoDb as our daily database. However we found that searching for text was extremely slow and while our customers are very patient people, we arent ! At the end, I used SqliteFTS to create an in-memory database, and inserted the text and the text id. When we need to search for text, we search in the in-memory database to get data and return the ids in a list, and this list goes into the mongodb for further processing in the aggregation pipeline.

Our next steps are to get persistence and 
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI4Nzg4MTM5NCwzMjY1ODgzOCwtMTk0MT
IwNTIwOSwtMzcyMTI0MTUxLDIyNTc5MDkyNiw3MzA5OTgxMTZd
fQ==
-->
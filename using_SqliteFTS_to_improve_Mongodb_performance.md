We quantify unstructured text data at Anzyz. 
MongoDB is a big part of our software arcitecture. A huge part of the magic that we provide our customers is the time we take to see the effect the manually crafted AI has on the text. on sub 100gb databases, the performance while finding substring in a text string field , while nothing to write about, was not bad. However, when customers came back to us with really huge datasets, we found that MongoDB really slowed down. It did not matter how much hardware we threw at the problem, it was not going to speed up anytime.
So i slowly started to research options to make this 
However we found that searching for text was extremely slow and while our customers are very patient people, we arent ! At the end, I used SqliteFTS to create an in-memory database, and inserted the text and the text id. When we need to search for text, we search in the in-memory database to get data and return the ids in a list, and this list goes into the mongodb for further processing in the aggregation pipeline.

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY4MTk5MjU5OCwyMDY2MjMwMjU5LC01Mj
I1MDg5OTAsMTczMTI4ODMxNywzMjY1ODgzOCwtMTk0MTIwNTIw
OSwtMzcyMTI0MTUxLDIyNTc5MDkyNiw3MzA5OTgxMTZdfQ==
-->
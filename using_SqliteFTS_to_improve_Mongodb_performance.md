We quantify unstructured text data at Anzyz. 
MongoDB is a big part of our software arcitecture. A huge part of the magic that we provide our customers is the time we take to see the effect the manually crafted AI has on the text. on sub 100gb databases, the performance , while nothing to write about, was not bad. However, when customers came back to build really huge When we started to deal with 
However we found that searching for text was extremely slow and while our customers are very patient people, we arent ! At the end, I used SqliteFTS to create an in-memory database, and inserted the text and the text id. When we need to search for text, we search in the in-memory database to get data and return the ids in a list, and this list goes into the mongodb for further processing in the aggregation pipeline.

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU4NDM0MDQ1NiwtNTIyNTA4OTkwLDE3Mz
EyODgzMTcsMzI2NTg4MzgsLTE5NDEyMDUyMDksLTM3MjEyNDE1
MSwyMjU3OTA5MjYsNzMwOTk4MTE2XX0=
-->
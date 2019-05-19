---
title: "Web Assembly and my opinion on it"
date: 2019-05-19T00:01:43+05:30
draft: true
tags : [programming , webDevelopment , webassembly ]
Description : "My effort to understand web assembly"
---
Since I heard about webASsembly, i have been enthralled by it. So i did some investigating on my own as to WA being faster than JavaScript. 
In short, what i did was follow [Daniel Simmons's](https://medium.freecodecamp.org/get-started-with-webassembly-using-only-14-lines-of-javascript-b37b6aaca1e4) awesome intro tute, but write some JS to benchmark some code.  
  
First i googled the code to benchmark the code and ended up at a [stackoverflow](https://stackoverflow.com/questions/4784745/how-can-i-measure-the-execution-time-of-a-script) post.
```javascript
function  time_my_script(script) {
	var  start  =  new  Date();
	script();
	return  new  Date() -  start;
}
```
The native javascript written to check the webassembly version was:
```javascript
function  js_squarer(num) {
	return  num  *  num;
}
``` 
I found that the native javascript version was consistently 3 times faster than the webassembly version. This lack of speed makes it clear to me that WA is not yet matured enough to be considered to replace JS in web development projects. However it can and will play a huge part in porting legacy projects to the web interface.   
I partially agree with [Lemire's](https://lemire.me/blog/2018/10/23/is-webassembly-faster-than-javascript/) conclusions and think that well written javascript will be faster than webassembly at this moment, May 2019. However, I respectfully disagree with him on a few points:
1. Loading times for WA is a bit more than JS. This can 
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUxNTYyODc0MSwyMDgzNzgzNDI0LC0xMz
k2NDM3NDI0LC04Njk3NTI4ODBdfQ==
-->
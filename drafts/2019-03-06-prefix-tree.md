---
title: "Implementing a prefix tree in typescript"
date: 2019-03-06T08:00:00+05:30
draft: false
tags : [Algorithm , PrefixTree, Trie, TypeScript, Javascript, DataStructures]
Description : "Building a prefix tree in typescript"
---  
I am avoiding the write up on the datastructure as wikipedia has a real nice [one](https://en.wikipedia.org/wiki/Trie) on it. But I do intend to implement it in typescript.  

I will start by coding up a node. At the least this node should have the value of the element and a list of child nodes and a way to add to the child node list.  

```typescript
type NumOrStrArray = number[] | string[];

class node {
    value: number|string|null;
    childNodes: NumOrStrArray ;
    constructor(value,parentNode) {
        this.value = value;
        this.childNodes = [];
        if (parentNode != null) {
            parentNode.addChild(this);
        }
    }
    addChild(childNode) {
        this.childNodes.push(childNode);
    }
}
```  

Since we have it in code, lets test it:
```javascript
var mother_node = new node(null, null);
var string_to_store = "rupsa";
var previous_node = mother_node;
var stored_nodes = [];
string_to_store.split('').forEach(function (element, index) {
    var newNode = new node(element, previous_node);
    stored_nodes.push(newNode);
    previous_node = newNode;
})
console.log(stored_nodes);
```
Now lets define a tree as a class.
```typescript
//TODO : 
class tree {
    constructor() {
        this.mother_node = new node(null, null);
    }
    addToTree(StringOrNumber){
        
    }
}
```
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYxNDIxMDk5NSwtOTQ2MTg2NDM5XX0=
-->
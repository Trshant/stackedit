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
class prefix_tree {
    mother_node: any;
    previous_node: any;
    stored_nodes: any[];
    constructor(value) {
        this.mother_node = new node(null, null);
        this.previous_node = this.mother_node;
        this.stored_nodes = [];
    }
    addToTree(StringOrNumber) {
        for (var element of StringOrNumber.split('')) {
            console.log(element, this.previous_node ) ;
            var oldNode = this.previous_node.searchChildNodes(element);
            if (oldNode == null) {
                var newNode = new node(element, this.previous_node);
                this.stored_nodes.push(newNode);
                this.previous_node = newNode;
            } else {
                this.previous_node = oldNode;
            }   
        }
    }
}
```
Now we have written this, but we dont have the function `searchChildNodes` in the node class. So we will need to code that up.

```typescript
searchChildNodes(valueToSearch) {
    for (var  element  of  this.childNodes) {
        if ( element.value  ==  valueToSearch) {
            return  element;
        }
    }
    return  null;
}
```
The complete `Node` class definition looks like this now:
```typescript
class node {
    value: number | string | null;
    childNodes: NameOrNameArray;
    constructor(value, parentNode) {
        this.value = value;
        this.childNodes = [];
        if (parentNode != null) {
            parentNode.addChild(this);
        }
    }
    addChild(childNode) {
        this.childNodes.push(childNode);
    }
    searchChildNodes(valueToSearch) {
        for (var element of this.childNodes) {
            if ( element.value == valueToSearch) {
                return element;
            }
            
        }
        return null;
    }
}
```
Testing it all together:
```typescript

```

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU4MDk3NDIzMSwtMjkyODY0Njc2LC02MT
QyMTA5OTUsLTk0NjE4NjQzOV19
-->
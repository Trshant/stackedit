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
        this.previous_node = this.mother_node;
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
var  trie  =  new  prefix_tree(null);
trie.addToTree("to");
trie.addToTree("tea");
console.log(trie.stored_nodes);
```
You can play around with [this](https://www.typescriptlang.org/play/#src=type%20NameOrNameArray%20%3D%20number%5B%5D%20%7C%20string%5B%5D%3B%0D%0A%0D%0Aclass%20node%20%7B%0D%0A%20%20%20%20value%3A%20number%20%7C%20string%20%7C%20null%3B%0D%0A%20%20%20%20childNodes%3A%20NameOrNameArray%3B%0D%0A%20%20%20%20constructor(value%2C%20parentNode)%20%7B%0D%0A%20%20%20%20%20%20%20%20this.value%20%3D%20value%3B%0D%0A%20%20%20%20%20%20%20%20this.childNodes%20%3D%20%5B%5D%3B%0D%0A%20%20%20%20%20%20%20%20if%20(parentNode%20!%3D%20null)%20%7B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20parentNode.addChild(this)%3B%0D%0A%20%20%20%20%20%20%20%20%7D%0D%0A%20%20%20%20%7D%0D%0A%20%20%20%20addChild(childNode)%20%7B%0D%0A%20%20%20%20%20%20%20%20this.childNodes.push(childNode)%3B%0D%0A%20%20%20%20%7D%0D%0A%20%20%20%20searchChildNodes(valueToSearch)%20%7B%0D%0A%20%20%20%20%20%20%20%20for%20(var%20element%20of%20this.childNodes)%20%7B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20(element.value%20%3D%3D%20valueToSearch)%20%7B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20element%3B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20%0D%0A%20%20%20%20%20%20%20%20%7D%0D%0A%20%20%20%20%20%20%20%20return%20null%3B%0D%0A%20%20%20%20%7D%0D%0A%7D%0D%0A%0D%0Aclass%20prefix_tree%20%7B%0D%0A%20%20%20%20mother_node%3A%20any%3B%0D%0A%20%20%20%20previous_node%3A%20any%3B%0D%0A%20%20%20%20stored_nodes%3A%20any%5B%5D%3B%0D%0A%20%20%20%20constructor(value)%20%7B%0D%0A%20%20%20%20%20%20%20%20this.mother_node%20%3D%20new%20node(null%2C%20null)%3B%0D%0A%20%20%20%20%20%20%20%20this.previous_node%20%3D%20this.mother_node%3B%0D%0A%20%20%20%20%20%20%20%20this.stored_nodes%20%3D%20%5B%5D%3B%0D%0A%20%20%20%20%20%20%20%20%2F%2Fconsole.log(this.previous_node%2C%20this.mother_node)%3B%0D%0A%20%20%20%20%7D%0D%0A%20%20%20%20addToTree(StringOrNumber)%20%7B%0D%0A%20%20%20%20%20%20%20%20this.previous_node%20%3D%20this.mother_node%3B%0D%0A%20%20%20%20%20%20%20%20for%20(var%20element%20of%20StringOrNumber.split(''))%20%7B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20console.log(element%2C%20this.previous_node%20)%20%3B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20oldNode%20%3D%20this.previous_node.searchChildNodes(element)%3B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20(oldNode%20%3D%3D%20null)%20%7B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20var%20newNode%20%3D%20new%20node(element%2C%20this.previous_node)%3B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20this.stored_nodes.push(newNode)%3B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20this.previous_node%20%3D%20newNode%3B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%20else%20%7B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20this.previous_node%20%3D%20oldNode%3B%0D%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%20%20%20%0D%0A%20%20%20%20%20%20%20%20%7D%0D%0A%20%20%20%20%7D%0D%0A%7D%0D%0A%0D%0Avar%20trie%20%3D%20new%20prefix_tree(null)%3B%0D%0Atrie.addToTree(%22to%22)%3B%0D%0Atrie.addToTree(%22tea%22)%3B%0D%0Aconsole.log(trie.stored_nodes)%3B%0D%0A) at the [typescript playground](https://www.typescriptlang.org/play/).

However, our work is not done yet. We need to implement a way to search the trie for our data. 
Here we go:
```typescript
searchInTree(StringOrNumber) {
    this.previous_node = this.mother_node;
    for (var element of StringOrNumber.split('')) {
        var oldNode = this.previous_node.searchChildNodes(element);
        if (oldNode == null) {
            return false;
        }
    }
    var oldNode = this.previous_node.searchChildNodes(null);
    if (oldNode == null) {
        return false;
    }
    return true;
}
```
Testing this
```typescript
var trie = new prefix_tree(null);
trie.addToTree("to");
trie.addToTree("tea");
console.log(trie.stored_nodes);
reply = trie.searchInTree("toe");
console.log(reply); // false
reply = trie.searchInTree("to");
console.log(reply); // true
```

And so, we have ourselves a trie. Do check out the code in the 
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMjg0MTg3MTAsLTE0MzE1ODQ5MTAsLT
EzMDkxNTU1NCwtMjkyODY0Njc2LC02MTQyMTA5OTUsLTk0NjE4
NjQzOV19
-->
---

tags: 
  - DOM

---
**The DOM**

the DOM is part of a standardized API where each HTML element is represented by an object - hence the "object model" in the name; each element has particular properties and methods associated with it (depending on the elements type) and each object is able to  have siblings and parents

the base type of elements is Node, which contains methods for traversing the tree

![[./_resources/Untitled_Note.1.resources/dom_types.png]]

an HTML document can be considered a tree of elements; each element is considered the child of the element that encloses it, and could be considered the ancestor of the elements it encloses

in terms of the DOM tree, the **HTML document itself** is the **Document** object and is at the root of the DOM tree

the DOM name for an HTML attribute is the camelCase name of that attribute - tabindex in HTML is tabIndex in JavaScript

---
---
**Element Hierarchy**

How objects **nest** in each other

* if you put an element within another, the former element is a **child** of the former
	* if you put a **paragraph** in a **body** element, the paragraph is considered a child of the body

How **text styling** gets passed down through this hierarchy

* styling of a parent element will affect the child elements
	* so, how I change the styling of the **body** element will alter all the paragraph elements within that body
		* child elements can **override** the parent style, though this must be made explicit 

Size

* Most elements are sized by the content inside them, so as  you add more content the given element will get larger
	* parent elements can be defined with **fixed values** so that the normal document flow is overridden and better controlled

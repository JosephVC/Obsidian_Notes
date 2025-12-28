---
---
**General React Notes**

**<div id="root"></div>** is called the root **DOM node** because everything inside that div will be handled by the React DOM

* React apps often have just a single **DOM node**, but if need be  you can have as many as you like

the **\--save** flag tells react that a dependency is meant for **production**
the **\--save-dev** tells react the dependencies are for **development**, and thus don't need to be pushed to the production server

* in the package.lock file, the above creates something like this:
	* ![[./_resources/Untitled_Note.resources/unknown_filename.png]]

**React is client-side code**

Technically React is a library but is referred to as a framework.

**Why use it?**

* makes front-end JS much easier
* uses self-contained, independent components with their own state
* allows for creation of interactive UIs
* has a virtual DOM
* allows JSX to easily incorporate JS into markup
* good when working with teams

**thinking in terms of components**

* items on a React page are all separate components

**React State**

* Components can have state, which is an object that determines how that component renders and behaves
	* ![[./_resources/Untitled_Note.resources/unknown_filename.1.png]]
* there is also an application level state by using a state manager like **Redux** or React's own context API

when using react native for creating web apps, you don't need **react-dom**, as there's no DOM to work with

the **react-scripts** dependency is created by create-react-app and has to do with the dev server

**Index.html**
Because React is considered a single-page application it runs through a single html file

* in the index.html, the will be a <div> tag with an id of "root"
* this also allows you to use a bootstrap CDN or something else

the **render()** method inside the main class is called the **life cycle method** and is one that is required it's needed to render the component in the browser

* it returns JSX, which is an easier way to write JS in the browser
	* one big difference is t hat you can't use the **class** attribute, but need to use **className**  

in VSCode, you can type **rce \[tab key\]** to generate a generic React class

anytime you use map, you will need keys, as the map function is creating a list of items

**PropTypes** 

PropTypes are a way of validating the properties a component should have; we can set the type of property and whether they are required

**Styling React**

here is a good example of simple styling in the React app itself
 ![[./_resources/Untitled_Note.resources/unknown_filename.2.png]]

You can define the background color in a single line above, but remember that would require double brackets

the below is a lengthy way to get a line through an item depending on whether it's true or false

![[./_resources/Untitled_Note.resources/unknown_filename.4.png]]

there's a more elegant way to do this using a **ternary operator** (using a question mark as a more elegant way than writing out a whole if/else statement)

![[./_resources/Untitled_Note.resources/unknown_filename.3.png]]

**Events**

We need to add checkboxes that consider our events 

![[./_resources/Untitled_Note.resources/unknown_filename.5.png]]

There is a way to use props to ensure when we check something complete it actually does something

so, we say we give props to **markComplete** in our **TodoItem**.js file
![[./_resources/Untitled_Note.resources/unknown_filename.6.png]]

then we go 'up the tree" to our Todo.js file (which calls on TodoItem) and create the prop

![[./_resources/Untitled_Note.resources/unknown_filename.7.png]]
**using React Router to point to new web pages**

React router can be used to point to new web pages, such as an About page (which is created as a separate About.js component)

![[./_resources/Untitled_Note.resources/React-component-about.png]]

Within the components folder, you can have separate folders for the layout of the page and also JS components for individual pages

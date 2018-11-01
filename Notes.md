# Notes from Mosh's React Course

## Getting Started

1. What is React?

   - React is a JavaScript library for building user interfaces
   - developed at Facebook in 2011
   - more popular than Angular or Vue
   - the Component is the core idea behind React, they are independent and reusable. All React apps contain at least one component (App) and usually a tree of components below it (e.g. navbar, profile, trends, feed, etc.)
   - Component is usually a JavaScript class with a State and a Render method
   - Render() is responsible for describing what the UI should look like, the output is a React Element (js object that maps to a DOM element) that is a lightweight representation of the real DOM element
   - When the State is changed, a new React Element is created
   - React will compare the new element (and its children) to the previous one and update whatever is changed
   - Virtual DOM is what's created through the React Elements, and it takes the place of the real DOM
   - React gets its name from its reactions to state changes
   - Angular and React are similar in that both use components for rendering UI, but Angular is a framework whereas React is a view library that only takes care of the view and the view's syncing; this allows for combining React with other libraries

2. Setting Up the Development Environment

   - uses Node package manager (npm) which requires nodejs installed
   - in terminal: `npm i -g create-react-app`
   - Download extension for vscode: Simple React Snippets

3. Your First React App

   - in terminal, Use create-react-app package to create new react app: `create-react-app <name>`
   - again in terminal, from root of newly created react app, run: `npm start` --> launches development browser on port 3000 and opens in browser
   - in public/index.html, `<div id-="root"></div>` is where this react app is going to render
   - src/App.test.js is a basic component that is responsible for rendering the initial black banner
   - src/App.js has a ES6 class called "App" that extends "Component" that contains render() and returns jsx syntax that looks like html; Babel (modern js compiler) is used to convert jsx syntax to plain js code that browsers understand
   - also in src/ are App.css that styles components and index.js that works as an entrypoint for the application

4. Hello World

   - delete all files in src/ in order to create everything from scratch
   - first create index.js file and import objects from modules
   - browser will automatically reload
   - jsx expression will always output object (a react element)
   - call `ReactDom.render(element, document.getElementById('root'))`
   - `<h1>Hello World</h1>` is a simple element, but normally an entire app component tree will be rendered

5. Custom Configs

   - advanced developers may want to customize configurations, like webpacks, by ejecting the React app from the terminal

6. Full-stack Architecture

   - Mosh will use node express and mongoDB for the purposes of this course to learn how to communicate with the backend from React

7. Course Structure

   - JavaScript features required for React
   - components
   - composing components (passing data between components and making them interact)
   - tables with pagination, sorting, and searching
   - forms with validation
   - routing and navigation (for multiple page apps)
   - http services and communication w/ backend
   - authentication and authorization
   - deployment

NOTE: Why is Redux not taught with this course?

    - React should be learning properly before Redux
    - a trend and common misconception is that React and Redux should be used together; this is why some React developers know how to use the latest tools and patterns but don't understand how they work
    - the creator of Redux says that not every project needs Redux
    - Mosh will have a separate course on Redux for those who compelete this React course

## ES6 Refresher

1. Introduction

2. Let vs Var vs Const

   - `var` restricts scope to a function, not a coding block
   - `let` restricts scope to a coding block and is maleable
   - `const` restricts scope to a coding block and is not maleable

3. Objects

   - functions that are set as values of keys in objects are known as "methods"; es6 syntax does not require a colon to separate the key and the function value, i.e. `walk() {}`
   - when targeting keys within an object, you can reference a key with either dot or square bracket notation; dot is used when you know what property you want to access, while square brackets are used when you are not sure because you may be accepting input from an input field from a client

4. The this Keyword
5. Binding this
6. Arrow Functions
7. Arrow Functions and this
8. Array.map Method
9. Object Destructuring
10. Spread Operator
11. Classes
12. Inheritance
13. Modules
14. Named and Default Exports

## Components

1. Introduction

   - Looking at basic e-commerce cart with navbar and cart item count, quantity of each item, add and subtract quantity buttons, delete item button, and counters that update with the press of each button (including some css changes when count gets to zero)

2. Setting up the Project

   - create-react-app counter-app
   - install boostrap 4.1.1

3. Your First React Component

   - create folder (components) and in that folder, a file (counter.jsx); important to use .jsx for better code completion
   - use code snippets (i.e.) from Simple React Snippets extension to speed up typing
   - export class Counter from components/counter.jsx, then import in index.js

4. Specifying Children

   - adding an increment button
   - multiple jsx expressions must have a single parent element
   - React.Fragment as an element can replace the parent element (doesn't actually create anything once rendered in the browser, eliminates unnecessary div)

5. Embedding Expressions

   - instead of hardcoding "Hello World" set it up to display dynamically using "state" property
   - state is a special property, an object that collects any data the component needs
   - use `{this.state.<state property>}`
   - jsx expressions are just like js expressions and can be stored in variables or returned, etc.

6. Setting Attributes

   - adding an image element and setting the value of source attribute dynamically
   - in the state object, add imageUrl property
   - in the img element, use curly braces to render an element dynamically for src
   - for styling css, set a "styles" object below the state, then use the word "style" as an attribute for an element and reference the styles object with curly braces
   - you can also use double curly braces, e.g. `{{fontSize:30}}` instead of referencing the styles object

7. Rendering Classes Dynamically

   - change color of count button based on count number
   - for className attribute, set value to {} and use t-his
   - refactor getBadgeColor() by moving it outside of render() to keep render() clean

8. Rendering Lists

   - use .map() to dynamically render an array
   - for a list, enter a new property in the state object, then set an array to the value of that property (e.g. `tags: ["tag1", "tag2", "tag3"]`)
   - now you can reference that property to dynamically render the list, just use {}
   - remember to also set up a unique "key" (react word for id attribute) for each item in that list, this can be dynamically rendered as well
   - it doesn't matter if the key is repeated in a different list, it just needs to be unique in the scope of each list

9. Conditional Rendering

   - there are two ways to do this: first, create a separate method, e.g. `renderTags()` and include an if statement; second, use the `&&` (a.k.a. the logical AND) with the condition first, and the action second, if the condition is false, the action will not happen

10. Handling Events

    - add the property in the jsx element, e.g. `onClick` and set it to `{this.<method name>}` without parentheses following the method

11. Binding Event Handlers

    - there are two ways to bind event handlers
    - first way: before the method where you are using t-his, call `constructor()`, then inside call `super()`, finally, set `this.<method using t-his> = this.<method using t-his.bind(this)`
    - second way (cleaner, but might not work in some cases): just set up the method as an es6 arrow function

12. Updating the State

    - use `this.setState({ })` within a function to bring the DOM insync with the virtual DOM
    - this allows you to directly reference and modify one of the state's properties (e.g. `count: this.state.count + 1`)

13. What Happens When State Changes

    - Virtual DOM is updated with each click of increment button, then React compares the DOM to the virtual DOM, notices the changes, and updates only the relevant parts of the DOM

14. Passing Event Arguments

    - when you need to pass an argument in an event, in `render()`, set the event to an arrow function and pass an argument within the event handler call

15. Setting Up the Vidly Project

    - npm install bootstrap and font-awesome
    - in app.js create the element: `<main className="container"></main>`
    - download attached zip with fakeGenreServices.js and fakeMovieServices.js

16. Exercises

    - Create a table of movies with delete-by-id functionality
    - movies can be retrieved from js file as array attached to lecture in zip, files include functions for retrieving all movies and by id

17. Building the Movies Component

    - code table by copying bootstrap 4 table model and zen coding technique
    - use `getMovies()` in the state and `.map` to render movies within `<tbody>`

18. Deleting a Movie

    - add a new blank `<th>` and a `<td>` with delete button
    - in the button, handle a click event by calling a method, `handleDelete`
    - create `handleDelete()` as an arrow function outside `render()`
    - make the click event handler a method, `onClick({})`
    - in `movies.map` render method, set the key attribute in `<tr>` to `{movie._id}`
    - create new movies array in the `handleDelete()`, use `.filter()` to return only movies that don't equal movie.\_id
    - then, still in `handleDelete()`, use `this.setState({movies})` to update the movies array in the state

19. Conditional Rendering

    - inside of `render()`, add conditional statement using `if` to return `<p>There are no movies in the database.</p>`
    - use another `<p>` above the table, but below the second return statement to access the movies' length
    - to make the code cleaner, use object destructuring and set a `const` just below `render()` like so: `const { length: count} = this.state.movies`
    - call `{count}` inside of the `<p>` statement where you tell how many movies are in the database
    - because there needs to be one parent, use `<React.Fragment>` to encapsulate the `<p>` and table

20. Summary

    - learned about JSX, Rendering Lists, Conditional Rendering, Handling Events, and Updating the State

## Composing Components

1. Introduction

   - Topics include: Passing Data, Raising and Handling Events, Composing Multiple Components in Sync, Composing Functional Components, Creating Lifecycle Hooks

2. Composing Components

   - instead of hard-coding every counter in `render()`, make them an array value of a key (counters) in the state object
   - for each item in the array, use curly braces
   - in `render()`, use `.map()` to display each counter component, like so
     `{this.state.counters.map(counter => <Counter key={counter.id} />)}`

3. Passing Data to Components

   - Every React component has a property called `props`
   - use `this.props.value` as a value of a property in the state, then reference it when dynamically rendering the value as an attribute of an element or component

4. Passing Children

   - special prop, `children`, can be used when we want to pass something between the opening and closing tag of an element and then reference it somewhere else, i.e. `this.props.children`

5. Debugging React Apps

   - Use React Developer Tools extension for chrome (made by Facebook), it allows for quick debugging through the developer tools console in chrome

6. Props vs State

   - Props includes data that we give to a component and is read-only (cannot change the input to the component inside of the component)
   - State includes data that is local/private to that component (other components can't access that data)
   - to modify an input during the life cycle of a component, then you get the input and put it in the state

7. Raising and Handling Events

   - Add "Delete" button in counter.jsx, just after the increment button inside of `render()`
   - the component that owns a piece of the state, should be the one modifying it
   - modify counter component to raise an event, `onDelete()`, then counters.jsx will handle the event, `handleDelete()`
   - concept of raising and handling events is common in many user-interface libraries
   - add new method to counters.jsx, and pass a reference to that method, via props, to counter.jsx

8) Updating the State

   - in counter.jsx, pass the id of the counter to the delete button by adding an arrow function inside the {} for `onClick()`, then call `this.props.onDelete(this.props.id)`
   - in counters.jsx, add `handleDelete()` as an arrow function with `counterId` as an argument, then declare a const inside, set it to `this.state.counters.filter(c => c.id != counterId)`, and finally, set the state with `this.setState({ counters })`; this makes a new array excluding the item that was clicked, and then resets the state so that React will render the new array
   - why pass `id` and `key` attributes in `render()` in counters.jsx? `key` is used internally by React (not accessible in counter.jsx)
   - to avoid having to write every prop in `<Counter/>` in counters.jsx `render()`, simply write `counter={counter}` to pass the counter object itself, that way it will include all properties you add later

9) Single Source of Truth

   - Single Source of Truth is currently missing from the project
   - create a Reset button
   - each component has its own local state and the value is currently disconnected from the value property for each counter in the array
   - to fix this, we need to remove the local state in counter.jsx and have a single source of truth

10) Removing the Local State

    - in counter.jsx, remove local state so that React relies on the props to receive data for the component
    - a "Controlled" component doesn't have it's own local state, it receives data via props and raises events whenever data needs to be changed (entirely controlled by it's parent)

11. Multiple Components in Sync

    - in order to get multiple components to sync, you need to establish a hierarchy with parents and children
    - App.jsx should be at the top, then navbar.jsx and counters.jsx, then branching off counters.jsx is counter.jsx
    - hierarchy is established through import and exports at the top and bottom of .jsx files (respectively)
    - to pass state information down to a child, counter.jsx gets data from counters.jsx via props

12. Lifting the State Up

    - refactor code to lift the state from the `counters.jsx` to `App.js`
    - children can inherit methods belonging to parents via `this.props.<method>`

13. Stateless Functional Components

    - `navbar.jsx` doesn't have or need a state, it inherits props from it's parents, so it is a "stateless functional component"
    - some React developers like to use SFCs when a state is not necessary, comes down to preference
    - without state, there is no props inherited, so `props` must be passed as an argument in the arrow function

14. Destructuring Arguments

    - to avoid repeating `this.props.` use object descructuring to pull the relevant methods and reference them by name only
    - this should be done inside `render()` but before `return()`

15. Lifecycle Hooks

    - components go through the following phases:
    - MOUNT is when an instance of a component is created and inserted into the DOM
    - methods can be added to the components that REACT automatically recognizes, they are known as LIFECYCLE HOOKS (in MOUNT, they are constructor, render, componentDidMount)
    - React calls these methods in order
    - UPDATE is when the state or props of a component are changed (LIFECYCLE HOOKS for this phase are render and componentDidUpdate)
    - UNMOUNT is when a component is removed from the DOM (e.g. deleting a counter), the LIFECYCLE HOOK for this phase is componentWillUnmount)

16. Mounting Phase

    - when a component is MOUNTED, that means it is in the DOM

17. Updating Phase

    - happens whenever the state or props of a component change
    - involves a change which is then rendered in the virtual DOM; React compares the virtual DOM and actual DOM and updates only the changes
    - `componentDidUpdate(prevProps, prevSate)` allows making an AJAX call to get new data from the server

18. Unmounting Phase

    -

19. Exercise-Decrement Button

20. Solution - Decrement Button

21. Exercise - Like Component

22. Solution - Like Component

23. Summary

## Pagination, Filtering, and Sorting

## Routing

## Forms

## Calling Backend Services

## Authentication and Authorization

## Deployment

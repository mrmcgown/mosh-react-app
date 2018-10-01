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
- also in src/ are App.css that styles components and index.js that works as entrypoint for the application

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

-

2. Let vs Var vs Const

- `var` restricts scope to a function, not a coding block
- `let` restricts scope to a coding block and is maleable
- `const` restricts scope to a coding block and is not maleable

3. Objects

- functions that are set as values of keys in objects are known as "methods"; es6 syntax does not require a colon to separate the key and the function value, i.e. `walk() {}`
- when targeting keys within an object, you can reference a key with either dot or square bracket notation; dot is used when you know what property you want to access, while square brackets are used when you are not sure because you may be accepting input from an input field from a client

4. The this Keyword

-

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
- use code snippets from Simple React Snippets extension to speed up typing
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

-

## Composing Components

## Pagination, Filtering, and Sorting

## Routing

## Forms

## Calling Backend Services

## Authentication and Authorization

## Deployment

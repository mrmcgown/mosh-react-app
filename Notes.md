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

## Components

## Composing Components

## Pagination, Filtering, and Sorting

## Routing

## Forms

## Calling Backend Services

## Authentication and Authorization

## Deployment

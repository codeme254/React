# Introduction
React is a JavaScript library for building user interfaces.

React was developed by Facebook in 2011 and was open-sourced in 2013.

React is not a framework—it is not even exclusive to the web, it is used with other libraries to render to certain
environments. For instance, react native can be used to build mobile applications.

To build for the web, developers use React together with ReactDOM.

React DOM is a separate package that enables React to update and render UI components on the web browser by directly
interacting with the browser's Document Object Model (DOM), ensuring smooth, dynamic user experiences.

## Why not "Just JavaScript"
- Writing complex JavaScript code quickly becomes cumbersome.
- Complex JavaScript code quickly becomes error-prone.
- Complex JavaScript code often is hard to maintain.
- React offers a simpler mental model.

## Setting up a React project
There are two CLI tools for setting up a React project:
- create-react-app ([deprecated](https://react.dev/blog/2025/02/14/sunsetting-create-react-app))
- using vite

To set up a React project using vite, run:
```Bash
npm init vite
```

or

```Bash
npm init vite@latest
```

This will walk you through a utility that will help you set up a React project.
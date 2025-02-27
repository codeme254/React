# Introduction
React is a JavaScript library for building user interfaces.

React was developed by Facebook in 2011 and was open-sourced in 2013, it is currently maintained by individual
developers and other companies.

React is not a framework—it is not even exclusive to the web, it is used with other libraries to render to certain
environments. For instance, react native can be used to build mobile applications.

To build for the web, developers use React together with ReactDOM.

React DOM is a separate package that enables React to update and render UI components on the web browser by directly
interacting with the browser's Document Object Model (DOM), ensuring smooth, dynamic user experiences.

## Why we need React
### Efficient UI Updates with Virtual DOM
React uses a Virtual DOM to efficiently update only the necessary parts of the UI when data changes, instead of 
reloading the entire page. This makes apps faster and more responsive.

### Component-Based Architecture
React promotes reusable components, reducing code duplication.

Components make large applications easier to manage and scale.

### Declarative Syntax
React’s JSX (JavaScript XML) makes UI code more readable and maintainable.

Instead of manually manipulating the DOM, you describe the UI state, and React ensures it updates accordingly.

### State Management
React makes handling dynamic data easier with its state and props system.

We will learn more about state management later


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
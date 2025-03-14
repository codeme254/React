# React Query

React query is a library for fetching data in a React application.

It is a powerful data-fetching and state management library for React applications.

## Why we need a data fetching library
React is a UI library, it has no specific pattern for data fetching.

To perform data fetching in React, we make use of the `useEffect` hook and the `useState` hook to maintain
component state like loading, error or resulting data.

If the data is needed throughout the app, we tend to use state management libraries.

Most of the state management libraries are good for working with **client state** for example theme.

State management libraries are not great for working with <b><u>asynchronous/server state</u></b>


## Client State VS Server State
Client state is persisted in your app memory and accessing or updating it is synchronous.

Server state, on the other hand, is persisted remotely and requires asynchronous APIs for fetching or updating.


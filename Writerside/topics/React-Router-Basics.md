# React Router Basics

Once you have `react-router-dom` installed, there are three things you need to do to use it:
- Setup your router
- Define your routes
- Handle navigation

## Configuring the router
This is the easiest step by far in setting up the router.

All you need to do is import the specific router you need (`BrowserRouter` for the web) and wrap your entire 
application in that router.

```JavaScript
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import App from "./App.jsx";
import { BrowserRouter } from "react-router-dom";
import "./index.css";

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </StrictMode>,
);
```

## Defining Routes
The next step in React Router is to define your routes. 

This is generally done at the top level of your application, such as in the App component, but can be done 
anywhere you want.

Defining routes is as simple as defining a single `Route` component for each route in your application and then putting 
all those `Route` components in a single `Routes` component.

Whenever your URL changes, React Router will look at the routes defined in your `Routes` component, and it will render 
the content in the `element` prop of the `Route` that has a path that matches the URL.

In the example below, if our URL was `/books` then the `BookList` component would be rendered.

```JavaScript
import { Routes, Route } from "react-router-dom";
import Home from "./Home";
import BookList from "./BookList";

function App() {
  return (
    <>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/books" element={<BookList />} />
      </Routes>
    </>
  );
}

export default App;
```

The nice thing about React Router is that when you navigate between pages, it will only refresh the content inside 
your Routes component. All the rest of the content on your page will stay the same which helps with performance 
and user experience.

## Handling Navigation
The final step to React Router is handling navigation.

Normally in an application you would navigate with anchor tags, but React Router uses its own custom `Link` 
component to handle navigation.

This `Link` component is just a wrapper around an anchor tag that helps ensure all the routing and conditional 
re-rendering is handled properly so you can use it just like your would a normal anchor tag.

```JavaScript
import { Link } from "react-router-dom";

function Header() {
  return (
    <div>
      <Link to="/">Home</Link>
      <Link to="/books">Books</Link>
    </div>
  );
}

export default Header;
```

In our example, we added two links to the home and books page. You will also notice that we used the `to` prop to 
set the URL instead of the `href` prop you are used to using with an anchor tag.

We can also use the `NavLink` component for navigation.

The `NavLink` component works similar to `Link` component, but it provides extra styling to indicate the active 
route in the navbar based on the active URL.

```JavaScript
import { NavLink } from "react-router-dom";

function Header() {
  return (
    <div>
      <NavLink
        className={({ isActive }) => (isActive ? "active-link link" : "link")}
        to="/"
      >
        Home
      </NavLink>
      <NavLink
        className={({ isActive }) => (isActive ? "active-link link" : "link")}
        to="/books"
      >
        Books
      </NavLink>
    </div>
  );
}

export default Header;
```
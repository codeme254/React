# Advanced Routing

There's a lot we can do with React Router to make more complex routes easier to read, and overall much more functional.

This can be done through the following techniques.

1. Dynamic Routing
2. Routing Priority
3. Nested Routes
4. Multiple Routes
5. `useRoutes` hook

## Dynamic Routing
The simplest and most common advanced feature in React Router is handling dynamic routes.

In our example, let’s assume that we want to render out a component for individual books in our application.

We could hardcode each of those routes, but if we have hundreds of books or the ability for users to create books,
then it is impossible to hardcode all these routes.

Instead, we need a dynamic route:

```JavaScript
function App() {
  return (
    <>
      <Header />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/books" element={<BookList />} />
        <Route path="/books/:id" element={<Book />} />
      </Routes>
    </>
  );
}
```
The final route in the above example is a dynamic route that has a dynamic parameter of `:id`.

Defining dynamic routes in React Router is as simple as putting a colon in front of whatever you want the dynamic part
of your route to be. In our case, our dynamic route will match any URL that starts with `/books` and ends with some 
value. For example, `/books/1`, `/books/bookName`, and `/books/literally-anything` will all match our dynamic route.


Pretty much always, when you have a dynamic route like this, you want to access the dynamic value 
in your custom component which is where the `useParams` hook comes in.

The `useParams` hook takes no parameters and will return an object with keys that match the dynamic parameters 
in your route. In our case, our dynamic parameter is `:id` so the `useParams` hook will return an object that has 
a key of `id` and the value of that key will be the actual `id` in our URL.

```JavaScript
import { useParams } from "react-router-dom";

function Book() {
  const params = useParams();
  return (
    <div>
      <h1>Book {params.id}</h1>
    </div>
  );
}

export default Book;
```

## Routing Priority
When we were just dealing with hard-coded routes, it was pretty easy to know which route would be rendered, but when 
dealing with dynamic routes it can be a bit more complicated.

Take these routes, for example:

```JavaScript
<Route path="/books/:id" element={<Book />} />
<Route path="/books/new" element={<NewBook />} />
```

If we have the URL `/books/new`, which route would this match? Technically, we have two routes that match. 
Both `/books/:id` and `/books/new` will match since the dynamic route will just assume that new is the `:id` 
portion of the URL so React Router needs another way to determine which route to render.

In older versions of React Router, whichever route was defined first would be the one that is rendered, so in our case,
the `/books/:id` route would be rendered, which is obviously not what we want.

Luckily, later versions of React Router changed this, so now React Router will use an algorithm to determine which route 
is most likely the one you want. In our case, we obviously want to render the `/books/new` route, so React Router 
will select that route for us.

## Nested Routes
Consider the example below:
```JavaScript
function App() {
  return (
    <>
      <Header />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/books" element={<BookList />} />
        <Route path="/books/:id" element={<Book />} />
        <Route path="/books/new" element={<NewBook />} />
      </Routes>
    </>
  );
}
```

We have three routes that start with `/books` so we can nest those routes inside each other to clean up our routes.

```JavaScript
function App() {
  return (
    <>
      <Header />
      <Routes>
        <Route path="/" element={<Home />} />

        <Route path="/books">
          <Route path="" element={<BookList />} />
          <Route path=":id" element={<Book />} />
          <Route path="new" element={<NewBook />} />
        </Route>

      </Routes>
    </>
  );
}
```

## Shared Layouts
Let's say we want a nav that specifically allows us to navigate between `BookList` page, `Book` page and `NewBook` page,
(book related component nav). To do this normally, we would need to make a shared component to store this navigation 
and then import that into every single book related component.

This is a bit of a pain, though, so React Router created its own solution to solve this problem.

If you pass an `element` prop to a parent route, it will render that component for every single child Route, 
which means you can put a shared nav or other shared components on every child page with ease.

In the shared component, we then use the `Outlet` component from `react-router-dom`:

```JavaScript
function App() {
  return (
    <>
      <Header />
      <Routes>
        <Route path="/" element={<Home />} />

        <Route path="/books" element={<BooksLayout />}>
          <Route path="" element={<BookList />} />
          <Route path=":id" element={<Book />} />
          <Route path="new" element={<NewBook />} />
        </Route>
      </Routes>
    </>
  );
}
```

```JavaScript
function BooksLayout() {
  return (
    <div>
      <Link to="/books">All books</Link>
      <Link to="/books/new">New Book</Link>

      <Outlet />
    </div>
  );
}
```

The way our new code will work is whenever we match a route inside the `/book` parent Route it will render the 
`BooksLayout` component which contains our shared navigation. Then whichever child Route is matched will be 
rendered wherever the `Outlet` component is placed inside our layout component.

The `Outlet` component is essentially a placeholder component that will render whatever our current page’s content is.

## `useRoutes` hook
You can use a JavaScript object to define your routes instead of JSX if you prefer.

```JavaScript
function App() {
  const routes = useRoutes([
    { path: "/", element: <Home /> },
    {
      path: "/books",
      element: <BooksLayout />,
      children: [
        { path: "", element: <BookList /> },
        { path: "new", element: <NewBook /> },
        { path: ":id", element: <Book /> },
      ],
    },
  ]);

  return (
    <>
      <Header />
      {routes}
    </>
  );
}
```
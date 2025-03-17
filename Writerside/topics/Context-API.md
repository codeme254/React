# Context API

When state needs to be shared across many nested components, passing props can become tedious (prop drilling).

React's context API solves this.

`useContext` is an inbuilt React hook that helps us to manage context.

The goal is to establish a single source of truth, creating a centralized location where any component can access the
required data. Any component that wants to update the data will also have to update it there.

The "centralized location" is known as **context** in the `useContext` hook, state management frameworks like redux
and Zustand call it **store**

The steps are:
- Create the context.
- Provide the context to all components that need it.
- Consume the context in child components.

## Step 1: Create the context
It is a convention to create each context in a separate js file that is placed inside a folder called context.

To create a context, we use the `createContext` hook form react.

```JavaScript
import { createContext } from "react";

const UserContext = createContext();

export default UserContext;
```


## Step 2: Provide the context
To provide the context, we import it in the parent component and wrap all the children that need access to the 
context with the context.

When enclosing all the children components within the context, we pass a prop to the context called **value** which
takes in an object of the state that is to be shared:

```JavaScript
import UserContext from "./context/UserContext";
import Dashboard from "./Dashboard";
import Profile from "./Profile";
function App() {
  const fullName = "Marcus Aurelius";
  const username = "marcus001";
  return (
    <UserContext.Provider value={{ fullName, username }}>
      <Dashboard />
      <Profile />
    </UserContext.Provider>
  );
}
```

## Step 3: Consume the context
To consume the context and thus the state, we sue the `useContext` hook.

We pass into `useContext` hook the context that we want to consume; the hook returns an object containing
all the states present in the context.
```JavaScript
import { useContext } from "react";
import UserContext from "./context/UserContext";

function Dashboard() {
  const { fullName, username } = useContext(UserContext);
  return (
    <div>
      <h1>Dashboard</h1>
      <h2>Full Name: {fullName}</h2>
      <h2>Username: {username}</h2>
    </div>
  );
}
```

```JavaScript
import { useContext } from "react";
import UserContext from "./context/UserContext";

function Profile() {
  const { fullName, username } = useContext(UserContext);
  return (
    <div>
      <h1>Profile</h1>
      <h2>Full name: {fullName}</h2>
      <h2>Username: {username}</h2>
    </div>
  );
}
```
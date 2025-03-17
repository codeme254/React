# Zustand

Zustand is a fast, small and scalable state management solution.

Zustand is primary dependent on hooks.

To use zustand, you need to install it:

```JavaScript
npm install zustand
```

After installation, all you need to do is to create a store and bind that store to the components that need it and
that's it.

## Important things to understand before using Zustand
- **store**: the store is an object that holds the state and state management logic centralizing the application's 
state.
- **set**: the set function is used to update the state in the store. It allows state change by directly setting new
values.
- **actions**: are functions defined within the store that encapsulate specific state transitions or operations, they
use the **set** function to modify state.

## Setting up Zustand store
The zustand store is a hook, and we can put anything within it, primitives, objects, functions e.t.c.

To create a store, we use a function that takes in a callback function called **set** as its parameter, this function
will then return an object containing the state and all the functions (actions) that will utilize the set function
to manipulate the state.

Zustand provides a function called **create** that takes the above function as an argument and returns the store
which can then be used throughout the application.

```JavaScript
import { create } from "zustand";

function counterStore(set) {
  return {
    count: 0,

    incrementCount: function () {
      set(function (previousState) {
        return { count: previousState.count + 1 };
      });
    },

    decrementCount: function () {
      set(function (previousState) {
        return { count: previousState.count - 1 };
      });
    },
  };
}

const useCounterStore = create(counterStore);

export default useCounterStore;
```

## Using the store
To use the store, we import it in the relevant component and access the necessary state and actions by calling
the store and selecting the desired variables and actions as shown:

```JavaScript
import useCounterStore from "./store/counterStore";
function App() {
  const count = useCounterStore((state) => state.count);
  const incrementCount = useCounterStore((state) => state.incrementCount);
  const decrementCount = useCounterStore((state) => state.decrementCount);
  return (
    <div>
      <button onClick={incrementCount}>increment</button>
      <h1>{count}</h1>
      <button onClick={decrementCount}>decrement</button>
    </div>
  );
}

export default App;
```

## Persisting State
Persisting state refers to the process of saving the state of an application so that it can be maintained across
sessions or page reloads.

To persist state in zustand, we use **devtools and persist** functions from `zustand/middleware as shown`:

```JavaScript
...
const useCounterStore = create(
  devtools(persist(counterStore, { name: "count" })),
);

export default useCounterStore;
```
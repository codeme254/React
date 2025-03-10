# useEffect

The `useEffect` hook is a fundamental part of React that allows functional components to handle side effects.

A side effect in programming (especially in React) is anything a function does that affects something outside of itself.

These side effects include; fetching data from APIs, directly manipulating the DOM e.t.c.

`useEffect` hook is imported from react:

```JavaScript
import { useEffect } from 'react';
```

The `useEffect` hook takes in two arguments:
- The first argument is a function that is executed to handle the side effects.
- The second argument (optional) is an array of dependencies that determines when the effect runs.

## `useEffect` without any dependencies (runs on every render)
When `useEffect` is used without any dependencies, it runs after every render:

```JavaScript
import { useState, useEffect } from "react";

function App() {
  const [number, setNumber] = useState(0);

  useEffect(() => {
    console.log(`Component rendered ${number}`);
  });

  return (
    <div>
      <p>{number}</p>
      <button onClick={() => setNumber(number + 1)}>Increase</button>
    </div>
  );
}
```

## `useEffect` with an Empty Dependency Array (Runs Only Once on Mounting)

If you pass an empty dependency array (`[]`), useEffect runs only once.

```JavaScript
import { useState, useEffect } from "react";

function App() {
  const [number, setNumber] = useState(0);

  useEffect(() => {
    console.log(`Component rendered ${number}`);
  }, []);

  return (
    <div>
      <p>{number}</p>
      <button onClick={() => setNumber(number + 1)}>Increase</button>
    </div>
  );
}
```

A use case for this would be fetching data when a component loads.

## `useEffect` with Dependencies (Runs When Dependencies Change)
You can specify dependencies inside the array. The effect will only run if one of the dependencies changes.

```JavaScript
import { useState, useEffect } from "react";

function App() {
  const [number, setNumber] = useState(0);

  useEffect(() => {
    console.log(`Component rendered ${number}`);
  }, [number]); // effect will run each time number changes

  return (
    <div>
      <p>{number}</p>
      <button onClick={() => setNumber(number + 1)}>Increase</button>
    </div>
  );
}
```
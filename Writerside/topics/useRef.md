# useRef

`useRef` hook allows you to create a mutable reference that persists across renders without causing a re-render when 
it updates.

Unlike `useState`, changing a `useRef` value does NOT trigger a re-render.

It's often used for directly interacting with the DOM or storing values that need to persist between renders 
without affecting performance.


## Storing mutable values without re-renders
Call `useRef` at the top level of your component and optionally pass the initial value.

`useRef` returns an object with a single property:
- `current`: Initially, it’s set to the initial value you have passed. You can later set it to something else.
```JavaScript
import { useRef } from "react";

function App() {
  console.log("component rendered");
  const numberRef = useRef(10);

  function handleIncrement() {
    numberRef.current += 1;
    console.log(numberRef);
  }
  return (
    <div>
      <button onClick={handleIncrement}>Click me</button>
    </div>
  );
}
```

## Storing a DOM reference
One of the most common uses of `useRef` is to get a reference to a DOM element.

To do this, initialize the `useRef` hook and attach it to the DOM element using the `ref` prop.

```JavaScript
import { useRef } from "react";

function App() {
  const inputRef = useRef();

  function handleFocusInput() {
    inputRef.current.focus();
  }

  return (
    <div>
      <input type="text" placeholder="username" ref={inputRef} />
      <button onClick={handleFocusInput}>Focus on Input</button>
    </div>
  );
}
```
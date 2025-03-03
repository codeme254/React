# Manipulating the DOM with Refs

> React automatically updates the DOM to match your render output, so your components won’t often need to manipulate it.
However, sometimes you might need access to the DOM elements managed by React—for example, to focus a node, scroll to 
it e.t.c. There is no built-in way to do those things in React, so you will need a ref to 
the DOM node.


## Getting a reference to a node
To access a DOM node managed by React, first, import the useRef `Hook` (more about hooks later):

```JavaScript
import { useRef } from 'react';
```

Then, use it to declare a ref inside your component:
```JavaScript
const myRef = useRef(null);
```

Finally, pass your ref as the ref attribute to the JSX tag for which you want to get the DOM node:

```JavaScript
<div ref={myRef}>
```

The `useRef` Hook returns an object with a single property called `current`. Initially, `myRef.current` will be null.

When React creates a DOM node for this `<div>`, React will put a reference to this node into `myRef.current`.

You can then access this DOM node from your event handlers and use the built-in browser APIs defined on it.

```JavaScript
import { useRef } from "react";

function MyComponent() {
  const myRef = useRef(null);
  function handleClick() {
    myRef.current.classList.toggle("box");
  }
  return (
    <div>
      <div ref={myRef}></div>
      <button onClick={handleClick}>Click me</button>
    </div>
  );
}

export default MyComponent;
```
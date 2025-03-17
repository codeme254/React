# State Management
State management in React is crucial for handling data flow within an application.

It determines how components share and update state.

State in React represents the dynamic data of a component, which changes over time and triggers re-renders.

We can manage local state using the `useState` hook.

```JavaScript
import { useState } from "react";

function App() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <h1>{count}</h1>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
}
```
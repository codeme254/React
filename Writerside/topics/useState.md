# useState

The `useState` hook is one of the most fundamental and commonly used hooks in React, `useState` hook allows 
functional components to manage state.

State refers to information that can change over time as a result of user actions or other events.

`useState` hook is imported from `react`.

```JavaScript
import { useState } from 'react';
```

When we call the `useState` hook, it returns an array with two elements, the current state value and a function to
update the state; we also pass the initial value of our state as the argument to the `useState` call.

```JavaScript
import { useState } from "react";

function App() {
  const [number, setNumber] = useState(0);
  return (
    <div>
      <p>Number = {number}</p>
    </div>
  );
}
```

To update the state, we **MUST** use the state update function:

```JavaScript
import { useState } from "react";

function App() {
  const [number, setNumber] = useState(0);

  function handleAddNumber() {
    // number += 1 // WRONG
    setNumber(number + 1);
  }

  return (
    <div>
      <p>Number = {number}</p>
      <button onClick={handleAddNumber}>increment number</button>
    </div>
  );
}
```

## Using a function to calculate the initial state
Sometimes, the initial state is expensive to calculate, you can pass a function to the `useState` hook, the function
will only run once (on the first render).

```JavaScript
import { useState } from "react";

function App() {
  const [number, setNumber] = useState(function () {
    console.log("A very expensive calculation to derive number");
    return 10;
  });

  function handleAddNumber() {
    // number += 1 // WRONG
    setNumber(number + 1);
  }

  return (
    <div>
      <p>Number = {number}</p>
      <button onClick={handleAddNumber}>increment number</button>
    </div>
  );
}
```

## Updating State Based on The Previous State
We can also update state based on what the previous state was.

For this, we pass a callback function to the state
update function which takes the previous state as a parameter and returns a new state based on the previous state.

```JavaScript
import { useState } from "react";

function App() {
  const [number, setNumber] = useState(function () {
    console.log("A very expensive calculation to derive number");
    return 10;
  });

  function handleAddNumber() {
    setNumber(function (previousNumber) {
      console.log(`Previous Number ${previousNumber}`);
      return previousNumber + 1;
    });
  }

  return (
    <div>
      <p>Number = {number}</p>
      <button onClick={handleAddNumber}>increment number</button>
    </div>
  );
}
```

## Handling state with objects
We can also work with objects in our state:

```JavaScript
import { useState } from "react";

function App() {
  const [profile, setProfile] = useState({ name: "John", age: 25})

  return (
    <div>
      <p>Name: {profile.name}</p>
      <p>Age: {profile.age}</p>
    </div>
  );
}
```

### Updating an object state
When updating an object state, we use the `spread` operator.

```JavaScript
import { useState } from "react";

function App() {
  const [profile, setProfile] = useState({ name: "John", age: 25 });

  function handleUpdateAge() {
    setProfile({ ...profile, age: profile.age + 1 });
  }
  return (
    <div>
      <p>Name: {profile.name}</p>
      <p>Age: {profile.age}</p>
      <button onClick={handleUpdateAge}>Update Age</button>
    </div>
  );
}
```

### Why use `{...profile}`
State updates in React replace the entire state object. If you do:
```JavaScript
setProfile({age: profile.age + 1 });
```
You will end up losing all the other object properties. Using `{...profile}` ensures that all properties remain
while updating only one.

## Handling State with Arrays
We could also handle state with arrays:

```JavaScript
import { useState } from "react";

function App() {
  const [tasks, setTasks] = useState(["task 1", "task 2"]);

  function handleAddTask() {
    setTasks([...tasks, `Another task`]);
  }

  return (
    <div>
      {tasks.map((task) => (
        <p key={Math.random()}>{task}</p>
      ))}
      <button onClick={handleAddTask}>Add Task</button>
    </div>
  );
}
```
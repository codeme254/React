# Conditional Rendering

React allows you to render different UI elements based on different conditions, this feature is called
conditional rendering.

> Your components will often need to display different things depending on different conditions.

Conditional rendering can be achieved as follows:

## Using `if` statements
```JavaScript
function Greeting({ isLoggedIn }) {
  if (isLoggedIn === true) {
    return <h1>Welcome Back</h1>
  } else {
    return <h1>Please log in</h1>
  }
}

function App() {
  return (
    <>
      <Greeting isLoggedIn={true} />
    </>
  );
}
```

## Ternary Operator

```JavaScript
function Greeting({ isLoggedIn }) {
  return isLoggedIn ? <h1>Welcome Back</h1> : <h1>Please log in</h1>;
}

function App() {
  return (
    <>
      <Greeting isLoggedIn={true} />
    </>
  );
}
```

## Logical AND Operator (`&&`)
Used when you want to render some jsx when a condition is true or render nothing otherwise.

```JavaScript
function Greeting({ isLoggedIn }) {
  return isLoggedIn === true && <button>Your account</button>
}

function App() {
  return (
    <>
      <Greeting isLoggedIn={true} />
    </>
  );
}
```
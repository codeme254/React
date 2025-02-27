# Props

Props (short for "properties") are used to pass data from a parent component to a child component.

Props are passed as arguments into React components, making these components highly reusable.

```JavaScript
function Greet(props) {
  return (
    <h1>
      Hello {props.firstName} {props.lastName}!
    </h1>
  );
}

function App() {
  return (
    <>
      <Greet firstName="John" lastName="Doe" />
      <Greet firstName="Jack" lastName="Smith" />
    </>
  );
}
```

## Props with destructuring
Instead of passing `props.firstName` and `props.lastName`, we can destructure them as shown:

```JavaScript
function Greet({ firstName, lastName }) {
  return (
    <h1>
      Hello {firstName} {lastName}!
    </h1>
  );
}

function App() {
  return (
    <>
      <Greet firstName="John" lastName="Doe" />
      <Greet firstName="Jack" lastName="Smith" />
    </>
  );
}
```

## Props are Read-Only
Props cannot be modified inside the component:
```JavaScript
function Greet({ firstName, lastName }) {
  firstName = "Emily"; // DON'T
  lastName = "Smith"; // DON'T
  return (
    <h1>
      Hello {firstName} {lastName}!
    </h1>
  );
}
```

## The `children` prop in React
In React, `children` is a special prop that allows components to wrap and display other components, elements, or 
content inside them. 

It makes components more reusable and flexible.

We use the `children` prop when a component **doesn't know what it will hold**

```JavaScript
function Card({ children }) {
  return <div>{children}</div>;
}

function App() {
  return (
    <>
      <Card>
        <h2>Service 1</h2>
        <p>Lorem ipsum</p>
        <p>Dolor sit</p>
        <a href="#">Get Started</a>
      </Card>

      <Card>
        <h2>Service 2</h2>
        <p>Benefit 1</p>
        <p>Benefit 2</p>
        <a href="#">Get Started</a>
      </Card>
    </>
  );
}
```
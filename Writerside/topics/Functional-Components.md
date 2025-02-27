# Functional Components

A functional component is the most common type of React component.

Functional components are created using functions, the name of this function should begin with an uppercase letter, 
and the function must only return one HTML element. We can nest as many HTML elements as we want in this single
returned HTML element.

**Example 1**
```JavaScript
function Greeting() {
  return <h1>Hello, React!</h1>
}

export default Greeting;
```

**Example 2**

```JavaScript
function Greeting() {
  return (
    <div>
      <h1>Hello, world!</h1>
      <p>React is awesome</p>
      <p>Good bye world!</p>
    </div>
  );
}
```
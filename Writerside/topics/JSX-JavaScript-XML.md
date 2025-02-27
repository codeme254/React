# JSX (JavaScript XML)

JSX is a syntax extension for JavaScript that lets you write HTML-like code inside JavaScript.

React uses JSX to describe what the UI should look like.

## The Rules of JSX
### 1. Return a single root element\
To return multiple elements from a component, wrap them with a single parent tag.

For example, you can use a <div>:

```HTML
<div>
    <h1>Hello, world!</h1>
    <p>React is awesome</p>
    <p>Always use React</p>
</div>
```

If you don't want to add an extra `div` element to your markup, you can use `<>` and `</>` instead.

This empty tag is called a **Fragment**, fragments allow you to group things without leaving any trace in the 
browser HTML tree.

```HTML
<>
    <h1>Hello, world!</h1>
    <p>React is awesome</p>
    <p>Always use React</p>
</>
```

### 2. Close all tags
JSX requires all tags to be explicitly closed.

Self-closing tags like `<img>` must become `<img />`

### 3. Camel Case most of the things.
In React, many HTML attributes are written in camel case, for example, `class` becomes `className`.

```JavaScript
function Greeting() {
  return (
    <>
      <h1 className="title">Hello, world!</h1>
      <p className="paragraph">React is awesome</p>
      <p className="paragraph">Always use React</p>
    </>
  );
}
```

### 4. Expressions inside of JSX use `{}`
Curly braces let you work with JavaScript right there in your markup.

The example below declares a name and embeds it with curly braces inside the `<h1>`

```JavaScript
function Greeting() {
    const username = "John Doe"
  return (
    <>
      <h1 className="title">Hello, world! My name is {username}</h1>
    </>
  );
}
```
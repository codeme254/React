# Events

> React lets you add event handlers to your JSX.

> Event handlers are your own functions that will be triggered in response to interactions like clicking, hovering,
focusing form inputs, and so on.


To add an event handler, you will first define a function and then pass it as a prop to the appropriate JSX tag.

```JavaScript
export default function Button() {
  function handleButtonClick() {
    alert("Button Clicked")
  }
  return (
    <button onClick={handleButtonClick}>Click me</button>
  );
}
```

Here, we have defined a function called `handleButtonClick` and then passed it as a prop to the button.

`handleButtonClick` is an **event handler**. Event handler function:
- Are usually defined inside your component.
- Have names that start with `handle`, followed by the name of the event (convention).

> Your event handlers will receive a React event object. It is also sometimes known as a “synthetic event”.

```JavaScript
export default function Button() {
  function handleButtonClick(e) {
    console.log(e); // React event object
  }
  return <button onClick={handleButtonClick}>Click me</button>;
}
```

## Inline Event Handlers
You can also define event handlers inline in the JSX:
```JavaScript
export default function Button() {
  return (
    <button
      onClick={function () {
        alert("Button Clicked");
      }}
    >
      Click me
    </button>
  );
}
```
Or, more concisely, using an arrow function:
```JavaScript
export default function Button() {
  return (
    <button
      onClick={() => {
        alert("Button clicked");
      }}
    >
      Click me
    </button>
  );
}
```

## Passing Event Handlers as Props

```JavaScript
export default function Button({ label, onButtonClick }) {
  return <button onClick={onButtonClick}>{label}</button>;
}
```

```JavaScript
<Button label="Say hello" onButtonClick={() => alert("Hello, world")} />
<Button
  label="Say goodbye"
  onButtonClick={function () {
    alert("Goodbye world");
    alert("This was fun");
  }}
/>
```

[More Events](https://react.dev/reference/react-dom/components/common#events)
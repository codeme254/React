# Styling Components

We can style React components using Vanilla CSS in the following ways:

## External CSS Stylesheets
Here, we basically create an external CSS file for each component and do the required styling of classes, and use
those class names inside the component.

It is a convention that the name of the external CSS file is the same as the name of the component but with a `.css`
extension.

**Button.css**

```css
/* Button.css */
.button {
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.button:hover {
  background-color: darkblue;
}
```

**Button.jsx**
```JavaScript
import "./Button.css";

function Button() {
  return <button className="button">Click Me</button>;
}

export default Button;
```

## CSS Modules
CSS Modules offer a powerful solution for writing component-specific styles in React.

They let you scope styles to individual components, thereby letting you avoid naming conflicts and simplifying style 
maintenance.

To use CSS modules in React, create a file with the `.module.css` extension. For example, `Button.module.css`.

You then need to import the file into your component with the `import` keyword and a name you want, for 
example, `styles` or `classes`, followed by the relative path of the CSS modules file:

**Button.module.css**
```CSS
/* Button.module.css */
.button {
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.button:hover {
  background-color: darkblue;
}
```

**Button.jsx**
```JavaScript
import classes from "./Button.module.css";

function Button() {
  return <button className={classes.button}>Click me</button>;
}

export default Button;
```

The name you choose is now an object, the keys are the classes in the CSS modules file, and the values are the 
respective properties in the class.

## Inline Styles (CSS in JS)
Every JSX element has a `style` property you can add to its opening tag.

This means you can add inline styling to JSX in a React component like in traditional HTML.

The primary difference is that you must specify inline styles as objects.

In this object, the keys are the CSS properties written in camelCase, and the values are strings corresponding to 
valid CSS values.

```JavaScript
function Button() {
  return (
    <button style={{ backgroundColor: "red", border: "2px solid red" }}>
      Click me
    </button>
  );
}

export default Button;
```

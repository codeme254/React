# Handling Forms in React

Forms are a crucial part of any web application, allowing users to input and submit data.

In React, form handling is different from traditional HTML forms because React uses **controlled** and **uncontrolled** 
components to manage form state.

## Controlled VS Uncontrolled Components
React offers two ways to handle forms:
- **Controlled Components** - React controls the input values using useState.
- **Uncontrolled Components** - Uses useRef to access input values directly.

Controlled components are the recommended approach.

With controlled components, inputs are fully controlled by **React State**.

Every time the user types something in the input, the state updates and the UI re-renders.

When it comes to submitting the form, you can control the submit action by adding an event handler in the `onSubmit`
attribute for the form.

## An example of a simple controlled form

```JavaScript
import { useState } from "react";

function App() {
  const [firstName, setFirstName] = useState("");
  const [lastName, setLastName] = useState("");

  function handleSubmit(e) {
    e.preventDefault();
    console.log(`Your name is ${firstName} ${lastName}`);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        placeholder="first name"
        value={firstName}
        onChange={(e) => setFirstName(e.target.value)}
      />
      <br />
      <input
        type="text"
        placeholder="last name"
        value={lastName}
        onChange={(e) => setLastName(e.target.value)}
      />
      <button>Submit</button>
      <p>
        {firstName} {lastName}
      </p>
    </form>
  );
}
```

- Each input field is controlled by state (`useState`).
- The `onChange` handler updates the state whenever the user types.
- When the form is submitted, `handleSubmit` logs the values.

## Multiple input fields
You can control the values of more than one input field by adding a name attribute to each element.

To do this, we initialize our state with an empty object.

To access the fields in the event handler, we will use the `event.target.name` and `event.target.value` syntax.

To update the state, we will use square brackets [bracket notation] around the property name, i.e. `[event.target.name]`

```JavaScript
import { useState } from "react";

function App() {
  const [formData, setFormData] = useState({ firstName: "", lastName: "" });

  function handleSubmit(e) {
    e.preventDefault();
    console.log(formData);
  }

  function handleInputChange(e) {
    setFormData({ ...formData, [e.target.name]: e.target.value });
  }

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        placeholder="first name"
        name="firstName"
        value={formData.firstName}
        onChange={handleInputChange}
      />
      <br />
      <input
        type="text"
        placeholder="last name"
        name="lastName"
        value={formData.lastName}
        onChange={handleInputChange}
      />
      <p>
        {formData.firstName} {formData.lastName}
      </p>
      <button>Submit</button>
    </form>
  );
}
```

- Instead of multiple useState calls, we store all form data in a single state object.
- handleChange updates the correct field dynamically using [e.target.name].

## Uncontrolled Components (less common)
```JavaScript
import { useRef } from "react";
function App() {
  const firstNameRef = useRef();
  const lastNameRef = useRef();

  function handleSubmit(e) {
    e.preventDefault();
    console.log(firstNameRef.current.value);
    console.log(lastNameRef.current.value);
  }
  return (
    <form onSubmit={handleSubmit}>
      <input type="text" placeholder="first name" ref={firstNameRef} />
      <br />
      <input type="text" placeholder="last name" ref={lastNameRef} />
      <button>submit</button>
    </form>
  );
}
```
- `useRef()` creates references to input fields.
- Values are accessed using ref.current.value when the form is submitted.
- This is useful when React doesn’t need to re-render on input change.
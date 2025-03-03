# Rendering Lists

When working with React, you will often times need to render lists of items.

## Displaying a List of Items In React
To achieve displaying a list of items in React, we are going to use the JavaScript's built in `map` method to iterate
over our list of items; and map them from primitives or objects to HTML elements.

**Note: Each element receives a mandatory _key_ prop**.

When rendering lists in React, **keys** help React identify which items changed, which items were added, or removed.

```JavaScript
function Applicants() {
  const applicants = ["Jack", "Jane", "Smith"];
  return (
    <div>
      {applicants.map(function (applicant) {
        return <p key={applicant}>{applicant}</p>;
      })}
    </div>
  );
}

export default Applicants;
```

We can also use JavaScript arrow function to make the inline function for the map more lightweight:

```JavaScript
function Applicants() {
  const applicants = ["Jack", "Jane", "Smith"];
  return (
    <div>
      {applicants.map((applicant) => {
        return <p key={applicant}>{applicant}</p>;
      })}
    </div>
  );
}

export default Applicants;
```

Since we are not doing anything in the function's block body, we can also refactor it to a concise body and 
omit the return statement and the curly braces for the function body:

```JavaScript
function Applicants() {
  const applicants = ["Jack", "Jane", "Smith"];
  return (
    <div>
      {applicants.map((applicant) => (
        <p key={applicant}>{applicant}</p>
      ))}
    </div>
  );
}

export default Applicants;
```

## Displaying a List of Objects
It doesn't work any different for complex objects in JavaScript arrays. You iterate over the list with the map method 
again and output for each list item your HTML elements.

```JavaScript
function Applicants() {
  const applicants = [
    { firstName: "John", lastName: "Doe", age: 25 },
    { firstName: "Jack", lastName: "Smith", age: 20 },
    { firstName: "Brad", lastName: "Paisley", age: 35 },
  ];
  return (
    <div>
      {applicants.map((applicant) => (
        <p key={applicant.firstName}>
          {applicant.firstName} {applicant.lastName} - {applicant.age}
        </p>
      ))}
    </div>
  );
}

export default Applicants;
```
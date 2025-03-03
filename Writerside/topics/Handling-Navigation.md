# Handling Navigation

Navigation in React Router can be achieved in the following ways:

## Link Navigation
This is the simplest and most common form of navigation you will encounter. We have already seen the most basic 
form of link navigation using the Link component:

```JavaScript
<Link to="/">Home</Link>
<Link to="/books">Books</Link>
```

If you pass the `reloadDocument` prop to the `Link` component, it will act like a normal anchor tag and do a full 
page refresh on navigation instead of just re-rendering the content inside your Routes component.

## Navigating programmatically using the `useNavigation` hook
The `useNavigate` hook is a really simple hook that takes no parameters and returns a single `navigate` 
function which you can use to redirect a user to specific pages.
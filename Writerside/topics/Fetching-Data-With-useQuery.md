# Fetching Data With useQuery

To use React Query, the first thing we need to do is wrap our entire application with `QueryProvider`

We also create an instance of the `QueryClient` and provide it to our application as shown:

```JavaScript
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";

const queryClient = new QueryClient();

function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <div>
        <h1>React Query</h1>
      </div>
    </QueryClientProvider>
  );
}
```

By doing this, our application now has access to every hook and method that react query provides.

## Running a basic query to get data
To fetch data, we use the `useQuery` hook which is imported from `react-query`.
```JavaScript
import { useQuery } from '@tanstack/react-query';
```

The `useQuery` hook takes several arguments, but two of these arguments are required:
- `queryKey`: a unique key to identify the query, this is used for caching and invalidating the query.
- `queryFn`: an asynchronous function that fetches the data.
These arguments are passed as an object as shown:

```JavaScript
useQuery({
  queryKey: ["your-query-key"],
  queryFn: async function () {}
})
```

The `useQuery` hook returns an object containing all the information you will ever need from that individual query.

We can destructure the following important values which are available in the object:
- `data`: the data that was fetched.
- `isLoading`: a boolean to indicate a loading process, where true means loading is happening, false means otherwise.
- `isError`: a boolean indicating whether an error happened during fetching where true means there was an error.

Below is a complete example:
```JavaScript
  const { data, isError, isLoading } = useQuery({
    queryKey: ["get-students"],
    queryFn: async function () {
        setTimeout(() => 5000)
      try {
        const response = await fetch(`http://localhost:3000/students`);
        const data = await response.json();
        return data;
      } catch (e) {
        console.log("There was an error");
      }
    },
  });
```

## Handling Query Errors
`useQuery` returns an `isError` flag as well as the error thrown from the request, we can use these to 
handle errors in our application as shown:

```JavaScript
const { data, isError, isLoading, error } = useQuery({
    queryKey: ["get-students"],
    queryFn: async function () {
        setTimeout(() => 5000)
      try {
        const response = await fetch(`http://localhost:3000/students`);
        const data = await response.json();
        return data;
      } catch (e) {
        console.log("There was an error");
      }
    },
  });

  if (isError) {
    return <h1>{error.message}</h1>;
  }
```
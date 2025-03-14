# React Query DevTools

React Query comes with dedicated DevTools, which we can use to visualize the inner workings of React Query.

To install the package:
```Bash
npm install @tanstack/react-query-devtools
```

Next, import the `ReactQueryDevtools` component from the package and place it just before the closing
`QueryClientProvider` as shown:

```JavaScript
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
import { ReactQueryDevtools } from '@tanstack/react-query-devtools'
const queryClient = new QueryClient();

function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <ReactQueryDevtools />
    </QueryClientProvider>
  );
}
```
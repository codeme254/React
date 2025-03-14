# Query Cache

The query cache in React Query is an in-memory storage that keeps track of fetched data.

It allows React Query to store, share, and sync data across your application without unnecessary re-fetching.

## How Query Cache Works
Whenever you use `useQuery`, React Query fetches the data and stores it in the cache, the next time the same data is
needed:
- If the data is fresh, it uses the cached data (no network request).
- If the data is stale, it re-fetches the data in the background.
- If the data is garbage-collected (removed from memory), it re-fetches on demand.

## Manually Accessing the Cache
You can manually access the Cache using the `useQueryClient` hook as shown:

```JavaScript
import { useQueryClient } from "@tanstack/react-query";

const queryClient = useQueryClient();
const data = queryClient.getQueryData([QUERY_KEY_HERE]);
console.log(data); // Cached data
```


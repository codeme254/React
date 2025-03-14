# Making API calls in React

React doesn't have a built-in support or pattern or a hook for API calls, but we can still use native JavaScript to
achieve this.


## Basic API Call Using `fetch`

The simplest way to make an API call in React is by using the fetch method inside `useEffect`.

This is especially useful when you want to fetch and show data on a page load.

```JavaScript
import { useEffect, useState } from "react";

function Posts() {
  const [data, setData] = useState(null);
  useEffect(() => {
    async function fetchData() {
      try {
        const response = await fetch(
          `https://jsonplaceholder.typicode.com/posts/`,
        );
        if (!response.ok) {
          throw new Error("There was an error fetching data");
        }
        const data = await response.json();
        setData(data);
        //
      } catch (e) {
        console.log("There was an error");
      }
    }

    fetchData();
  });
  return <div>{/* map through data to display it */}</div>;
}
```

## Handling Loading and Errors
A real-world app should handle loading states and error states such as network failure.

```JavaScript
import { useEffect, useState } from "react";

function Posts() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);

  useEffect(() => {
    async function fetchData() {
      try {
        setLoading(true);
        const response = await fetch(
          `https://jsonplaceholder.typicode.com/posts/`,
        );
        if (!response.ok) {
          throw new Error("There was an error fetching data");
        }
        const data = await response.json();
        setData(data);
        setLoading(false);
      } catch (e) {
        setError("There was an error");
        setLoading(false);
      }
    }

    fetchData();
  });
  if (loading) return <p>Loading please wait...</p>
  if (error) return <p>Error: {error}</p>
  return <div>{/* map through data to display it */}</div>;
}
```

## Making API Calls on User Interaction such as a Button Click
Sometimes, you don't want an API call to run on a page load, but only when a user makes an interaction such as a button
click.

```JavaScript
import { useState } from "react";

function App() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(false);

  async function fetchData() {
    setLoading(true);
    try {
      const response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
      const json = await response.json();
      setData(json);
    } catch (error) {
      console.log("Error:", error);
    } finally {
      setLoading(false);
    }
  }

  return (
    <div>
      <button onClick={fetchData} disabled={loading}>
        {loading ? "Loading..." : "Fetch Data"}
      </button>
      {/* show data */}
    </div>
  );
}
```
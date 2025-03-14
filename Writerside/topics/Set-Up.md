# Installation and Set up

## Installing React Query In Your Project
To install React Query in your project, run:

```Bash
npm install @tanstack/react-query
```

## Setting up a Fake Server
Since we don't have a real backend, we can use a fake server.

The fake server allows us to practice fetching, mutating, and handling data responses without needing a real backend.

For this, we will use [json server](https://www.npmjs.com/package/json-server) npm package.

Install `json-server` to your project:

```Bash
npm install json-server
```

In the root directory, create a `db.json` file and past in the following data:
```json
{
  "students": [
    {
      "firstName": "John",
      "lastName": "Doe",
      "age": 20
    },
    {
      "firstName": "Jane",
      "lastName": "Smith",
      "age": 22
    },
    {
      "firstName": "Michael",
      "lastName": "Johnson",
      "age": 21
    },
    {
      "firstName": "Emily",
      "lastName": "Davis",
      "age": 19
    },
    {
      "firstName": "Daniel",
      "lastName": "Brown",
      "age": 23
    }
  ]
}
```

Finally, run:
```bash
npx json-server db.json
```

This will start the server on port `3000`.

If you want a custom port, you can set up a script, add the following script to your `package.json` under scripts:

```Bash
"serve-json": "json-server --watch db.json --port 4000"
```

Finally, run:

```Bash
npm run serve-json
```
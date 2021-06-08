# Using middleware to log requests to an API

This project will have you building your own middleware, to log requests to an API

## What you will be doing

This project will allow you to practise using:

> Creating middleware in Express.js

This project assumes you've already had experience with:

> Express.js middleware
> Node.js filesystem

To do this project, you must have completed:

**express-solar-system-api**

## Tasks

### Task 1 - Writing your middleware function

Use the snippet **middleware template**

Your middleware should intercept **all** requests from the client, and write some data to a file

Each **new line** in the file should include the:

- `request.ip` - the ip of the client
- `request.method` - the method or type of request
- `request.originalUrl` - the original request url

> Hint: You can use `fs.writeFile()` to write to a file
> Hint: You can create a new line by writing `\n` at the end of each line

Each of these values should be separated with a pipe character `|`, surrounded by a whitespace character.

For example:

```text
127.0.0.1 | GET | /planets/find
```

### Task 2 - Reviewing the log

- Create a new endpoint, which allows the user to **GET** all the data from the log file

The endpoint should read the log file and **respond** with all the data from the file

> Hint: You can use `fs.readFile()` to read from a file

## Task 3 - Ignore requests for the log

In the middleware you created for Task 1, make it so that the any requests for the **log endpoint** you created in Task 2, is not recorded to the log

### Task 4 - Securing the log

- Write some middleware which will only allow requests through which include the query parameter `secret`, and where the query parameter `secret` matches a value (of your choice)

- Use this middleware to "protect" the endpoint you wrote in **Task 2**

### Task 5 - Add some data to your log

- Make a number of requests to your endpoint to generate some data for your log

- Review your log using the API and see what data you got!

# Using middleware to log requests to an API

A server log is a text document that contains all activities of a server. It can give you details of how, when, and who accessed your application.

## What you will be doing

To simulate a server in the real world, you will create some server endpoints to service requests from a client. In the real world, the server will also keep track of all requests to the server. You will be writing a middleware function to do this.

A helper function has already been written for you which writes data to the file system.

## Tasks

### Task 1 - Creating some endpoints

We need a few endpoints for the server.

In the file `server.js`;

1. Create a `GET` endpoint which has the path `"/travel"`. It can return any random data you like.
2. Create a `GET` endpoint which has the path `"/search"`. It can return any random data you like.
3. Create a `POST` endpoint which has the path `"/subscribe"`. It can return any random data you like.
4. Create a `POST` endpoint which has the path `"/createBooking"`. It can return any random data you like.
5. Create a `PATCH` endpoint which has the path `"/update"`. It can return any random data you like.

### Task 2 - Reading the Express documentation

1. Read the Express request object [ip](http://expressjs.com/en/4x/api.html#req.ip) property
2. Read the Express request object [method](http://expressjs.com/en/4x/api.html#req.method) property
3. Read the Express request object [originalUrl](http://expressjs.com/en/4x/api.html#req.originalUrl) property

When you have finished, create a new file `logger.js`. This is where you will write your middleware.

### Task 3 - Writing your middleware

Working within `logger.js`;

1. Use the following snippet of code to structure your middlware.

   ```js
   function logger(req, res, next) {
     next();
   }
   ```

2. Within the `logger` function, create the variable `data`

3. Using the information you learned from the documentation, assign a string to the variable `data` which includes the;

   - **request.ip** - the ip of the client
   - **request.method** - the method or type of request
   - **request.originalUrl** - the original request url

   You can separate each piece of information with a pipe `|` character.

   For example:

   ```text
   127.0.0.1 | GET | /travel
   ```

> 👽 Important! The `next()` function should be the **last** instruction in the function! Why? Because this calls the next middleware in the chain, and signifies that your middleware is complete.

### Task 4 - Writing your middleware (continued)

1. Import the `appendToLogFile` function from `helpers.js` into `logger.js`
2. Inside the `logger` function, execute `appendToLogFile` with the `data` variable as your argument
3. Export your middleware function

### Task 5 - Implementing the middleware

Now is the time to use your middleware! We must add it to our middleware "chain".

Inside `server.js`;

1. Import your middleware function
2. Mount your middleware into your express application with the `app.use()` function, using the path `"/"`. This should be written **before** your endpoint handlers.

> 🦥 The path `"/"` is the root path, which means it will catch every request

### Task 6 - Add some data to your log

Using an API testing tool like [insomnia](https://insomnia.rest/) or [postman](https://www.postman.com/), create some requests to your server endpoint to generate data for your log.

Review your log file (`log.text`) and see what data was created!

## When enter the command `localhost:4000/add-message?s=Hello`:

### 1. Which methods are called in the code?
The `handleRequest` method is called.

### 2. What are the parameters associated with those methods and the values of any associated fields of the class?
- The value of the parameter `url` for the `handleRequest` method is `localhost:4000/add-message?s=Hello`, which is a URI object.
- The relevant fields of class `StringHandler` are:
  - `str`: its initial value is an empty `StringBuilder` object.
  - `count`: its initial value is 0.

### 3. How do the values of the relevant fields of the class change as a result of this particular request? If no values were changed, explain why.
- The value of `count` increases from 0 to 1 as the request is processed.
- The value of `str` changed from an empty `StringBuilder` object to a `StringBuilder` object containing "1. Hello\n".
- This is because the logic inside the `handleRequest` method checks to see if the path of the request is `/add-message`, and if it is, it takes the message from the query string, adds it to `str`, and increases the value of `count`.

# JavaScript Asynchronous

---

In JavaScript, a block of code can be executed in specified time intervals. These time intervals are called timing events.

There are two methods for executing code at specific intervals. They are:

- `**setInterval()**`
- `**setTimeout()**`

## **JavaScript set Timeout**

The `setTimeout()` method executes

a block of code after the specified time. The method executes the code only once.

The commonly used syntax of JavaScript `setTimeout` is:

```jsx
setTimeout(function, milliseconds);
```

Its parameters are:

- **function** - a function containing a block of code
- **milliseconds** - the time after which the function is executed

The `setTimeout()` method returns an **intervalID**, which is a positive integer.

<aside>
💡 **Note**
: The `setTimeout()`
 method is useful when you want to execute a block of code once after some time. For example, showing a message to a user after the specified time.

</aside>

## **JavaScript set Interval**

The `setInterval()` method repeats a block of code at every given timing event.

The commonly used syntax of JavaScript `setInterval` is:

```jsx
setInterval(function, milliseconds);
```

Its parameters are:

- **function** - a function containing a block of code
- **milliseconds** - the time interval between the execution of the function

The `setInterval()` method returns an **intervalID** which is a positive integer.

```jsx
// program to display a text using setInterval method
function greet() {
    console.log('Hello world');
}

setInterval(greet, 1000);
```

In the above program, the `setInterval()` method calls the `greet()` function every **1000** milliseconds(**1** second).

Hence the program displays the text Hello world once every **1** second.

<aside>
💡 **Note**
: The `setInterval()`
 method is useful when you want to repeat a block of code multiple times. For example, showing a message at a fixed interval.

</aside>

## JavaScript Promise

A Promise is a built-in object in JavaScript that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. It's a way to handle asynchronous operations without resorting to callback functions, which can quickly become unwieldy when dealing with complex code.

Promises have three states:

- **`pending`**: The initial state; the promise is neither fulfilled nor rejected.
- **`fulfilled`**: The operation completed successfully, and the promise has a resulting value.
- **`rejected`**: The operation failed, and the promise has a reason for the failure.

A Promise is created using the **`Promise`** constructor, which takes a function called an executor as its argument. The executor function takes two arguments: a **`resolve`** function and a **`reject`** function. The **`resolve`** function is called when the operation is completed successfully, and the **`reject`** function is called when the operation fails.

![https://cdn.programiz.com/sites/tutorial2program/files/javascript-promise.png](https://cdn.programiz.com/sites/tutorial2program/files/javascript-promise.png)

```jsx
const promise = new Promise((resolve, reject) => {
  // Do some asynchronous operation
  // If successful, call resolve with the result
  // If failed, call reject with the reason
});

promise.then(result => {
  // Handle successful result

}).catch(error => {
  // Handle error
});
```

The **`then()`** method is used to handle the successful completion of a Promise, and the **`catch()`** method is used to handle any errors that occur during the Promise's execution.

Promises can also be chained together using the **`then()`** method, which returns a new Promise. This allows for more complex asynchronous operations to be handled in a readable and organized way.

2nd Example

```jsx
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = [1, 2, 3, 4, 5];
      // Simulate a successful request with the data as the result
      resolve(data);
      // Simulate a failed request with an error message
      // reject("Error fetching data");
    }, 2000);
  });
};

fetchData()
  .then(data => {
    console.log("Data fetched:", data);
  })
  .catch(error => {
    console.log("Error fetching data:", error);
  });
```

In this example, the **`fetchData()`** function returns a new Promise that simulates fetching data from a server. The Promise resolves with an array of numbers after a 2 second delay. If we uncomment the **`reject()`** call and comment out the **`resolve()`** call, the Promise would reject with an error message instead.

We then use the **`then()`** method to handle the successful completion of the Promise by logging the fetched data to the console. If an error occurs, we use the **`catch()`** method to handle it by logging the error message to the console.

---

## Callback JavaScript

In JavaScript, a callback function is a function that is passed as an argument to another function and is executed later when the first function has completed its operation. The callback function is typically used to handle the result of an asynchronous operation, such as an HTTP request or a file read operation.

Here's a simple example of a callback function in JavaScript:

```jsx
function fetchData(url, callback) {
  // Make an HTTP request to the specified URL
  var xhr = new XMLHttpRequest();
  xhr.open("GET", url);
  xhr.onload = function() {
    if (xhr.status === 200) {
      // If the request is successful, call the callback function with the response data
      callback(null, xhr.responseText);
    } else {
      // If the request fails, call the callback function with an error message
      callback("Error fetching data");
    }
  };
  xhr.send();
}

// Call the fetchData function and pass a callback function
fetchData("https://example.com/api/data", function(error, data) {
  if (error) {
    console.log("Error fetching data:", error);
  } else {
    console.log("Data fetched:", data);
  }
});
```

Example 2 

```jsx
const doSomething = callback => {
  setTimeout(() => {
    const skills = ['HTML', 'CSS', 'JS']
    callback(false, skills)
  }, 2000)
}

doSomething((err, result) => {
  if (err) {
    return console.log(err)
  }
  return console.log(result)
})
```

---

## Fetch API

The Fetch API is a modern, Promise-based API for making HTTP requests in JavaScript. It provides a simpler and more flexible alternative to the older XMLHttpRequest (XHR) API and is widely supported in modern browsers and Node.js environments.

Here's an example of using the Fetch API to make a GET request:

```jsx
fetch('https://example.com/api/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

In this example, we call the **`fetch()`** method with the URL of the API endpoint that returns JSON data. The **`fetch()`** method returns a Promise that resolves to a **`Response`** object. We then chain a **`then()`** method to the Promise that checks if the response is OK (i.e., between 200 and 299) and returns the JSON response data using the **`json()`** method.

We then chain a second **`then()`** method to the Promise to handle the success case, where we log the fetched data to the console. If an error occurs, we catch it using the **`catch()`** method and log the error message to the console.

```jsx
<script>
    fetch('https://uselessfacts.jsph.pl/api/v2/facts/random?language=en')
        .then((response) => response.json())
        .then((data) => {
            const fact = data.text;
            console.log('Random Useless Fact:', fact);
        })
        .catch((error) => {
            console.log('Error:', error);
        });
</script>

In this example, the fetch function is used to send an HTTP GET request to the specified API endpoint. The fetch function returns a promise that resolves to the response. We can then use the .json() method on the response object to extract the JSON data.
Once we have the data, we can access the desired information, in this case, the useless fact, by accessing the appropriate property (e.g., data.text). Finally, we log the random useless fact to the console. If any error occurs during the fetch request
or the JSON parsing, the catch block will handle the error and log it to the console. When you run this code in a JavaScript environment (such as a web browser's console or a Node.js environment), it will fetch a random useless fact and log it to the
console.
```

---

## **Async and Await**

Async/await is a modern way of writing asynchronous code in JavaScript. It allows you to write asynchronous code that looks like synchronous code, making it easier to read, write, and reason about. Async/await is built on top of Promises and is supported in all modern browsers and Node.js environments.

<aside>
💡 In JavaScript, asynchronous code is code that does not execute in a linear, synchronous fashion. Instead, it allows for multiple tasks to be executed concurrently, without blocking the execution of other tasks. Asynchronous code is essential for working with I/O-bound tasks such as network requests, file system operations, and user input.

</aside>

<aside>
💡 In asynchronous code, on the other hand, multiple tasks can be started at the same time, and the code does not wait for each task to complete before moving on to the next one. Instead, callbacks or Promises are used to handle the completion of each task.

</aside>

```jsx
async function fetchData() {
  try {
    const response = await fetch('https://example.com/api/data');
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error fetching data:', error);
  }
}
```

In this example, we define an async function called **`fetchData()`** that uses the **`await`** keyword to wait for the Promise returned by the **`fetch()`** method to resolve. We then check if the response is OK and use the **`await`** keyword again to wait for the Promise returned by the **`json()`** method to resolve, which returns the JSON response data.

We handle the success case by logging the fetched data to the console, and the error case by catching any errors thrown by the **`fetch()`** or **`json()`** methods.

The **`await`** keyword can only be used inside an async function and is used to wait for a Promise to resolve before continuing with the execution of the function. If the Promise rejects, the **`await`** keyword will throw an error, which can be caught using a try/catch block.

Async/await makes it easier to write asynchronous code that is easier to read and understand. It also helps avoid callback hell and makes error handling easier by allowing you to use try/catch blocks instead of chaining multiple catch functions.
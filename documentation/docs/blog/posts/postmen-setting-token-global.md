---
draft: false
tags: [Postman]
comments: true
date: 2024-01-04
authors:
  - bishow
---

# Automatically set Bearer Token in global variable postman after Login api

In Postman, `pm` is a built-in JavaScript object that provides access to the Postman API. It allows you to interact with and manipulate the data and features within the Postman environment during the execution of pre-request scripts and tests.

<!-- more -->

**_ALL YOU NEED 2 lines of code_**

```js
// Stores the access token in an environment or global variable
var accessToken = pm.response.json().access;

// It set in the global enviroment variable named `accessToken`
pm.globals.set("accessToken", accessToken);

// if you want to set in local enviroment variable named `TOKEN`
pm.environment.set("TOKEN", token);
```

Here are some common uses of `pm` in Postman:

- **`pm.environment`**: This property allows you to access and manipulate environment variables. For example, you can use pm.environment.get("variableName") to retrieve the value of an environment variable.

- **`pm.globals`**: This property is similar to pm.environment, but it deals with global variables.

- **`pm.request`**: This property provides information about the current request being sent, allowing you to modify request details dynamically.

- **`pm.response`**: This property provides information about the response received after sending a request, allowing you to extract data or perform tests on the response.

- **`pm.sendRequest`**: This method allows you to send additional HTTP requests from within your scripts.

Here's a simple example using pm.environment:

```js
// Get the value of the "TOKEN" variable in the current environment
var token = pm.environment.get("TOKEN");

// Log the token to the console
console.log("Token:", token);
```

In this example, `pm.environment.get("TOKEN")` is used to retrieve the value of the "TOKEN" variable in the current environment. The retrieved value is then logged to the console using `console.log`.

---

Testing in Postman

The **Tests** tab allows for any post-processing after a request is sent and includes the ability to write tests for assessing response data.
The **Test tab sandbox** has the Chai.js library built in, so you can use Chai's behavior-driven development (BDD) syntax to create readable test assertions.

```js
pm.test("Response status code is 200", function () {
  pm.response.to.have.status(200);
});

pm.test("Response has access and refresh properties", function () {
  var res = pm.response.json();
  pm.expect(res).to.have.property("access");
  pm.expect(res).to.have.property("refresh");
});

pm.test("Access property has a length greater than 0", function () {
  var res = pm.response.json();
  pm.expect(res.access).to.have.lengthOf.above(0);
});
```

---

## Reference

- [Set Bearer Token as Environment Variable in Postman for All APIs](https://iroshandu.medium.com/set-bearer-token-as-environment-variable-in-postman-for-all-apis-13277e3ebd78)
- [How do i set up a bearer token in postman from an environment variable?](https://stackoverflow.com/questions/50893947/how-do-i-set-up-a-bearer-token-in-postman-from-an-environment-variable)
- [How to automatically set a Bearer Token for your Postman requests?](https://community.postman.com/t/how-to-automatically-set-a-bearer-token-for-your-postman-requests/10126/10)

- [Write API test scripts in Postman](https://learning.postman.com/docs/writing-scripts/test-scripts/)
- [Postman Test script examples](https://learning.postman.com/docs/writing-scripts/script-references/test-examples/)
- [Api Testing in postmen ](https://www.postman.com/api-platform/api-testing/)

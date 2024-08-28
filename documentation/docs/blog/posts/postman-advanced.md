---
drafts: false
tags: [postment, api]
comments: true
date: 2024-05-05
authors:
  - bishow
---


# Postmen Advanced Topics

In Postman, `pm` is a ==global object== that provides various functions and methods to interact with the Postman sandbox environment. This object allows you to write scripts to manipulate the request and response, set and get variables, and perform assertions. The pm object is available in both Pre-request Scripts and Test Scripts.

<!-- more -->


Here are some advanced topics in Postman to help you level up your API testing and automation:

1.  Advanced Scripting

    - Pre-request Scripts: Write JavaScript code to execute before making a request. ==Useful for== setting `dynamic parameters`, `generating tokens`, etc.
    - Tests Scripts: Write JavaScript code to validate the response. You can perform assertions, set variables, and chain requests.

2.  Environment and Global Variables

    - Environment Variables: Define variables specific to an environment (e.g., `development`, `staging`, `production`) to easily switch contexts.
    - Global Variables: Variables accessible in all environments and collections. Useful for storing data that is constant across environments.

3.  Collection Runner and Automation

    - Collection Runner: Run a collection of requests in a specific order. Useful for running test suites and workflows.
    - Newman: A command-line tool to run Postman collections. It integrates with CI/CD pipelines, allowing automated testing.

4.  Data-Driven Testing

    - Using CSV/JSON Files: Import CSV or JSON files in the Collection Runner to execute the same requests with different sets of data.
    - Dynamic Variables: Use dynamic variables (like `{{$randomInt}}`, `{{$randomUUID}}`) to generate random data for tests.

5.  Chaining Requests

    - Setting Variables: Capture data from one request and use it in subsequent requests by setting and using variables.
    - Post-Request Scripts: Use test scripts to parse response data and set it as variables for the next request.

6.  Mock Servers

    - Creating Mocks: Simulate endpoints to test your application without hitting the actual API. Useful for frontend-backend decoupled development.
    - Custom Responses: Define custom responses for different scenarios (e.g., success, error, timeout).

7.  API Documentation

    - Generating Documentation: Automatically generate and publish documentation for your APIs. Postman can generate markdown or HTML documentation based on your collections.
    - API Versioning: Manage different versions of your API documentation.

8.  Integration with Version Control Systems

    - Version Control: Use Postman’s integration with Git to version control your collections. Helps maintain history and collaboration on API definitions.

9.  Security Testing

    - OWASP Testing: Implement tests to check for common vulnerabilities like SQL Injection, XSS, etc.
    - Authorization Testing: Test different authorization mechanisms like `OAuth`, `JWT`, `API Keys`.

10. Monitoring

    - Uptime Monitoring: Schedule and run collections periodically to ensure your APIs are up and running.
    - Performance Monitoring: Measure response times and other performance metrics over time.

11. Advanced Assertions

    - Chai Assertions: Use the Chai assertion library (integrated with Postman) for more complex assertions.
    - Custom Functions: Write custom JavaScript functions for reusable validation logic.

12. Visualizing Response Data

    - Postman Visualizer: Create custom visualizations of response data using HTML and JavaScript. Useful for interpreting and presenting data.

13. GraphQL Support

    - Query Execution: Support for making GraphQL queries and mutations.
    - GraphQL Variables: Use variables in GraphQL queries for dynamic data.

14. Postman Flows

    - Building Workflows: Use the Postman Flows feature to create and automate workflows visually, connecting requests and logic blocks.

15. Integrations

    - Third-party Integrations: Integrate Postman with tools like `Jenkins`, `Slack`, `Datadog`, and more for enhanced functionality.

These advanced features of Postman help you perform more thorough and efficient API testing and automation, improving your overall development and testing workflows.

---

???+ abstract "pm Methods and Attributes"

    The pm object in Postman provides a comprehensive set of methods and attributes to interact with the Postman runtime environment. Here is a detailed list of the main methods and attributes available within the pm object:

    === "Variables"

        **pm.variables**: Methods to interact with the variable scope (local, environment, global, data).

        - `pm.variables.get(variableName)`: Get the value of a variable from the current scope.
        - `pm.variables.set(variableName, variableValue)`: Set the value of a variable in the current scope.

        **pm.environment**: Methods to interact with environment variables.

        - `pm.environment.get(variableName)`: Get the value of an environment variable.
        - `pm.environment.set(variableName, variableValue)`: Set the value of an environment variable.
        - `pm.environment.unset(variableName)`: Remove an environment variable.
        - `pm.environment.clear()`: Clear all environment variables.

    === "Environment"

        > Methods to manage environment variables.

        - `pm.environment.set(variableName, variableValue)`: Set an environment variable.
        - `pm.environment.get(variableName)`: Get an environment variable.
        - `pm.environment.unset(variableName)`: Unset an environment variable.

    === "Request and Response"

        **pm.request**: Methods to interact with the request object.

        -   `pm.request.url`: Get or set the request URL.
        -   `pm.request.headers`: Access the request headers.

            -   `pm.request.headers.add(headerObject)`: Add a header to the request.
            -   `pm.request.headers.remove(headerName)`: Remove a header from the request.
        

        **pm.response**: Methods to interact with the response object.

        - `pm.response.json()`: Parse the response as JSON.
        - `pm.response.text()`: Get the response body as plain text.
        - `pm.response.code`: Get the response status code.
        - `pm.response.headers`: Access the response headers.
        - `pm.response.time()`: Get the response time.
    
    === "Assertions and Tests"

    === "Sending Requests"

---

## Reference

- [postman docs](https://learning.postman.com/docs/tests-and-scripts/write-scripts/test-examples/)
- [postman tutorial: javatpoint](https://www.javatpoint.com/variables-in-postman)
- [post mock server: geeksforgeeks](https://www.geeksforgeeks.org/postman-mock-server/)
- [postman :tutorialspoint](https://www.tutorialspoint.com/postman/postman_run_collections_using_newman.htm)

---
## React and Django Stack

=== "Django Stack"

    ```
    Rest stack for Django:

    - drf
    - Celery
    - Postgresql
    - redis
    - elastic search

    - rabbitmq
    - graphene

    Django + Graphene => Apollo + React
    ```

=== "React Stack"

    ```
    - Razzle JS,
    - Apollo,
    - react-loadable,
    - helmet,
    - react-router
    - redux
    ```

---

## Testing Framework

=== "React Testing Frameworks"

    1.  Jest:

        Jest is a widely-used JavaScript testing framework that works seamlessly with React applications. It provides features like snapshot testing, mocking, and a test runner. Jest is often the default choice for React projects.

        ```
        # For Jest
        npm install --save-dev jest
        ```

    2.  React Testing Library:

        This library is built on top of DOM Testing Library and provides utilities for testing React components. It encourages testing components as users would interact with them, promoting a more user-centric approach to testing.

        ```
        # For React Testing Library
        npm install --save-dev @testing-library/react @testing-library/jest-dom
        ```

    3.  Enzyme:

        Enzyme is a testing utility for React developed by Airbnb. It provides a set of tools to make it easier to test React components' output and behavior. Enzyme is compatible with Jest and other testing frameworks.

        ```
        npm install --save-dev enzyme enzyme-adapter-react-16 enzyme-to-json
        ```

=== "Django Testing Frameworks"

    1.  Django Test Framework (built-in):

        Django comes with its built-in testing framework. It includes support for unit tests, functional tests, and integration tests. Tests are usually placed in a tests module within each Django app.

    2.  pytest-django:

        pytest-django is a plugin for the popular Python testing framework pytest. It provides additional functionality for testing Django applications and is known for its concise syntax and powerful fixtures.

        ```py
        pip install pytest pytest-django
        ```

## Integration Testing:

1.  Cypress (for React):

    Cypress is an end-to-end testing framework for web applications. It allows you to write and run integration tests for your React applications. Cypress provides a real-time interactive test runner.

    ```
    npm install --save-dev cypress
    ```

2.  Selenium (for Django):

    Selenium is a tool for automating web browsers. It can be used for integration testing of Django applications by simulating user interactions with the browser. The Django project itself provides tools like django-selenium to simplify integration with Selenium.

    ```
    pip install selenium
    ```

## Testing Django and React Together:

1.  Django Rest Framework Test (for API testing):

    If your React frontend communicates with a Django backend through a RESTful API, you can use Django Rest Framework Test for testing your API endpoints.

2.  TestCafe (for end-to-end testing):

    TestCafe is a JavaScript end-to-end testing framework that allows you to test web applications in various browsers. It can be used to test the interaction between your React frontend and Django backend.

    ```
    npm install -g testcafe
    ```

3.  Jest-Django (for Jest and Django integration):

    Jest-Django is a Jest transformer and utility functions for working with Django. It helps when writing tests for JavaScript code that interacts with Django templates or uses Django's static files.

    ```
    npm install --save-dev jest-django
    ```

---

## Configuration

After installation, you may need to configure the testing frameworks according to your project structure. For example, setting up Jest configurations in a jest.`config.js` file or configuring pytest with `pytest.ini`.

Remember to consult the official documentation for each testing framework for more detailed configuration and usage instructions. Additionally, make sure your project's dependencies and versions are compatible with the chosen testing tools.

=== "Jest Configuration (jest.config.js)"

    Create a `jest.config.js` file in the root of your project. This file is used to configure Jest. Here's a simple example:

    ```js title="jest.config.js"
    module.exports = {
    // Set the test environment (browser-like)
    testEnvironment: "jsdom",

    // Extend Jest with testing-library assertions
    setupFilesAfterEnv: ["@testing-library/jest-dom/extend-expect"],

    // Ignore specific paths during tests
    testPathIgnorePatterns: ["/node_modules/", "/build/"],

    // Add more configuration options as needed
    };
    ```

=== "pytest Configuration (pytest.ini)"

    Create a `pytest.ini` file in the root of your project. This file is used to configure pytest. Here's a basic example:

    ```py
    [pytest]

    # Set the Django settings module
    DJANGO_SETTINGS_MODULE = your_project.settings

    # Enable code coverage for your Django app
    addopts = --cov=your_app_name

    # Specify the file naming convention for test files
    python_files = tests.py test_*.py *_tests.py
    ```

    Make sure to replace `your_project` and `your_app_name` with your actual Django project and app names.

    These configurations are just starting points, and you might need to customize them based on your project structure and specific needs. Consult the official documentation for Jest and pytest for more advanced configuration options and details.

## Additional Tips:

Jest Configuration for React Projects:

If you're working on a React project, you might want to extend Jest to work with Babel for transpiling JSX and ES6 code. Install the necessary packages:

```
npm install --save-dev babel-jest @babel/preset-env @babel/preset-react
```

=== "jest.config.js"

    Then, update your `jest.config.js`:

    ```js title="jest.config.js"
    module.exports = {
    // ...other configurations
    transform: {
        "^.+\\.jsx?$": "babel-jest", // Transform JSX with Babel
    },
    // ...other configurations
    };
    ```

=== "pytest.ini"

    Pytest Configuration for Django:

    If you're using pytest with Django, you might want to add additional configurations for Django-related testing:

    ```py title="pytest.ini"
    [pytest]
    DJANGO_SETTINGS_MODULE = your_project.settings

    # Specify Django settings module during tests
    addopts = --cov=your_app_name --ds=your_project.settings

    python_files = tests.py test_*.py *_tests.py
    ```

    Adjust the file names and paths according to your project structure.

    Remember to install the necessary Python packages for pytest and code coverage:

    ```py
    pip install pytest pytest-django pytest-cov
    ```

    Customize these configurations based on your project's needs, and consult the documentation for Jest and pytest for more in-depth details and options.

---

> Notes

When setting up testing for a project, it's essential to consider the specific requirements and preferences of your team. The mentioned frameworks and libraries are widely used and well-documented, making them good choices for testing React and Django applications.

---

## Reference

- [django stack](https://www.reddit.com/r/django/comments/a5en7h/professional_django_devs_what_does_the_rest_of/)

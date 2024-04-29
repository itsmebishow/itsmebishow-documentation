
!!! abstract "Core Advanced"

## 1. What is Reconciliation in React ?

Reconciliation is the process through which React updated the DOM by comparing the newly returned elements with the previously rendered ones.

React updates the DOM when a component's state changes.

## 2. What is React Fiber ?

React Fiber is the **reconciliation engine** that replaced the core algorithm in React v16.

It is a rewrite of the core algorighm, responsible for scheduling what get rendered on screen.

It is a set of algorithms for efficiently updating the UI.


## 3. Explain the concept of error boundaries in React.

Error boundaries are special React components that catch JavaScript errors during rendering, in lifecycle methods, and during the constructor of whole tree below them.

You can use `react-error-boundary` package to create error boundaries in your application.

```
# Installation
$ npm i react-error-boundary
```

---

!!! abstract "Core Intermediate"

## 1. What is the High-Order Components (HOCs)?

A High-Order Components (HOCs) is a function that takes a component and returns a new component.

Basically, it's a pattern that is derived from [React Compositional nature](https://felixgerschau.com/react-component-composition/).

High-order components are not part of the React API.
They are the pattern that emerges from [React Compositional nature](https://felixgerschau.com/react-component-composition/).

## 2. How React Virtual DOM works?

Virtual DOM works in this steps:

- Whenever any underlying data changes, new virtual DOM representation will be created.
- Then the difference between the previous DOM representation and the new one is calculated.
- Once the calculations are done, the real DOM will be updated with only the things that have actually changed.

## 3. What is the purpose of the `useEffect` hook in React?

The useEffect hook in React is used for performing side effects in functional components. Side effects can include data fetching, DOM manipulation, and subscribing to external data sources.

---

!!! abstract "Core Beginner"

## 1. What is the naming convention for React components?

**In React, the naming convention for components is to use PascalCase**, meaning the first letter of each word in the component's name should be capitalized. 

For example, `UserProfile`, `SidebarItem`, or `NavigationMenu`. This convention differentiates custom React components from regular HTML tags in JSX, as React treats elements starting with a lowercase letter as DOM tags and those starting with a capital letter as custom components.


## 2. What is the difference between class components and function components?

Class components let you define your components with the help of classes. You can extend from `React.Component` class to create a component. **Class components also allow you to define component level lifecycle methods**. 

Functional components are the preferred way to write React components. **There are no lifecycle methods similar to class components available in functional components**; you can use React hooks instead to manage the component lifecycle.

## 3. Can we change the state of the component directly?

No, we can't change the state of the component directly. State can only be changed by using `setState()` method. Changing the state variable directly won't re-render the component.

## 4. What is the purpose of `key` attribute in React?

The string attribute `key` is a special attribute you need to include when rendering an array of elements. Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity.

## 5. How to render HTML in React?

You can use `dangerouslySetInnerHTML` prop to render HTML in React. It is used to set HTML directly from React. You should be careful while using this property as it can cause XSS attacks.

## 6. How to render a list in React?

In React, you can render a list by using the JavaScript map function to iterate over an array of items and return a JSX element for each item. It's important to provide a unique key prop to each element in the list for **React's diffing algorithm** to function efficiently during re-renders. Here's a basic example:

```jsx
const items = ['Apple', 'Banana', 'Cherry'];

function FruitList() {
  return (
    <ul>
      {items.map((fruit, index) => (
        <li key={index}>{fruit}</li>
      ))}
    </ul>
  );
}
```

> Note: While using the index as a key can work in some cases, it's generally not recommended for dynamic lists where items can be added, removed, or reordered.

## 7. What is the difference between stateful and stateless components?

The main difference between stateful and stateless components is one has state and the other doesn't. 

Stateful components keep track of changes to their state and re-render themselves when the state changes. 

Stateless components, on the other hand, render whatever is passed to them via `props` or always render the same thing.

## 8. What's the component's lifecycle in React?

In React functional components, lifecycle-like behaviors are achieved using hooks:

**Mounting and Unmounting**

Utilizing the useEffect hook with an empty dependency array ([]) ensures the hook runs after the component mounts to the DOM.

```jsx
useEffect(() => {
  // do something after component mounts
  return () => {
    // do something before component unmounts
  };
}, []);
```

The `cleanup function` returned within the useEffect callback offers a mechanism for handling tasks when the component is about to **unmount**.



**Updates**

The useEffect hook, when invoked without a dependency array or with specific dependencies, executes after every render or when specified prop/state changes are detected.

```jsx
useEffect(() => {
  // do something after every render
});
```

```jsx
useEffect(() => {
  // do something after specific prop/state changes
}, [state1, state2]);
```

---

!!! abstract "Performance·Beginner"

## Why you shouldn't use `index` as a key in React lists and iterators?

Using `index` as a key can negatively impact performance and may cause issues with the component state. 
When the list items change due to additions, deletions, or reordering, using indexes can lead to unnecessary re-renders or even incorrect UI updates. React uses keys to identify elements in the list, and if the key is just an index, it might reuse component instances and state inappropriately.
Especially in cases where the list is dynamic or items can be reordered, it's recommended to use unique and stable identifiers as keys to ensure consistent behavior.


> Performance·Intermediate

## What is the purpose of the `useMemo` hook in React?

The `useMemo hook` is used to memoize the result of a computationally expensive operation in a functional component. It helps optimize performance by caching the result of the operation and returning the cached result on subsequent renders if the dependencies have not changed. This can prevent unnecessary calculations.

> State·Intermediate

## What is the purpose of the `useContext` hook in React?

The `useContext hook` is used to access and consume context values in functional components. It provides a way to access context data without the need for a context consumer. useContext is particularly useful when you want to access context values in nested components without having to pass props through intermediate components.

---

## Reference

- [roadmap.sh/questions/react](https://roadmap.sh/questions/react)
- [reactjs interview question : github](https://github.com/sudheerj/reactjs-interview-questions)
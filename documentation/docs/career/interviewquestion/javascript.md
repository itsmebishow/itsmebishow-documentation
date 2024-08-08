!!! abstract "Core Begineer"

## 1. Difference between `defer` and `async` attributes in JavaScript?

The main difference between defer and async ***is the order of execution.***

**Defer attribute**

A `<script>` element with a `defer` attribute, it will continue to load the HTML page and render it while the script is being downloaded. The script is executed after the HTML page has been completely parsed. `defer` scripts maintain their order in the document.

```
<script defer src="script1.js"></script>
<script defer src="script2.js"></script>
```

In the example above, `script1.js` will be executed before `script2.js`. The browser will download both scripts in parallel, but `script1.js` will be executed after the HTML page has been parsed and `script2.js` will be executed after script1.js has been executed.

**Async attribute**

On the other hand, A `<script>` element with an `async` attribute, it will pause the HTML parser and execute the script immediately after it has been downloaded. The HTML parsing will resume after the script has been executed.

```
<script async src="script1.js"></script>
<script async src="script2.js"></script>
```

In the example above, the browser will download both scripts in parallel, and execute them as soon as they are downloaded. The order of execution is not guaranteed.

To know more you can check [this diagram](https://roadmap.sh/guides/avoid-render-blocking-javascript-with-async-defer) from us that explains the difference between `defer` and `async` in a visual way.

## 2. Is it possible to run JavaScript outside the browser?

Yes, it is possible to run JavaScript outside the browser. There are several ways to run JavaScript outside the browser. You can use **Node.js**, **Deno**, **Bun**, or any other JavaScript runtime environment.

## 3. How to parse JSON in JavaScript?

In order to parse JSON, you can use the `JSON.parse()` method. It parses a JSON string and returns the JavaScript equivalent.

```
const json = '{"name":"JavaScript","year":1995}';
const roadmap = JSON.parse(json);

console.log(roadmap.name); // JavaScript
console.log(roadmap.year); // 1995
```

---

!!! abstract "Core·Intermediate*"

## 1. What is ternary operator in JavaScript?

The ternary operator is a **conditional operator that takes three operands**.
It is frequently used as a shortcut for the if statement.

```
console.log(condition ? true : false);
```

## 2. Does `map()` method mutate the original array?

No, the `map() method` **does not mutate the original array**. It returns a new array with the results of calling a provided function on every element in the calling array.

```
const roadmaps = ['JavaScript', 'React', 'Node.js'];

const renamedRoadmaps = roadmaps.map((roadmap) => {
  return `${roadmap} Roadmap`;
});

console.log(roadmaps); // ['JavaScript', 'React', 'Node.js']
console.log(renamedRoadmaps); // ['JavaScript Roadmap', 'React Roadmap', 'Node.js Roadmap']
```

## 3. What is the difference between `map()` and `forEach()` methods?

The `map()` method creates a new array with the results of calling a provided function on every element in the calling array. 

Whereas, the `forEach()` method executes a provided function once for each array element.

## 4. Does `forEach()` method return a new array?

No, the `forEach()` method does not return a new array. It simply calls a provided function on each element in the array.

```
const roadmaps = ['JavaScript', 'React', 'Node.js'];

roadmaps.forEach((roadmap) => {
  console.log(roadmap);
});
```

## 5. What is the difference between `map()` and `reduce()` methods?

The `map()` method creates a new array with the results of calling a provided function on every element in the calling array. 

***Whereas***, 
the `reduce()` method executes a reducer function (that you provide) on each element of the array, resulting in a single output value.

## 6. How to use `reduce()` method?

You can use the `reduce()` method to reduce an array to a single value. The `reduce()` method executes a reducer function (that you provide) on each element of the array, resulting in a single output value.

**Syntax**

```
array.reduce((accumulator, currentValue) => {
  // ...
}, initialValue);
```

**Example**

You can use the `reduce()` method to sum all the numbers in an array.

```
const numbers = [1, 2, 3, 4, 5, 6];

const sum = numbers.reduce((accumulator, currentValue) => {
  return accumulator + currentValue;
}, 0);

console.log(numbers); // [1, 2, 3, 4, 5, 6]
console.log(sum); // 21
```

## 7. Can you **merge multiple arrays** in JavaScript?

Yes, you can merge multiple arrays into one array using the `concat()` method, or the spread operator `....`

**concat()**

The `concat()` method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.

```
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const arr3 = arr1.concat(arr2);
console.log(arr3); // [1, 2, 3, 4, 5, 6]
```

**Spread operator**

The spread operator `...` is used to expand an iterable object into the list of arguments.

```
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const arr3 = [...arr1, ...arr2];
console.log(arr3); // [1, 2, 3, 4, 5, 6]
```


## 8. What is the spread operator in JavaScript?

The spread operator in JavaScript is represented by three dots (...). It allows the elements of an array or properties of an object to be expanded or "spread" into individual elements or properties. This can be useful in various contexts, such as when passing elements as function arguments, cloning arrays and objects, or merging arrays and objects.

```
const roadmaps = ['JavaScript', 'React', 'Node.js'];
const bestPractices = ['AWS', 'API Security'];

const resources = [...roadmaps, ...bestPractices];
console.log(resources); 
// ['JavaScript', 'React', 'Node.js', 'AWS', 'API Security']
```

```
const roadmap = {
  name: 'JavaScript',
  type: 'dynamic',
};

const roadmapClone = { ...roadmap }; // shallow copy
console.log(roadmapClone); // { name: 'JavaScript', type: 'dynamic' }
```

---

!!! abstract "Core Advanced"

## 1. Garbage collection in JavaScript?

The JavaScript engine uses automatic garbage collection. 
JavaScript automatically manages memory by freeing up space used by objects no longer needed. 
**This algorithm is called Mark and Sweep**, which is performed periodically by the JavaScript engine.

## 2. What are Heap and Stack in JavaScript?

The Heap and Stack in JavaScript Engine are two different data structures that store data in different ways.

**Stack**

The Stack is a small, organized region of memory. It is where primitive values, function calls, and local variables are stored. It follows a "Last In, First Out" (LIFO) order, meaning that the last item added to the stack is the first one to be removed. Each function invocation creates a new stack frame, which contains the function's local variables, return address, and other contextual data.

**Heap**

The Heap is a large, mostly unstructured region of memory. It is where `objects`, `arrays`, and `functions` are stored. Variables from the Stack (e.g., in functions) point to locations in the Heap for these dynamically allocated structures.

When you declare a primitive type (like a number or boolean), it's usually managed in the stack. But when you create an object, array, or function, it's stored in the heap, and the stack will hold a reference to that location in the heap.

For example:

```
// Stored on the stack
const name = 'JavaScript'; 

// `roadmap` reference on the stack, actual object { name: 'JS' } in the heap
const roadmap = { name: 'JS' }; 
```

In the code above, the primitive value `JavaScript` for variable `name` is directly stored on the stack. For the object assigned to `roadmap`, its actual data resides in the heap, and the reference to this data (a memory address pointer) is held on the stack.


--- 

> **Function Advanced**

## 1. What is IIFE in JavaScript?

The IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined.

```
(function () {
  console.log('Hello Roadmap!');
})();
```

The IIFE is frequently used to create a new scope to avoid variable hoisting from within blocks.

```
(function () {
  var roadmap = 'JavaScript';
  console.log(roadmap);
})();

console.log(roadmap); // ReferenceError: name is not defined
```

---

> Operator Beginner

## 1. What is Nullish Coalescing Operator?

The Nullish Coalescing Operator (`??`) returns the right operand if the left one is `null` or `undefined`, otherwise, it returns the left operand. It's useful for setting default values without considering falsy values like `0` or `''` as absent.

```
console.log(null ?? 'hello'); // hello
console.log(undefined ?? 'hello'); // hello
console.log('' ?? 'hello'); // ''
console.log(0 ?? 'hello'); // 
```

---

> DOM Beginner

## 1. How to measure dimensions of an Element?

You can use `getBoundingClientRect` method to get the dimensions of an element.

```
const roadmapWrapper = document.querySelector('.roadmap-wrapper');
const dimensions = roadmapWrapper.getBoundingClientRect();

console.log(dimensions); 
// DOMRect { x: 8, y: 8, width: 784, height: 784, top: 8, right: 792, bottom: 792, left: 8 }
```

## 2. How to get viewport dimensions in JavaScript?

You can use `window.innerWidth` and `window.innerHeight` to get the viewport dimensions.


## 3. How to scroll to the top of the page using JavaScript?

In order to scroll to the top of the page, we can use the `scrollTo` method.

```
window.scrollTo(0, 0);
```

---

## Reference

- [roadmap.sh/questions/javascript](https://roadmap.sh/questions/javascript)
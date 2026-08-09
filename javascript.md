## 1. What is the difference between `var`, `let`, and `const`?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`var` is function-scoped and can be redeclared. `let` is block-scoped and can be reassigned but not redeclared in the same scope. `const` is block-scoped and cannot be reassigned.

### Deep Explanation

`var` is hoisted and initialized with `undefined`, which makes it easy to accidentally use before declaration. `let` and `const` are also hoisted, but they are not usable before their declaration because they live in the Temporal Dead Zone. `const` does not make a value immutable; it only prevents reassignment of the variable binding.

### Example

```javascript
function demo() {
	if (true) {
		var a = 1;
		let b = 2;
		const c = 3;
	}

	console.log(a); // 1
	// console.log(b); // ReferenceError
	// console.log(c); // ReferenceError
}
```

### Common Follow-ups

- Why is `var` considered unsafe in modern code?
- Does `const` make arrays and objects immutable?
- Why do `let` and `const` have a temporal dead zone?

### My Answer


### Interview Notes

- Prefer `const` by default.
- Use `let` when reassignment is needed.
- Avoid `var` unless reading old code.

## 2. What is hoisting in JavaScript?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Hoisting is JavaScript's behavior of moving declarations to the top of their scope during compilation.

### Deep Explanation

Function declarations are fully hoisted, so they can be called before they appear in the file. `var` declarations are hoisted and initialized with `undefined`. `let`, `const`, and class declarations are hoisted too, but they are not initialized until execution reaches their declaration line.

### Example

```javascript
console.log(x); // undefined
var x = 10;

sayHi(); // "hi"
function sayHi() {
	console.log("hi");
}
```

### Common Follow-ups

- What is the difference between hoisting for `var` and `let`?
- Are function expressions hoisted the same way as function declarations?
- How does hoisting relate to the Temporal Dead Zone?

### My Answer


### Interview Notes

- Hoisting affects declarations, not assignments.
- Function declarations are the most hoisted form.
- TDZ applies to `let`, `const`, and class declarations.

## 3. What is the difference between `==` and `===`?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`==` compares values after type coercion. `===` compares both value and type without coercion.

### Deep Explanation

Loose equality (`==`) can produce surprising results because JavaScript may convert one operand before comparing. Strict equality (`===`) is usually preferred because it is predictable and easier to reason about. In interviews, it is often best to say that `===` should be the default choice.

### Example

```javascript
0 == "0";   // true
0 === "0";  // false

null == undefined;  // true
null === undefined; // false
```

### Common Follow-ups

- Why does `null == undefined` evaluate to true?
- When, if ever, is `==` acceptable?
- What are some other coercion pitfalls?

### My Answer


### Interview Notes

- Prefer `===` in production code.
- Know the common edge cases with `null` and `undefined`.
- Coercion is one of the biggest sources of bugs in JavaScript.

## 4. What are primitive and reference types?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Primitive types store the actual value directly. Reference types store a reference to a location in memory that contains the value.

### Deep Explanation

Primitive values include `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, and `bigint`. Objects, arrays, and functions are reference types. When you assign or pass a primitive, JavaScript copies the value. When you assign or pass an object, JavaScript copies the reference, so multiple variables can point to the same object.

### Example

```javascript
let a = 5;
let b = a;
b = 10;
console.log(a); // 5

let user1 = { name: "A" };
let user2 = user1;
user2.name = "B";
console.log(user1.name); // "B"
```

### Common Follow-ups

- Why are objects compared by reference?
- Are arrays primitive or reference types?
- Is `null` a primitive or an object?

### My Answer


### Interview Notes

- Primitives are immutable values.
- Objects are mutable and shared by reference.
- `typeof null` returning `"object"` is a historical bug.

## 5. How does JavaScript pass values to functions?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

JavaScript passes arguments by value, but when the value is an object, the copied value is a reference to that object.

### Deep Explanation

This is sometimes described as "pass-by-sharing". The function receives a copy of the argument. For primitives, that copy is the value itself. For objects, that copy is a reference to the same object, so the function can mutate the original object through that reference. Reassigning the parameter inside the function does not change the caller's variable.

### Example

```javascript
function changePrimitive(x) {
	x = 10;
}

let n = 5;
changePrimitive(n);
console.log(n); // 5

function changeObject(user) {
	user.name = "New";
}

let person = { name: "Old" };
changeObject(person);
console.log(person.name); // "New"
```

### Common Follow-ups

- Is JavaScript pass-by-value or pass-by-reference?
- Why can objects be mutated inside a function?
- What happens when you reassign an object parameter?

### My Answer


### Interview Notes

- The parameter itself is always a local copy.
- Object mutation affects shared state.
- Reassignment inside a function does not affect the caller.

## 6. What is scope? Explain global, function, and block scope.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Scope determines where a variable can be accessed. Global scope is accessible everywhere, function scope is accessible only inside the function, and block scope is accessible only inside the nearest block.

### Deep Explanation

JavaScript uses lexical scoping, so scope is determined by where code is written. Variables declared with `var` are function-scoped, not block-scoped. Variables declared with `let` and `const` are block-scoped. Global variables are accessible from most places, but relying on them makes code harder to maintain.

### Example

```javascript
let globalValue = "global";

function demo() {
	var functionValue = "function";

	if (true) {
		let blockValue = "block";
		console.log(globalValue);
		console.log(functionValue);
		console.log(blockValue);
	}
}
```

### Common Follow-ups

- How do `var`, `let`, and `const` differ in scope?
- What is lexical scope?
- Why should global scope be avoided when possible?

### My Answer


### Interview Notes

- `var` is function-scoped.
- `let` and `const` are block-scoped.
- Scope helps avoid naming collisions and accidental bugs.

## 7. What is a closure?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

A closure is a function that remembers and can access variables from its outer lexical scope even after that outer function has finished executing.

### Deep Explanation

Closures happen because functions in JavaScript carry a reference to the environment where they were created. This lets inner functions keep using outer variables later. Closures are useful for data privacy, stateful functions, callbacks, and preserving values in async code.

### Example

```javascript
function createCounter() {
	let count = 0;

	return function () {
		count += 1;
		return count;
	};
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```
### Common Follow-ups

- Why does the inner function still have access to `count`?
- How are closures used in callbacks and event handlers?
- Can closures cause memory leaks?

### My Answer


### Interview Notes

- A closure is function plus preserved lexical environment.
- Closures are one of the most important JavaScript concepts.
- Be ready to explain them with a practical example.

## 8. Give a real-world use case for closures.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Closures are commonly used for private state, such as counters, caches, and factories that return configured functions.

### Deep Explanation

In real applications, closures let you hide implementation details while exposing a small public API. They are also useful in asynchronous code, for example when you need a callback to remember the request ID, timer value, or current user context. Another common use is memoization, where a function remembers previously computed results.

### Example

```javascript
function createApiClient(baseUrl) {
	return function request(path) {
		return `${baseUrl}${path}`;
	};
}

const client = createApiClient("https://api.example.com");
console.log(client("/users"));
```

### Common Follow-ups

- How do closures help with private data?
- How are closures used in memoization?
- What is a common closure bug inside loops?

### My Answer


### Interview Notes

- Mention private state or factory functions in interviews.
- Closures are also common in React hooks and event handlers.
- Loop-related closure bugs often appear with `var`.

## 9. What is lexical scope?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Lexical scope means a variable's scope is determined by where it is written in the source code, not by where it is called from.

### Deep Explanation

When JavaScript parses your code, it builds a scope chain based on nested blocks and functions. Inner functions can access variables from outer scopes because the structure of the code defines those relationships. This is why closures work: the outer variables remain reachable through the lexical environment.

### Example

```javascript
function outer() {
	const message = "hello";

	function inner() {
		console.log(message);
	}

	inner();
}
```

### Common Follow-ups

- How is lexical scope different from dynamic scope?
- How does lexical scope relate to closures?
- Why is lexical scope important for readability?

### My Answer


### Interview Notes

- JavaScript uses lexical scope.
- Scope is determined at write time, not call time.
- Closures depend on lexical scope.

## 10. What is the Temporal Dead Zone?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

The Temporal Dead Zone is the period between entering a scope and the declaration of a `let`, `const`, or class variable, during which the variable cannot be accessed.

### Deep Explanation

Although these variables are hoisted, they are not initialized until execution reaches their declaration. Accessing them earlier throws a `ReferenceError`. The TDZ helps catch bugs by preventing use of variables before they are properly declared.

### Example

```javascript
{
	// console.log(name); // ReferenceError
	let name = "Ava";
	console.log(name);
}
```

### Common Follow-ups

- Why does the TDZ exist?
- How is TDZ different from hoisting with `var`?
- Do function declarations have a TDZ?

### My Answer


### Interview Notes

- TDZ applies to `let`, `const`, and class declarations.
- `var` does not have a TDZ in the same way.
- This is a common interview edge case.

## 11. What is the difference between regular functions and arrow functions?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Regular functions have their own `this`, `arguments`, `prototype`, and can be used as constructors. Arrow functions do not create their own `this` or `arguments` and cannot be used as constructors.

### Deep Explanation

Arrow functions inherit `this` from the surrounding lexical scope, which makes them useful in callbacks where you want to preserve context. Regular functions determine `this` based on how they are called. Regular functions can be invoked with `new`, while arrow functions cannot. Because arrow functions do not have their own `prototype`, they are not suitable for methods that need constructor behavior.

### Example

```javascript
const user = {
	name: "Mina",
	regular: function () {
		console.log(this.name);
	},
	arrow: () => {
		console.log(this.name);
	}
};

user.regular(); // "Mina"
user.arrow(); // undefined in most cases
```

### Common Follow-ups

- When should I prefer an arrow function?
- Why does `this` behave differently in arrow functions?
- Can arrow functions be constructors?

### My Answer


### Interview Notes

- Arrow functions are great for concise callbacks.
- Regular functions are needed when you want dynamic `this`.
- Know the `arguments` difference too.

## 12. How does `this` work in JavaScript?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`this` refers to the object that is currently calling the function, but its value depends on how the function is invoked.

### Deep Explanation

In a regular function, `this` is determined at call time. Called as a method, `this` points to the object before the dot. Called as a plain function in strict mode, `this` is `undefined`. With `new`, `this` refers to the newly created instance. `call`, `apply`, and `bind` can explicitly set `this`. Arrow functions do not bind their own `this`; they capture it from the surrounding scope.

### Example

```javascript
const person = {
	name: "Leila",
	sayName() {
		console.log(this.name);
	}
};

person.sayName(); // "Leila"
```

### Common Follow-ups

- What is the default value of `this` in strict mode?
- How do `call`, `apply`, and `bind` affect `this`?
- Why does `this` inside arrow functions behave differently?

### My Answer


### Interview Notes

- Focus on invocation style, not declaration style.
- `this` is one of the most misunderstood parts of JavaScript.
- Arrow functions use lexical `this`.

## 13. What are `call`, `apply`, and `bind`?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

They are methods used to control the value of `this` when calling a function.

### Deep Explanation

`call` invokes the function immediately and passes arguments one by one. `apply` also invokes immediately but accepts arguments as an array. `bind` returns a new function with `this` permanently set to the provided value, which is useful for callbacks and event handlers.

### Example

```javascript
function greet(greeting) {
	return `${greeting}, ${this.name}`;
}

const user = { name: "Sara" };

console.log(greet.call(user, "Hi"));
console.log(greet.apply(user, ["Hello"]));

const bound = greet.bind(user);
console.log(bound("Hey"));
```

### Common Follow-ups

- What is the difference between `call` and `apply`?
- When would you use `bind` instead of `call`?
- Does `bind` execute the function right away?

### My Answer


### Interview Notes

- `call` and `apply` run immediately.
- `bind` returns a new function.
- `apply` is convenient when arguments are already in an array.

## 14. What is prototypal inheritance?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Prototypal inheritance is the mechanism where objects inherit properties and methods from other objects through the prototype chain.

### Deep Explanation

Every object in JavaScript has an internal link to another object called its prototype. When you access a property, JavaScript first looks on the object itself. If it is not found, it looks up the prototype chain until it finds the property or reaches `null`. This is how shared behavior can be reused without copying methods onto every instance.

### Example

```javascript
const parent = {
	greet() {
		return "hello";
	}
};

const child = Object.create(parent);
console.log(child.greet()); // "hello"
```

### Common Follow-ups

- How is prototypal inheritance different from class inheritance?
- What is `Object.create` used for?
- What happens when a property exists on both the object and its prototype?

### My Answer


### Interview Notes

- JavaScript inheritance is prototype-based.
- Objects delegate property lookups to their prototypes.
- Shared methods usually live on prototypes to save memory.

## 15. What is the prototype chain?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

The prototype chain is the sequence of objects JavaScript searches when looking up a property or method.

### Deep Explanation

When a property is not found directly on an object, JavaScript follows the object's prototype, then that prototype's prototype, and so on until it reaches `null`. This lookup path is called the prototype chain. It is central to how inheritance and method sharing work in JavaScript.

### Example

```javascript
const arr = [];
console.log(arr.toString());
console.log(Object.getPrototypeOf(arr));
```

### Common Follow-ups

- How does property lookup work along the chain?
- What is the difference between `__proto__` and `prototype`?
- Why does every object eventually inherit from `Object.prototype`?

### My Answer


### Interview Notes

- The chain ends at `null`.
- Methods like `toString` come from prototypes.
- Understanding the chain helps with debugging weird lookup behavior.

## 16. What is the difference between shallow copy and deep copy?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

A shallow copy duplicates only the top level, while a deep copy duplicates nested objects as well.

### Deep Explanation

With a shallow copy, nested reference values are still shared between the original and the copy. That means changing a nested object in one affects the other. A deep copy creates an entirely separate structure, so nested changes do not leak across copies.

### Example

```javascript
const original = { name: "A", address: { city: "Cairo" } };
const shallow = { ...original };
shallow.address.city = "Alex";

console.log(original.address.city); // "Alex"
```

### Common Follow-ups

- Why is spread syntax only a shallow copy?
- What are common ways to deep copy objects?
- Are functions and special objects easy to deep copy?

### My Answer


### Interview Notes

- Shallow copy is enough for flat objects.
- Deep copy is needed when nested state must be isolated.
- Be careful with `JSON.parse(JSON.stringify(...))` limitations.

## 17. Explain destructuring.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Destructuring is syntax for unpacking values from arrays or properties from objects into variables.

### Deep Explanation

It makes code shorter and easier to read when extracting multiple values. Object destructuring matches property names, while array destructuring matches positions. You can also rename variables, provide default values, and destructure nested structures.

### Example

```javascript
const user = { name: "Omar", age: 29 };
const { name, age } = user;

const numbers = [1, 2, 3];
const [first, second] = numbers;
```

### Common Follow-ups

- How do you rename a destructured property?
- How do default values work in destructuring?
- Can destructuring be nested?

### My Answer


### Interview Notes

- Object destructuring uses property names.
- Array destructuring uses order.
- Destructuring is common in React and modern JS.

## 18. Explain spread vs rest operators.

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Spread expands values, while rest collects values.

### Deep Explanation

The same `...` syntax is used in two different contexts. Spread is used when you want to expand an iterable or object into individual elements or properties. Rest is used in function parameters or destructuring to collect remaining items into an array or object.

### Example

```javascript
const arr1 = [1, 2];
const arr2 = [...arr1, 3];

function sum(...values) {
	return values.reduce((total, value) => total + value, 0);
}
```

### Common Follow-ups

- How is spread used with objects?
- Where can rest parameters be used?
- Why is spread a shallow copy?

### My Answer


### Interview Notes

- Spread expands, rest gathers.
- Rest parameters must be last in a function signature.
- The syntax looks the same but the usage is different.

## 19. What are higher-order functions?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Higher-order functions are functions that take other functions as arguments, return functions, or both.

### Deep Explanation

They are a core part of functional JavaScript. Methods like `map`, `filter`, `reduce`, and event handlers all rely on higher-order functions. They help separate behavior from data and make code more reusable.

### Example

```javascript
function createMultiplier(multiplier) {
	return function (value) {
		return value * multiplier;
	};
}

const double = createMultiplier(2);
console.log(double(5)); // 10
```

### Common Follow-ups

- Is `map` a higher-order function?
- Why are callbacks useful?
- Can a higher-order function return another function?

### My Answer


### Interview Notes

- Callbacks are a common form of higher-order functions.
- They are essential in async and array methods.
- Closures often appear together with higher-order functions.

## 20. What are pure functions?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

A pure function always returns the same output for the same input and does not cause side effects.

### Deep Explanation

Pure functions are predictable and easier to test. They do not modify external state, read random values, or depend on mutable shared data. Because of this, they are a common goal in functional programming and state management.

### Example

```javascript
function add(a, b) {
	return a + b;
}
```

### Common Follow-ups

- What counts as a side effect?
- Why are pure functions easier to test?
- Can a function read from arguments and still be pure?

### My Answer


### Interview Notes

- Pure functions are deterministic.
- Avoid mutation and hidden dependencies.
- They improve reliability and testability.

## 21. Explain the JavaScript Event Loop.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

The event loop coordinates execution between the call stack and queued asynchronous tasks so JavaScript can handle non-blocking work.

### Deep Explanation

JavaScript runs on a single main thread, so it cannot execute everything at once. Synchronous code runs on the call stack. When async work finishes, its callback is placed into a queue. The event loop continuously checks whether the call stack is empty and then moves queued work onto the stack. This is what allows timers, network requests, and UI events to be handled without freezing the page.

### Example

```javascript
console.log("start");

setTimeout(() => {
	console.log("timeout");
}, 0);

Promise.resolve().then(() => console.log("promise"));

console.log("end");
```

### Common Follow-ups

- Why does `Promise.then` run before `setTimeout`?
- What role does the call stack play?
- Is JavaScript itself multithreaded?

### My Answer


### Interview Notes

- Event loop enables non-blocking behavior.
- Microtasks usually run before macrotasks.
- This is one of the most common interview topics.

## 22. Explain Call Stack, Web APIs, Task Queue, and Microtask Queue.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

The call stack runs synchronous code, Web APIs handle browser-provided async work, the task queue stores callback tasks, and the microtask queue stores promise-related jobs.

### Deep Explanation

The call stack is where functions execute. Browser APIs like `setTimeout`, DOM events, and fetch work outside the stack. When they finish, their callbacks are queued. Task queue callbacks are processed after the stack clears. Microtasks, such as promise resolutions and `queueMicrotask`, have higher priority and run before the next task queue item.

### Example

```javascript
console.log("A");

setTimeout(() => console.log("B"), 0);

Promise.resolve().then(() => console.log("C"));

console.log("D");
```

### Common Follow-ups

- Why do microtasks run before tasks?
- What belongs to Web APIs in the browser?
- How does this differ in Node.js?

### My Answer


### Interview Notes

- Microtasks have priority over tasks.
- The call stack must be empty before queued work runs.
- Knowing the order helps explain async output.

## 23. What is the difference between Promises and `async/await`?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`async/await` is syntax built on top of Promises that makes asynchronous code easier to read and write.

### Deep Explanation

A Promise represents a value that will be available in the future. `async/await` lets you write promise-based code in a more synchronous style. An `async` function always returns a Promise, and `await` pauses that function until the Promise settles. Under the hood, both are still based on Promises.

### Example

```javascript
async function getData() {
	const response = await fetch("/api/data");
	return response.json();
}
```

### Common Follow-ups

- Is `async/await` better than `.then()`?
- What happens if an `async` function throws?
- How do you handle errors with `await`?

### My Answer


### Interview Notes

- `async/await` improves readability.
- Use `try/catch` for error handling.
- Promises remain the underlying primitive.

## 24. What is the difference between `Promise.all`, `allSettled`, `race`, and `any`?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`Promise.all` resolves when all succeed, `allSettled` waits for all outcomes, `race` settles with the first settled promise, and `any` resolves with the first fulfilled promise.

### Deep Explanation

`Promise.all` is useful when every task must succeed. If one rejects, the whole result rejects immediately. `Promise.allSettled` is useful when you want a full report of successes and failures. `Promise.race` is useful for timeout or fastest-response scenarios because it settles as soon as one promise settles. `Promise.any` ignores rejections until one promise fulfills, and it rejects only if all promises reject.

### Example

```javascript
const p1 = Promise.resolve("A");
const p2 = Promise.reject("B");

Promise.all([p1, p2]).catch(console.log);
Promise.allSettled([p1, p2]).then(console.log);
```

### Common Follow-ups

- When should I use `allSettled` instead of `all`?
- What happens if all promises reject in `any`?
- How is `race` different from `any`?

### My Answer


### Interview Notes

- `all` fails fast.
- `allSettled` never short-circuits.
- `any` returns the first success.

## 25. Explain debouncing vs throttling and give use cases.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Debouncing waits until activity stops before running a function, while throttling limits how often a function can run during repeated activity.

### Deep Explanation

Debouncing is useful for search inputs, resizing, or autosave, where you want one final action after the user stops triggering events. Throttling is useful for scroll handlers, analytics, or drag events, where you want periodic updates but not on every event. Debounce groups bursts into one call, while throttle guarantees execution at a steady rate.

### Example

```javascript
function debounce(fn, delay) {
	let timer;
	return function (...args) {
		clearTimeout(timer);
		timer = setTimeout(() => fn.apply(this, args), delay);
	};
}
```

### Common Follow-ups

- When should I use debounce instead of throttle?
- Can both be implemented with `setTimeout`?
- How do these patterns help performance?

### My Answer


### Interview Notes

- Debounce waits for silence.
- Throttle enforces a rate limit.
- These are common performance patterns in UI code.

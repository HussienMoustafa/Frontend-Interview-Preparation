## What is React and why is it used?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

React is a JavaScript library for building user interfaces with reusable components and efficient updates.

### Deep Explanation

React helps you model the UI as a composition of components that describe how the interface should look for a given state. It uses a declarative approach, which means you describe the output and let React handle DOM updates. This makes complex UIs easier to reason about, especially when state changes often.

### Example

```jsx
function Greeting({ name }) {
	return <h1>Hello, {name}</h1>;
}
```

### Common Follow-ups

- Why is React considered declarative?
- What problems does component reuse solve?
- Is React a framework or a library?

### My Answer


### Interview Notes

- React focuses on UI composition.
- Components and state are the core ideas.
- It is widely used for interactive web apps.

## What is the difference between props and state?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Props are inputs passed from parent to child, while state is local data managed inside a component.

### Deep Explanation

Props are read-only from the child’s perspective and are used to configure or feed data into components. State belongs to the component and changes over time in response to user actions, network responses, or other events. A component usually renders based on a combination of props and state.

### Example

```jsx
function Counter({ initialValue }) {
	const [count, setCount] = useState(initialValue);
}
```

### Common Follow-ups

- Can props be changed inside a component?
- When should data live in state instead of props?
- What is derived state?

### My Answer


### Interview Notes

- Props flow down.
- State is owned locally.
- Keep state as minimal as possible.

## What causes a React component to re-render?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

A component re-renders when its state changes, its props change, or its parent re-renders and passes new values.

### Deep Explanation

React re-renders to produce a new UI description whenever it thinks something relevant has changed. A state update always schedules a re-render of that component. A parent render can also trigger child renders unless React can bail out with memoization or unchanged props. Context changes and certain hook updates can also cause re-renders.

### Example

```jsx
const [count, setCount] = useState(0);
setCount(count + 1);
```

### Common Follow-ups

- Does every re-render update the DOM?
- Why do parent re-renders affect children?
- How can you reduce unnecessary re-renders?

### My Answer


### Interview Notes

- Re-rendering is normal.
- Not every render leads to DOM changes.
- Memoization can help when it matters.

## What is the Virtual DOM?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

The Virtual DOM is an in-memory representation of the UI that React uses to compare changes before updating the real DOM.

### Deep Explanation

React builds a tree of lightweight JavaScript objects that describe the UI. When state changes, React creates a new tree and compares it with the previous one. This comparison helps React compute the smallest set of real DOM updates needed. The Virtual DOM is not faster by magic; it is a useful abstraction for predictable UI updates.

### Example

```jsx
return <div>{count}</div>;
```

### Common Follow-ups

- Is the Virtual DOM the same as the real DOM?
- Why not update the DOM directly every time?
- How does diffing help performance?

### My Answer


### Interview Notes

- It is a representation, not the browser DOM.
- React compares old and new trees.
- The goal is efficient, predictable updates.

## Explain reconciliation.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Reconciliation is React’s process of comparing old and new UI trees to decide what changed and what should be updated.

### Deep Explanation

When a component re-renders, React creates a new tree of elements and compares it with the previous one. It uses heuristics to determine which parts can be reused and which need to be replaced. Keys play a big role in helping React match list items correctly. Reconciliation is how React keeps UI updates efficient and predictable.

### Example

```jsx
items.map((item) => <li key={item.id}>{item.name}</li>)
```

### Common Follow-ups

- Why are keys important in reconciliation?
- What does React compare during diffing?
- How does component identity affect reuse?

### My Answer


### Interview Notes

- Reconciliation is diffing plus update planning.
- Stable keys improve correctness.
- It explains why some UI changes are reused and others are remounted.

## Why are keys important when rendering lists?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Keys help React identify which list items changed, were added, or were removed.

### Deep Explanation

Without stable keys, React may reuse the wrong DOM elements or component instances when list order changes. Good keys let React preserve state for the correct item and reduce unnecessary re-renders. Using array indexes as keys is risky when the list can reorder, insert, or delete items.

### Example

```jsx
{todos.map((todo) => (
	<li key={todo.id}>{todo.title}</li>
))}
```

### Common Follow-ups

- Why is using the array index as a key sometimes a problem?
- What makes a key stable?
- Can keys be duplicated?

### My Answer


### Interview Notes

- Keys should be stable and unique among siblings.
- Prefer IDs from your data.
- Keys help React preserve component identity.

## What happens when state changes?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

State updates schedule a re-render, React computes the new UI, and then it updates the DOM if needed.

### Deep Explanation

When you call a state setter like `setCount`, React queues an update rather than changing the UI immediately. It then re-renders the component with the new state, reconciles the result with the previous render, and commits any necessary DOM changes. Modern React may batch multiple updates together for efficiency.

### Example

```jsx
setCount((current) => current + 1);
```

### Common Follow-ups

- Is state updated synchronously?
- What is batching?
- Why should you use the functional state updater sometimes?

### My Answer


### Interview Notes

- State updates are queued.
- React may batch multiple updates.
- The DOM update happens after reconciliation.

## What is the difference between controlled and uncontrolled components?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Controlled components store form values in React state, while uncontrolled components let the DOM manage the input state.

### Deep Explanation

In controlled components, the value is driven by React state and updated through `onChange`. This gives you full control and makes validation easier. Uncontrolled components use refs to read values directly from the DOM, which can be simpler for quick forms or integrations with non-React code.

### Example

```jsx
<input value={value} onChange={(e) => setValue(e.target.value)} />
```

### Common Follow-ups

- When is uncontrolled better?
- Why are controlled forms common in React?
- How do refs fit in?

### My Answer


### Interview Notes

- Controlled is the default for most React forms.
- Uncontrolled can be simpler in some cases.
- Refs are often used with uncontrolled inputs.

## What is lifting state up?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Lifting state up means moving shared state to the nearest common parent so multiple children can use it.

### Deep Explanation

When two or more components need the same state, keeping separate copies can cause them to get out of sync. By moving the state to a shared parent, you keep a single source of truth and pass the value and updater down as props. This is a common React pattern for forms, tabs, filters, and synchronized views.

### Example

```jsx
function Parent() {
	const [value, setValue] = useState("");
}
```

### Common Follow-ups

- What is a single source of truth?
- When do you lift state too far up?
- How does this relate to props drilling?

### My Answer


### Interview Notes

- Shared state should live where it is needed.
- Lifting state up reduces duplication.
- It often leads to cleaner data flow.

## What is prop drilling and how can you solve it?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Prop drilling is passing props through multiple layers just to reach a deeply nested component. It can be solved with Context, component composition, or state management libraries.

### Deep Explanation

Prop drilling is not inherently wrong, but it becomes noisy when intermediate components do not actually need the data. Context helps when many components need the same value. For more complex applications, external state stores or better composition patterns can reduce the need for long prop chains.

### Example

```jsx
<App user={user} />
```

### Common Follow-ups

- When is prop drilling acceptable?
- Why can Context be overused?
- What is a better alternative in large apps?

### My Answer


### Interview Notes

- Prop drilling is a symptom of deeply shared data.
- Context is the usual first fix.
- Avoid solving small problems with large global state.

## Explain `useState`.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`useState` is a React Hook that lets a component store and update local state.

### Deep Explanation

It returns a state value and a setter function. Calling the setter schedules a re-render with the new value. You can initialize state with a value or a lazy initializer function. For derived or shared data, other patterns may be more appropriate than local state.

### Example

```jsx
const [count, setCount] = useState(0);
```

### Common Follow-ups

- Why use the functional updater form?
- Can `useState` hold objects and arrays?
- How does lazy initialization work?

### My Answer


### Interview Notes

- `useState` is for local mutable UI state.
- State updates trigger re-renders.
- The setter should not be treated as synchronous.

## Explain `useEffect`.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`useEffect` runs side effects after rendering, such as fetching data, subscriptions, timers, or DOM interactions.

### Deep Explanation

Effects are for syncing React with external systems. They run after the render is committed, which keeps rendering pure. If the effect returns a function, that function is used for cleanup before the effect re-runs or the component unmounts. Choosing the right dependencies is critical for correct behavior.

### Example

```jsx
useEffect(() => {
	document.title = count.toString();
}, [count]);
```

### Common Follow-ups

- Why not do side effects during render?
- What does the cleanup function do?
- When does `useEffect` run?

### My Answer


### Interview Notes

- Effects sync React with the outside world.
- Keep render logic pure.
- Cleanup prevents leaks and stale subscriptions.

## How does the `useEffect` dependency array work?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

The dependency array tells React when to re-run an effect by listing the values the effect depends on.

### Deep Explanation

If a value used inside the effect changes, the effect should usually re-run so it stays in sync. An empty array means the effect runs once after mount, while omitting the array runs it after every render. Incorrect dependencies can cause stale values, missed updates, or infinite loops.

### Example

```jsx
useEffect(() => {
	fetchData(userId);
}, [userId]);
```

### Common Follow-ups

- Why does ESLint warn about missing dependencies?
- What happens with an empty array?
- Why can object dependencies be tricky?

### My Answer


### Interview Notes

- Dependencies should match values used in the effect.
- The array controls re-execution, not initial mount only.
- Stable references help avoid unnecessary reruns.

## What is the cleanup function in `useEffect`?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

The cleanup function runs before an effect re-runs and when the component unmounts.

### Deep Explanation

Cleanup is used to remove subscriptions, clear timers, cancel requests, or release resources created by the effect. It prevents memory leaks and stale updates. If the effect subscribes to something external, cleanup is usually required.

### Example

```jsx
useEffect(() => {
	const id = setInterval(() => console.log("tick"), 1000);
	return () => clearInterval(id);
}, []);
```

### Common Follow-ups

- When is cleanup necessary?
- Does cleanup run on every render?
- How does cleanup help with subscriptions?

### My Answer


### Interview Notes

- Cleanup prevents leaks and duplication.
- It runs before the next effect and on unmount.
- Think about anything that needs teardown.

## What problems can occur with incorrect `useEffect` dependencies?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Incorrect dependencies can cause stale data, repeated side effects, missed updates, and infinite render loops.

### Deep Explanation

If a dependency is missing, the effect may keep using old values and produce wrong behavior. If too many unstable values are included, the effect can re-run too often and create loops or performance issues. Correct dependency management is one of the most important parts of writing reliable React effects.

### Example

```jsx
useEffect(() => {
	loadUser(userId);
}, []);
```

### Common Follow-ups

- What is a stale closure?
- Why is `useEffect` dependency management tricky?
- How can you stabilize function dependencies?

### My Answer


### Interview Notes

- Missing dependencies often create stale bugs.
- Extra unstable dependencies can cause loops.
- Follow lint rules and understand the data flow.

## What is the difference between `useMemo` and `useCallback`?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`useMemo` memoizes a computed value, while `useCallback` memoizes a function reference.

### Deep Explanation

Use `useMemo` when a calculation is expensive or when you need to preserve an object or array reference between renders. Use `useCallback` when you want to avoid recreating a function unless dependencies change. Both are optimization tools, not default requirements.

### Example

```jsx
const filtered = useMemo(() => items.filter(Boolean), [items]);
const handleClick = useCallback(() => setOpen(true), []);
```

### Common Follow-ups

- Are these hooks always needed?
- What is the real cost of recreating a function?
- When does memoization actually help?

### My Answer


### Interview Notes

- `useMemo` memoizes results.
- `useCallback` memoizes function identity.
- Avoid using them everywhere by default.

## What is `React.memo`?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`React.memo` memoizes a component so it only re-renders when its props change.

### Deep Explanation

It performs a shallow comparison of props by default and can skip rendering when props are unchanged. This is useful for expensive components that often receive the same inputs. However, if props change often or the component is cheap to render, `React.memo` may add complexity without much benefit.

### Example

```jsx
const Item = React.memo(function Item({ name }) {
	return <div>{name}</div>;
});
```

### Common Follow-ups

- When does `React.memo` help?
- Does it compare deeply?
- How do function props affect memoization?

### My Answer


### Interview Notes

- It is a rendering optimization.
- Props are shallow-compared by default.
- Use it selectively, not everywhere.

## When should you use `useMemo`?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Use `useMemo` when a computation is expensive or when you need a stable reference for a derived value.

### Deep Explanation

If a value is cheap to compute, `useMemo` often adds more complexity than value. It becomes useful when calculations are heavy, or when changing object identity causes unnecessary child renders or effect reruns. The goal is to optimize actual bottlenecks, not to memoize everything by habit.

### Example

```jsx
const visibleItems = useMemo(() => expensiveFilter(items), [items]);
```

### Common Follow-ups

- Can `useMemo` hurt performance?
- Is it okay to return objects from `useMemo`?
- How do you know a memoization is needed?

### My Answer


### Interview Notes

- Use it for expensive calculations or stable references.
- Measure before optimizing.
- Keep the dependency list accurate.

## When should you use `useCallback`?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Use `useCallback` when you need a stable function reference, usually to work with memoized children or effect dependencies.

### Deep Explanation

Every render normally creates new function identities. That is fine in many cases, but it can defeat memoization or retrigger effects if the function is used as a dependency. `useCallback` helps when function identity matters more than function creation cost.

### Example

```jsx
const handleSubmit = useCallback(() => {
	setOpen(false);
}, []);
```

### Common Follow-ups

- Is `useCallback` just `useMemo` for functions?
- When is a stable callback useful?
- Can `useCallback` be overused?

### My Answer


### Interview Notes

- Use it when identity matters.
- It is often paired with `React.memo`.
- Avoid unnecessary memoization.

## What are custom hooks and why would you create one?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Custom hooks are reusable functions that combine React Hooks to share stateful logic between components.

### Deep Explanation

A custom hook lets you extract repeated behavior such as fetching, form handling, event subscriptions, or local persistence into a named function. This improves reuse without changing the component tree. It also keeps components smaller and easier to read.

### Example

```jsx
function useWindowWidth() {
	const [width, setWidth] = useState(window.innerWidth);
}
```

### Common Follow-ups

- Why do custom hooks start with `use`?
- What logic belongs in a custom hook?
- Can custom hooks share state between components?

### My Answer


### Interview Notes

- Custom hooks are for shared logic, not shared UI.
- They make components cleaner.
- The `use` prefix is required for linting and conventions.

## How do you prevent unnecessary re-renders?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

You prevent unnecessary re-renders by keeping state local, memoizing only when needed, stabilizing props, and avoiding overly broad context updates.

### Deep Explanation

Start by understanding what causes the render rather than optimizing blindly. Split components so state changes affect only the necessary subtree. Use `React.memo`, `useMemo`, and `useCallback` where identity or expensive work is actually causing a problem. Also avoid recreating large objects and functions unless necessary.

### Example

```jsx
const MemoChild = React.memo(Child);
```

### Common Follow-ups

- How do you find the cause of a render?
- When is memoization not worth it?
- How does context affect renders?

### My Answer


### Interview Notes

- Optimize after measuring.
- Keep state as close as possible to where it is used.
- Memoization is a tool, not a default.

## What is Context API and when should you use it?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Context is a way to pass data through the component tree without prop drilling.

### Deep Explanation

It is useful for app-wide concerns like theme, auth user, locale, or feature flags. Context is not ideal for highly volatile data that changes constantly, because many consumers may re-render when the value changes. For large or frequently updated state, a dedicated state management solution may be better.

### Example

```jsx
const ThemeContext = createContext("light");
```

### Common Follow-ups

- What are the downsides of Context?
- Why can Context cause performance issues?
- When should you choose a store instead?

### My Answer


### Interview Notes

- Great for shared, relatively stable data.
- Avoid using it as a universal state store.
- Context reduces prop drilling.

## What are React Error Boundaries?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Error Boundaries are components that catch rendering errors in their child tree and show a fallback UI.

### Deep Explanation

They help prevent a single component failure from crashing the entire app. Error Boundaries catch errors during rendering, lifecycle methods, and constructors in their descendant tree. They do not catch errors in event handlers or async code directly.

### Example

```jsx
<ErrorBoundary fallback={<p>Something went wrong</p>}>
	<App />
</ErrorBoundary>
```

### Common Follow-ups

- What kinds of errors do they catch?
- Can hooks replace error boundaries?
- Why are they useful in production?

### My Answer


### Interview Notes

- They improve resilience.
- They only catch render-tree errors.
- A fallback UI is required.

## What is lazy loading in React?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Lazy loading means loading components only when they are needed instead of bundling them upfront.

### Deep Explanation

React supports code splitting through `React.lazy` and `Suspense`. This can reduce initial bundle size and improve startup performance. It is useful for routes, modals, heavy charts, or infrequently used features.

### Example

```jsx
const Settings = React.lazy(() => import("./Settings"));
```

### Common Follow-ups

- What is `Suspense` used for?
- When should you lazy load?
- Does lazy loading always improve performance?

### My Answer


### Interview Notes

- Lazy load expensive or infrequent code.
- Pair with a fallback UI.
- Don’t split too aggressively.

## What is code splitting?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Code splitting breaks a large JavaScript bundle into smaller chunks that load on demand.

### Deep Explanation

It improves initial load time by sending only the code needed for the first screen. Additional chunks can be loaded later when the user navigates or interacts with the app. In React, this is often done with dynamic imports and lazy-loaded routes or components.

### Example

```jsx
const AdminPage = React.lazy(() => import("./AdminPage"));
```

### Common Follow-ups

- How is code splitting related to lazy loading?
- What are the tradeoffs of many small chunks?
- How does bundling affect performance?

### My Answer


### Interview Notes

- Code splitting improves startup performance.
- It reduces initial bundle size.
- Use it where the user does not need everything immediately.

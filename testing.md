## What is the difference between unit, integration, and end-to-end testing?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Unit tests verify small pieces in isolation, integration tests verify multiple pieces working together, and end-to-end tests verify the full user flow.

### Deep Explanation

Unit tests are fast and focused on a single function, component, or module. Integration tests ensure that modules cooperate correctly, such as a form interacting with state and API logic. End-to-end tests simulate real user behavior through the full app, which gives high confidence but is slower and more expensive to maintain.

### Example

```text
unit -> function behavior
integration -> component plus data flow
e2e -> browser user journey
```

### Common Follow-ups

- Which test type is cheapest to run?
- When should you prefer integration tests?
- Why are end-to-end tests slower?

### My Answer


### Interview Notes

- Test depth increases with scope.
- A balanced test strategy is usually best.
- More unit tests do not always mean better quality.

## What is Jest and what is it used for?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Jest is a JavaScript testing framework used for running tests, making assertions, mocking dependencies, and measuring coverage.

### Deep Explanation

Jest provides a complete testing experience with a test runner, assertion library, mocking utilities, and snapshot support. It is common in React projects because it integrates well with component testing and frontend tooling. Its built-in mocking makes it useful for isolating code under test.

### Example

```javascript
expect(sum(1, 2)).toBe(3);
```

### Common Follow-ups

- What is a mock function?
- What is snapshot testing?
- Why is Jest popular in frontend apps?

### My Answer


### Interview Notes

- Jest covers the full testing loop.
- It is widely used in JavaScript and React apps.
- Mocking and assertions are core features.

## What is React Testing Library?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

React Testing Library is a tool for testing React components the way users interact with them instead of testing implementation details.

### Deep Explanation

It encourages tests that query by text, role, label, and visible behavior rather than component internals or state. This makes tests more resilient to refactoring and closer to actual usage. The philosophy is to verify what the user sees and does, not how the component is built internally.

### Example

```javascript
screen.getByRole("button", { name: /save/i });
```

### Common Follow-ups

- Why is RTL preferred over shallow testing?
- What does testing behavior mean?
- How do accessibility queries help testing?

### My Answer


### Interview Notes

- Test user-facing behavior.
- Prefer accessible queries.
- Avoid overfocusing on internals.

## What should you test in a React component?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Test the component’s behavior, visible output, user interactions, and important edge cases.

### Deep Explanation

Good component tests verify that the right content appears, buttons trigger the correct actions, and conditional states render properly. You should also test error states, loading states, and accessibility where relevant. Avoid testing implementation details that may change during refactoring without affecting the user experience.

### Example

```javascript
expect(screen.getByText("Loading...")).toBeInTheDocument();
```

### Common Follow-ups

- Should you test private helper functions?
- How do you test loading and error states?
- What should not be tested in component tests?

### My Answer


### Interview Notes

- Focus on behavior and important states.
- Test what users can observe.
- Keep tests robust against refactors.

## What is mocking and when should you use it?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Mocking replaces a real dependency with a fake one so you can isolate the code under test.

### Deep Explanation

Mocks are useful when a dependency is slow, unreliable, hard to set up, or outside the scope of the test, such as network calls, timers, storage, or analytics. They let you control inputs and assert interactions. Overusing mocks can make tests brittle, so they should support the test goal rather than dominate it.

### Example

```javascript
jest.fn();
```

### Common Follow-ups

- What is the difference between mocks and stubs?
- When does mocking become overuse?
- Why mock network calls in tests?

### My Answer


### Interview Notes

- Mock external or slow dependencies.
- Keep tests focused on behavior.
- Avoid mocking what you really want to verify.

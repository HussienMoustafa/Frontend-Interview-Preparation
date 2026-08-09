## How would you structure a large React application?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

I would structure it by feature or domain, keep shared utilities small, separate UI from business logic, and use clear boundaries for data, state, and routing.

### Deep Explanation

Large React apps work best when the folder structure mirrors product domains rather than technical layers alone. Features should own their components, hooks, services, and tests when possible. Shared code should be truly reusable and kept lightweight so it does not become a dumping ground. The goal is to make navigation, ownership, and change impact obvious.

### Example

```text
src/
	features/
	components/
	hooks/
	services/
```

### Common Follow-ups

- Why structure by feature instead of by file type only?
- How do you avoid a shared folder becoming too large?
- Where should global state live?

### My Answer


### Interview Notes

- Prefer feature-based boundaries.
- Keep shared code small and intentional.
- Organize around how the product changes.

## How would you design a reusable component?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

A reusable component should have a clear responsibility, simple API, sensible defaults, and enough flexibility to cover real use cases without becoming too abstract.

### Deep Explanation

Good reusable components solve a repeated problem in a consistent way. They should be easy to understand, easy to compose, and hard to misuse. A clean API with well-typed props, support for customization through composition, and minimal hidden behavior usually works better than lots of special-case flags.

### Example

```tsx
<Button variant="primary" onClick={handleClick}>Save</Button>
```

### Common Follow-ups

- When does a component become too generic?
- Why is composition often better than configuration flags?
- How do you keep props manageable?

### My Answer


### Interview Notes

- Start with a real repeated use case.
- Keep the public API small and expressive.
- Reusability should not destroy clarity.

## How would you handle global state in a large application?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

I would keep state local when possible, lift shared state only as needed, use Context for stable cross-cutting data, and introduce a state manager when the app truly needs one.

### Deep Explanation

Not all state belongs in a global store. UI state is often best kept close to where it is used, while auth, theme, and app-wide configuration may belong in shared context. If many screens need to coordinate complex updates or cached server state, a dedicated store or data-fetching layer may be the right choice. The main goal is predictable ownership and minimal coupling.

### Example

```text
local UI state -> component
shared app state -> context/store
server state -> data fetching cache
```

### Common Follow-ups

- When is Context enough?
- What is the difference between UI state and server state?
- Why can global state become hard to maintain?

### My Answer


### Interview Notes

- Do not put everything into global state.
- Match the tool to the type of state.
- Keep ownership obvious.

## How would you optimize a slow frontend application?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

I would profile the app first, identify whether the problem is rendering, data fetching, JavaScript execution, or asset delivery, and then optimize the actual bottleneck.

### Deep Explanation

Performance work should start with measurement. Common fixes include reducing bundle size, splitting code, memoizing expensive renders, virtualizing long lists, caching API responses, compressing images, and avoiding unnecessary state updates. Often the largest gains come from removing work rather than making the same work slightly faster.

### Example

```tsx
<VirtualizedList items={items} />
```

### Common Follow-ups

- What tools help you profile frontend performance?
- Why is image optimization often overlooked?
- How do you know if a render is the real problem?

### My Answer


### Interview Notes

- Measure before changing code.
- Focus on the biggest bottleneck first.
- Simplifying work is often more effective than micro-optimizing.

## How would you design the frontend architecture for a large-scale application?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

I would design it around clear layers, feature boundaries, strong typing, predictable data flow, shared design primitives, and a scalable approach to routing, state, and data fetching.

### Deep Explanation

Large-scale frontend architecture should separate concerns without creating unnecessary ceremony. UI components should remain focused on presentation, feature modules should own business workflows, and data access should be centralized or standardized. The architecture should also support testing, performance, accessibility, and gradual evolution as product needs change.

### Example

```text
design system -> reusable UI
features -> business workflows
data layer -> API access and caching
```

### Common Follow-ups

- What belongs in a design system versus a feature?
- How do you keep the architecture flexible?
- How do you avoid overengineering?

### My Answer


### Interview Notes

- Optimize for change, not just today’s implementation.
- Keep layers small and meaningful.
- Use shared patterns to reduce accidental complexity.

## 1. Why use TypeScript instead of JavaScript?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

TypeScript adds static typing on top of JavaScript, which helps catch mistakes earlier and makes large codebases easier to maintain.

### Deep Explanation

TypeScript does not replace JavaScript runtime behavior; it adds compile-time checks, better tooling, and clearer contracts between parts of an application. It is especially useful when many people work in the same codebase, because types document intent and reduce accidental misuse of functions, objects, and APIs. It also improves autocomplete and refactoring support in editors.

### Example

```typescript
function add(a: number, b: number): number {
	return a + b;
}
```

### Common Follow-ups

- Does TypeScript run in the browser?
- What kinds of bugs does TypeScript catch?
- Is TypeScript fully optional at runtime?

### My Answer


### Interview Notes

- TypeScript is a development-time safety layer.
- It improves maintainability, tooling, and readability.
- It still compiles to plain JavaScript.

## 2. What is the difference between `interface` and `type`?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`interface` is best for describing object shapes and can be extended or merged. `type` is more flexible and can represent unions, intersections, primitives, tuples, and mapped types.

### Deep Explanation

Both can describe object structures, and in many cases they are interchangeable. `interface` supports declaration merging and is often preferred for public object contracts and class shapes. `type` is more powerful for composing complex types, especially unions and utility-style aliases. In practice, many teams use `interface` for objects and `type` for everything else.

### Example

```typescript
interface User {
	name: string;
}

type Status = "idle" | "loading" | "success";
```

### Common Follow-ups

- Can interfaces extend types?
- Can types be merged like interfaces?
- When should I choose one over the other?

### My Answer


### Interview Notes

- `interface` is great for object contracts.
- `type` is more expressive for composition.
- Team conventions matter more than strict rules.

## 3. What are union and intersection types?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Union types allow a value to be one of several types. Intersection types combine multiple types into one that has all of their properties.

### Deep Explanation

Unions are useful when a variable can legitimately hold different kinds of values, such as a result that may be `string` or `null`. Intersections are useful when you want to merge capabilities, such as combining a domain object with metadata. Unions usually require narrowing before you can safely use the value. Intersections produce a type that satisfies every member type at once.

### Example

```typescript
type Id = string | number;
type Employee = { name: string } & { id: number };
```

### Common Follow-ups

- How do you narrow a union type?
- What happens if union members have overlapping properties?
- When are intersections useful in practice?

### My Answer


### Interview Notes

- Unions mean one of many.
- Intersections mean all of many.
- Narrowing is often needed with unions.

## 4. What are generics?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Generics let you write reusable types and functions that work with different value types while preserving type safety.

### Deep Explanation

Instead of hard-coding a type, a generic introduces a type parameter such as `T`. This allows the compiler to infer or enforce the right type at the call site. Generics are common in arrays, API wrappers, hooks, utility functions, and reusable components. They reduce duplication while keeping strong typing.

### Example

```typescript
function identity<T>(value: T): T {
	return value;
}
```

### Common Follow-ups

- What does `T` stand for?
- How is type inference used with generics?
- Can generics have constraints?

### My Answer


### Interview Notes

- Generics make APIs flexible and safe.
- Type inference often removes the need to write explicit type arguments.
- Constraints can limit what `T` is allowed to be.

## 5. Explain `any`, `unknown`, and `never`.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`any` disables type checking, `unknown` is a safe top type that must be narrowed before use, and `never` represents values that should never exist.

### Deep Explanation

`any` is an escape hatch, but it removes most of TypeScript's benefits because anything can be done with it. `unknown` is safer: you can receive any value, but you must prove its type before using it. `never` is used for impossible code paths, such as functions that always throw or exhaustive checks that should never be reached.

### Example

```typescript
let value: unknown = "hello";
if (typeof value === "string") {
	console.log(value.toUpperCase());
}
```

### Common Follow-ups

- Why is `unknown` safer than `any`?
- When does TypeScript infer `never`?
- How is `never` useful in exhaustive checks?

### My Answer


### Interview Notes

- Prefer `unknown` over `any`.
- `never` often signals impossible branches.
- `any` should be used sparingly.

## 6. What is type narrowing?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Type narrowing is the process of reducing a broad type to a more specific one based on checks like `typeof`, `instanceof`, or property tests.

### Deep Explanation

When a value starts as a union, TypeScript needs help determining which member is currently in use. Narrowing tells the compiler more about the value through control flow, conditionals, and user-defined checks. This makes code safer because you can access only the properties that are valid for the refined type.

### Example

```typescript
function print(value: string | number) {
	if (typeof value === "string") {
		console.log(value.toUpperCase());
	} else {
		console.log(value.toFixed(2));
	}
}
```

### Common Follow-ups

- Which operators help with narrowing?
- How does control flow analysis work?
- How do custom type guards narrow types?

### My Answer


### Interview Notes

- Narrowing is essential when working with unions.
- TypeScript follows the control flow of your code.
- Good narrowing reduces runtime errors.

## 7. What are type guards?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Type guards are checks that help TypeScript narrow a value to a more specific type.

### Deep Explanation

Built-in guards include `typeof`, `instanceof`, and discriminant checks on object properties. You can also write custom type guard functions that return a type predicate like `value is User`. Type guards are especially useful when dealing with API responses, union types, or unknown input.

### Example

```typescript
function isString(value: unknown): value is string {
	return typeof value === "string";
}
```

### Common Follow-ups

- What is a user-defined type predicate?
- How is a type guard different from a normal boolean function?
- When would you use discriminated unions?

### My Answer


### Interview Notes

- Type guards improve safety with dynamic data.
- Custom guards are common in validation code.
- They work hand in hand with narrowing.

## 8. What is the difference between optional properties and nullable properties?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

An optional property may be missing entirely, while a nullable property exists but can explicitly be `null`.

### Deep Explanation

Optional properties are marked with `?`, which means the property might not be present on the object at all. Nullable properties are usually written as a union with `null`, which means the key exists but its value may be `null`. This distinction matters when modeling APIs and form state because absence and explicit emptiness are not always the same.

### Example

```typescript
type User = {
	middleName?: string;
	nickName: string | null;
};
```

### Common Follow-ups

- Is `undefined` the same as optional?
- When should I use `null` instead of `undefined`?
- How does strict null checking affect this?

### My Answer


### Interview Notes

- Optional means may be omitted.
- Nullable means may explicitly hold `null`.
- Be consistent with API and state modeling.

## 9. What are utility types such as `Partial`, `Pick`, `Omit`, and `Record`?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Utility types are built-in TypeScript helpers that transform existing types into new shapes.

### Deep Explanation

`Partial<T>` makes all properties optional, `Pick<T, K>` selects a subset of properties, `Omit<T, K>` removes selected properties, and `Record<K, T>` creates an object type with keys of one type and values of another. They are useful for shaping API payloads, component props, and derived data types without redefining everything manually.

### Example

```typescript
type User = { id: number; name: string; email: string };
type UserPreview = Pick<User, "id" | "name">;
```

### Common Follow-ups

- What does `Partial` do in forms or patches?
- How is `Record` different from an index signature?
- When is `Omit` cleaner than `Pick`?

### My Answer


### Interview Notes

- Utility types save time and reduce duplication.
- They are common in state and API layers.
- Learn the most common ones by name and behavior.

## 10. What is `readonly`?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

`readonly` prevents reassignment of a property or variable after it is initialized.

### Deep Explanation

It helps communicate intent and reduce accidental mutation. You can mark object properties and array/tuple types as readonly. Note that `readonly` in TypeScript is a compile-time restriction; it does not freeze values at runtime.

### Example

```typescript
type Point = {
	readonly x: number;
	readonly y: number;
};
```

### Common Follow-ups

- Is `readonly` the same as `Object.freeze`?
- Can arrays be readonly?
- Why is immutability useful?

### My Answer


### Interview Notes

- `readonly` improves safety and intent.
- It is enforced by TypeScript, not JavaScript.
- Immutable patterns are common in React.

## 11. What are enums and what alternatives can you use?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Enums define named constant sets. Common alternatives are union literal types and `as const` objects.

### Deep Explanation

Enums can be useful for representing fixed categories, but they add runtime output unless you use `const enum`, which has its own tradeoffs. Many teams prefer literal unions because they are lighter, easier to serialize, and more aligned with plain JavaScript. `as const` objects are another practical option when you want both values and types.

### Example

```typescript
type Status = "idle" | "loading" | "success";

const Status = {
	Idle: "idle",
	Loading: "loading",
	Success: "success"
} as const;
```

### Common Follow-ups

- When are enums worth using?
- What is the downside of numeric enums?
- Why do many TypeScript teams prefer unions?

### My Answer


### Interview Notes

- Literal unions are often the simplest option.
- Enums are more common in older codebases.
- Match the choice to your team's conventions.

## 12. How would you type a React component's props?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

You can type React props by defining an `interface` or `type` for the props object and using it in the component signature.

### Deep Explanation

Typing props makes component APIs explicit and catches missing or invalid values at compile time. You can use `interface` for object-shaped props or `type` if you need unions, intersections, or derived forms. For reusable components, typing children, callbacks, and optional props clearly helps prevent misuse and improves editor autocomplete.

### Example

```typescript
type ButtonProps = {
	label: string;
	onClick: () => void;
};
```

### Common Follow-ups

- Should I use `type` or `interface` for props?
- How do you type `children`?
- How do you type optional callback props?

### My Answer


### Interview Notes

- Keep props types close to the component.
- Prefer clear names like `ButtonProps`.
- Use strict typing for callbacks and required props.

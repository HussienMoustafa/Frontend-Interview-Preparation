## What is the difference between React and React Native?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

React builds web UIs, while React Native builds mobile apps using native platform components.

### Deep Explanation

React targets the browser and renders to the DOM. React Native uses the same component model and JavaScript patterns, but its components map to native iOS and Android views. That means you can share logic and architecture while still shipping platform-specific mobile experiences.

### Example

```jsx
<View>
	<Text>Hello</Text>
</View>
```

### Common Follow-ups

- Do React and React Native share the same hooks?
- What do React Native components render to?
- Can you reuse web code in React Native?

### My Answer


### Interview Notes

- React Native is not React for the web.
- It uses native rendering primitives.
- Business logic can often be shared.

## How does React Native communicate with native platforms?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

React Native communicates with native code through a bridge or the newer native architecture, depending on the version and setup.

### Deep Explanation

JavaScript drives the app logic, while native modules handle platform-specific work like sensors, storage, or advanced UI features. Historically, communication happened over a bridge that serialized data between the JavaScript and native sides. Newer architectures reduce overhead and improve performance by using a more direct and optimized model.

### Example

```jsx
NativeModules.SomeModule.doThing();
```

### Common Follow-ups

- What is the bridge?
- Why can bridge communication be a bottleneck?
- What improves in the new architecture?

### My Answer


### Interview Notes

- Native modules expose platform capabilities.
- Cross-thread communication has performance cost.
- Architecture changes aim to reduce that overhead.

## What is the difference between React Native components and native components?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

React Native components are cross-platform abstractions, while native components are platform-specific UI elements implemented in iOS or Android.

### Deep Explanation

Components like `View`, `Text`, and `Pressable` are portable building blocks that React Native maps to native views. Native components are used when a platform has a specialized feature or a custom implementation is needed. Most apps should use React Native components first and only drop into native code when necessary.

### Example

```jsx
<Pressable onPress={onPress}>
	<Text>Tap</Text>
</Pressable>
```

### Common Follow-ups

- When would you build a native component?
- What is the benefit of cross-platform components?
- Can React Native expose custom native UI?

### My Answer


### Interview Notes

- Use React Native components for portability.
- Native components are for platform-specific needs.
- Keep the native surface area small when possible.

## Explain the React Native rendering architecture at a high level.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

React Native renders UI by converting React component trees into native views through its rendering pipeline.

### Deep Explanation

At a high level, JavaScript decides what the UI should look like, React Native computes changes, and native code renders the result on the device. The architecture includes JavaScript execution, layout calculation, and native view updates. Newer React Native versions improve this flow with better synchronization and less overhead between the JavaScript and native sides.

### Example

```jsx
<View style={{ flex: 1 }} />
```

### Common Follow-ups

- What is the role of the JavaScript thread?
- How does layout work in React Native?
- Why is the architecture important for performance?

### My Answer


### Interview Notes

- React Native translates UI descriptions into native rendering.
- Layout and rendering are separate concerns.
- Architecture directly affects responsiveness.

## How would you optimize React Native performance?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Optimize by reducing unnecessary renders, minimizing bridge traffic, using efficient lists, and avoiding heavy work on the JS thread.

### Deep Explanation

Start by measuring bottlenecks instead of guessing. Common fixes include memoizing expensive components, using `FlatList` correctly, keeping state local, reducing large object creation, and moving expensive native work off the critical path. You should also watch image sizes, animation performance, and repeated context updates.

### Example

```jsx
<FlatList data={items} renderItem={renderItem} keyExtractor={(item) => item.id} />
```

### Common Follow-ups

- Why is `FlatList` preferred over `ScrollView` for large lists?
- How do you profile a slow screen?
- What causes JS thread blocking?

### My Answer


### Interview Notes

- Measure first, optimize second.
- Use virtualization for large lists.
- Keep the JS thread free for user interactions.

## What causes unnecessary re-renders in React Native?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Unnecessary re-renders are caused by changing props, unstable callback references, broad context updates, and poorly scoped state.

### Deep Explanation

React Native follows React's rendering model, so the same render triggers apply. If parent state changes frequently, child components can re-render even when their visible output does not change. Large lists, inline object props, and new function instances can all contribute to extra work and dropped frames.

### Example

```jsx
<Child onPress={() => doThing()} />
```

### Common Follow-ups

- How do you stabilize props?
- Why does context sometimes hurt performance?
- How do you know a re-render is unnecessary?

### My Answer


### Interview Notes

- Treat React Native as React with platform constraints.
- Inline objects and functions can be expensive.
- Scope state carefully.

## How does React Navigation work?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

React Navigation manages screen transitions and navigation state using navigators, routes, and params.

### Deep Explanation

It provides stack, tab, drawer, and nested navigation patterns while keeping the current navigation state in sync with the UI. Screens are registered inside navigators, and navigation actions update the state tree. The library also supports deep linking, screen options, and nested navigators for complex apps.

### Example

```jsx
navigation.navigate("Details", { id: 1 });
```

### Common Follow-ups

- What is a nested navigator?
- How are route params passed?
- Why is navigation state separate from component state?

### My Answer


### Interview Notes

- Navigation is state-driven.
- Different navigator types solve different flows.
- Keep route params small and serializable.

## How do you persist data in React Native?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

You persist data using storage options such as AsyncStorage, secure storage, SQLite, or backend sync depending on the data type and sensitivity.

### Deep Explanation

Simple preferences and cached UI state can often live in local storage. Sensitive data like tokens should use secure storage backed by the operating system. For structured offline data or larger datasets, a database solution may be better. The right choice depends on size, sensitivity, and sync needs.

### Example

```jsx
await AsyncStorage.setItem("theme", "dark");
```

### Common Follow-ups

- What should not be stored in plain local storage?
- When do you use a database instead?
- How do you hydrate state on app start?

### My Answer


### Interview Notes

- Match storage to the data sensitivity.
- Secure storage is for secrets.
- Load persisted data early in app startup.

## AsyncStorage vs secure storage — when would you use each?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Use AsyncStorage for non-sensitive preferences and cached data, and secure storage for secrets like tokens and credentials.

### Deep Explanation

AsyncStorage is convenient but not designed for protecting sensitive information. Secure storage uses platform security features such as Keychain or Keystore to better protect secrets. A good rule is to treat anything that grants access to a user account as sensitive and keep it out of plain storage.

### Example

```jsx
await SecureStore.setItemAsync("token", token);
```

### Common Follow-ups

- Is AsyncStorage encrypted?
- Why are auth tokens sensitive?
- What data is safe in plain storage?

### My Answer


### Interview Notes

- Use secure storage for secrets.
- Use AsyncStorage for low-risk preferences.
- Never assume plain storage is private.

## How do you handle deep linking?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Deep linking routes a URL into a specific screen inside the app.

### Deep Explanation

You configure the app to recognize URL patterns and map them to screens and parameters. Deep links are useful for marketing links, notifications, and sharing specific content. Handling them well means supporting both cold starts and already-open apps.

### Example

```jsx
myapp://product/42
```

### Common Follow-ups

- What is universal linking?
- How do you parse route params from a URL?
- What happens when the app is already open?

### My Answer


### Interview Notes

- Deep links connect external URLs to internal screens.
- Support both app launch and in-app navigation.
- Test links on both platforms.

## How do you handle permissions in React Native?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

You request permissions through platform APIs or libraries and handle the user’s response before accessing protected features.

### Deep Explanation

Camera, location, microphone, and notifications all require permission handling. The app should explain why the permission is needed, request it at the right time, and handle denial gracefully. Good permission flows avoid surprising users and reduce rejection risk.

### Example

```jsx
const result = await requestCameraPermission();
```

### Common Follow-ups

- When should you ask for permission?
- What is the difference between denied and blocked?
- How do you handle fallback UI?

### My Answer


### Interview Notes

- Ask only when the user needs the feature.
- Handle denial gracefully.
- Platform-specific APIs vary by permission type.

## How would you debug a React Native performance issue?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Start by profiling the app, identifying slow renders or blocked frames, and then isolate whether the issue is in JavaScript, layout, images, or native work.

### Deep Explanation

Look for repeated renders, expensive list rows, large images, unnecessary state updates, and slow interactions on the JS thread. Use React DevTools, performance monitors, logging, and platform profiling tools to narrow the problem. Once you know whether the bottleneck is rendering, computation, or native bridging, the fix becomes much clearer.

### Example

```jsx
console.log("render", item.id);
```

### Common Follow-ups

- What tools help profile React Native?
- How do you tell JS thread problems from native ones?
- What are the most common causes of lag?

### My Answer


### Interview Notes

- Measure the bottleneck before fixing it.
- Separate UI, JS, and native causes.
- Large lists and heavy images are common culprits.

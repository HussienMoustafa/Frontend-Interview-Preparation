## What is Next.js and why use it instead of plain React?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Next.js is a React framework that adds routing, server rendering, data fetching patterns, and production features out of the box.

### Deep Explanation

Plain React gives you the component layer, but you still need to assemble routing, bundling, SSR, code splitting, and deployment patterns yourself. Next.js provides a higher-level framework for building full web apps with server-side capabilities, better performance options, and integrated conventions. It is a strong choice when you want React plus application infrastructure.

### Example

```tsx
export default function Page() {
	return <h1>Hello Next.js</h1>;
}
```

### Common Follow-ups

- Is Next.js a replacement for React?
- What problems does it solve beyond routing?
- When would plain React still be enough?

### My Answer


### Interview Notes

- Next.js is React plus app framework features.
- It simplifies production-ready web development.
- It supports both server and client rendering.

## Explain SSR, CSR, SSG, and ISR.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

SSR renders pages on the server per request, CSR renders in the browser, SSG prebuilds pages at build time, and ISR updates static pages after deployment on a schedule or demand.

### Deep Explanation

SSR is useful for dynamic content that needs fresh HTML on each request. CSR shifts most rendering to the browser after JavaScript loads. SSG is ideal for content that changes rarely and benefits from fast delivery. ISR sits between SSG and SSR by letting static pages regenerate periodically without a full rebuild.

### Example

```tsx
export async function getServerSideProps() {
	return { props: {} };
}
```

### Common Follow-ups

- Which rendering mode is fastest?
- When is SSR better than SSG?
- How does ISR improve scalability?

### My Answer


### Interview Notes

- Choose rendering mode based on freshness and performance needs.
- CSR is not always the best default.
- ISR helps balance static speed with content updates.

## What is the difference between Server Components and Client Components?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Server Components render on the server and never ship their code to the browser, while Client Components run in the browser and can use client-only features like state and effects.

### Deep Explanation

Server Components are great for data fetching, secure access to backend resources, and reducing client bundle size. Client Components are needed for interactivity, browser APIs, and hooks like `useState` and `useEffect`. In the App Router, you can mix both to keep most of the app server-rendered while isolating interactive parts on the client.

### Example

```tsx
"use client";
```

### Common Follow-ups

- Why do Server Components reduce bundle size?
- What cannot be used in a Server Component?
- When do you need `"use client"`?

### My Answer


### Interview Notes

- Server Components stay on the server.
- Client Components handle interactivity.
- Use the client boundary only where needed.

## When would you use `"use client"`?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

You use `"use client"` when a component needs client-side interactivity, browser APIs, or React hooks that only run in the browser.

### Deep Explanation

Without the directive, components in the App Router are Server Components by default. If a component uses state, effects, event handlers, or browser-only objects like `window`, it must be a Client Component. Keeping the client boundary as small as possible helps reduce shipped JavaScript.

### Example

```tsx
"use client";

import { useState } from "react";
```

### Common Follow-ups

- Does `"use client"` apply to child components?
- Why not make everything a client component?
- What is the performance tradeoff?

### My Answer


### Interview Notes

- Use it only for interactive components.
- It marks the client/server boundary.
- Smaller client bundles are usually better.

## Explain Next.js routing.

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Next.js routing is file-system based, where folders and files define routes automatically.

### Deep Explanation

In the App Router, route segments are created from the folder structure, and special files like `page.tsx`, `layout.tsx`, and `loading.tsx` define behavior for each route. This removes most manual route configuration and makes route structure easier to see in the filesystem. Nested routes, dynamic segments, and route groups help organize large applications cleanly.

### Example

```tsx
app/products/[id]/page.tsx
```

### Common Follow-ups

- What are dynamic routes?
- What is a layout in Next.js?
- How do route groups work?

### My Answer


### Interview Notes

- Routing is convention-based.
- The folder structure is part of the app design.
- Dynamic segments use bracket syntax.

## How does Next.js handle data fetching?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Next.js supports data fetching on the server, in Server Components, in route handlers, and on the client depending on the use case.

### Deep Explanation

In modern Next.js, server-side data fetching is often done directly in async Server Components or server-only utilities. For interactive or rapidly changing data, client fetching still makes sense. The right strategy depends on freshness, caching, SEO, and whether the data is needed before the page can render.

### Example

```tsx
const data = await fetch("https://api.example.com/posts");
```

### Common Follow-ups

- When should data be fetched on the server?
- What role do route handlers play?
- How does caching affect data fetching?

### My Answer


### Interview Notes

- Server fetching is common in the App Router.
- Choose the fetching location based on user experience.
- Caching strategy matters a lot.

## What are the benefits of server-side rendering?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Server-side rendering can improve initial load experience, SEO, and content availability before JavaScript finishes loading.

### Deep Explanation

With SSR, the server returns HTML that already contains useful content, which helps search engines and users see meaningful output sooner. This is valuable for public pages, marketing sites, and content-heavy applications. SSR can also improve perceived performance, though it adds server work and can increase complexity.

### Example

```tsx
export default async function Page() {
	return <div>Rendered on the server</div>;
}
```

### Common Follow-ups

- Is SSR always better for SEO?
- What are the tradeoffs of SSR?
- How does SSR differ from hydration?

### My Answer


### Interview Notes

- SSR improves first response HTML.
- It is useful for SEO and dynamic content.
- It comes with server complexity.

## How would you optimize a Next.js application?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Optimize by reducing client JavaScript, using the right rendering mode, caching aggressively where appropriate, and loading only what is needed.

### Deep Explanation

Start with bundle size, routing strategy, and data fetching placement. Use Server Components where possible, split heavy client code, optimize images, avoid unnecessary client state, and leverage caching and static generation for stable content. Measure the real bottleneck before changing architecture.

### Example

```tsx
import Image from "next/image";
```

### Common Follow-ups

- How do Server Components help performance?
- What role does image optimization play?
- How do you reduce client bundle size?

### My Answer


### Interview Notes

- Keep the client bundle small.
- Choose the right rendering strategy per page.
- Use caching, images, and code splitting wisely.

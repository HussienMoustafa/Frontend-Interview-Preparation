## What happens when you enter a URL into the browser?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

The browser resolves the domain, opens a connection, sends an HTTP request, receives a response, and then parses and renders the page.

### Deep Explanation

First the browser checks caches and performs DNS resolution if needed. It then establishes a network connection, negotiates security for HTTPS, and sends the request. The server responds with HTML, which the browser parses into the DOM while fetching linked assets like CSS, JavaScript, and images. After that, layout, paint, and script execution produce the final page.

### Example

```text
URL -> DNS -> connection -> request -> response -> parse -> render
```

### Common Follow-ups

- What is DNS?
- What is the difference between parsing and rendering?
- What happens after the HTML response arrives?

### My Answer


### Interview Notes

- The browser does much more than just open a page.
- Network, parsing, layout, and rendering all matter.
- Caching can short-circuit parts of the process.

## Explain HTTP methods: GET, POST, PUT, PATCH, DELETE.

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

GET reads data, POST creates data, PUT replaces a resource, PATCH partially updates a resource, and DELETE removes a resource.

### Deep Explanation

These methods describe the intent of a request. GET should be safe and idempotent for reading. POST is typically used for creating or triggering server-side actions. PUT usually replaces the entire resource, PATCH updates part of it, and DELETE removes it.

### Example

```http
GET /users/1
POST /users
PATCH /users/1
DELETE /users/1
```

### Common Follow-ups

- What does idempotent mean?
- When should you use PATCH instead of PUT?
- Is POST idempotent?

### My Answer


### Interview Notes

- Match the method to the intent.
- GET should not mutate server state.
- PUT usually replaces, PATCH usually modifies.

## What is the difference between HTTP and HTTPS?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

HTTPS is HTTP protected by TLS, which encrypts data and verifies the server's identity.

### Deep Explanation

HTTP sends data in plain text, which can be intercepted or modified in transit. HTTPS adds encryption, integrity, and authentication via TLS. In modern web development, HTTPS is effectively the default because it protects user data and is required for many browser features.

### Example

```text
https://example.com
```

### Common Follow-ups

- What does TLS do?
- Why is HTTPS important for cookies and auth?
- Can HTTP ever be safe?

### My Answer


### Interview Notes

- HTTPS is HTTP over TLS.
- It protects confidentiality and integrity.
- Production sites should use HTTPS.

## What are HTTP status codes and the important ones you should know?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

HTTP status codes tell the client whether a request succeeded, failed, or needs further action.

### Deep Explanation

The main classes are informational, success, redirection, client error, and server error. Important examples include `200` success, `201` created, `204` no content, `301` moved permanently, `400` bad request, `401` unauthorized, `403` forbidden, `404` not found, `500` server error, and `503` service unavailable. Knowing the common codes helps with debugging APIs and understanding browser behavior.

### Example

```http
200 OK
404 Not Found
500 Internal Server Error
```

### Common Follow-ups

- What is the difference between `401` and `403`?
- When do you return `201`?
- What does `204` mean?

### My Answer


### Interview Notes

- Learn the common codes by heart.
- Status codes communicate request outcomes.
- `401` and `403` are a common interview trap.

## What is CORS and why does it exist?

**Priority:** ⭐⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

CORS is a browser security mechanism that controls whether a page can make requests to a different origin.

### Deep Explanation

Browsers block many cross-origin requests by default to protect users from malicious sites reading sensitive data from other domains. Servers can opt in to safe cross-origin access by sending the right CORS headers. This is not a server-to-server restriction; it is a browser-enforced policy.

### Example

```http
Access-Control-Allow-Origin: https://example.com
```

### Common Follow-ups

- What is an origin?
- What is a preflight request?
- Why does CORS exist only in browsers?

### My Answer


### Interview Notes

- CORS is browser-enforced.
- It protects against unsafe cross-origin reads.
- Correct headers are required on the server.

## What is the difference between cookies, localStorage, and sessionStorage?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Cookies can be sent with HTTP requests, localStorage persists until cleared, and sessionStorage lasts only for the current tab session.

### Deep Explanation

Cookies are often used for authentication, server communication, and session tracking. localStorage is simple persistent client storage for non-sensitive data like preferences, but it is accessible to JavaScript. sessionStorage is similar but is cleared when the tab closes. Each has different limits, lifetimes, and security considerations.

### Example

```javascript
localStorage.setItem("theme", "dark");
```

### Common Follow-ups

- Are cookies automatically sent with requests?
- Why is localStorage not good for secrets?
- When does sessionStorage get cleared?

### My Answer


### Interview Notes

- Cookies can be HTTP-only and secure.
- localStorage survives browser restarts.
- sessionStorage is tab-scoped.

## What is caching and how can it improve web performance?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Caching stores previously fetched data or assets so future requests can be served faster or avoided entirely.

### Deep Explanation

Browsers, CDNs, servers, and application code can all cache data. Good caching reduces latency, network traffic, and server load. Static assets, API responses, and rendered pages can all benefit from the right cache policy. The tradeoff is keeping cached content fresh.

### Example

```http
Cache-Control: public, max-age=3600
```

### Common Follow-ups

- What is the difference between browser cache and CDN cache?
- How do you keep cached data fresh?
- What headers control caching?

### My Answer


### Interview Notes

- Caching improves speed and scalability.
- Freshness vs performance is the main tradeoff.
- Good cache headers matter.

## What is the difference between authentication and authorization?

**Priority:** ⭐⭐⭐⭐  
**Status:** 🔴 Not learned

### Short Answer

Authentication verifies who you are, while authorization determines what you are allowed to do.

### Deep Explanation

Logging in is authentication because the system confirms your identity. Access control is authorization because the system checks your permissions for a specific resource or action. Good systems separate these concerns so identity and permissions can evolve independently.

### Example

```text
Login -> authenticate
Access admin page -> authorize
```

### Common Follow-ups

- Which comes first?
- What is a session or token used for?
- Why is authorization not the same as login?

### My Answer


### Interview Notes

- Authentication is identity.
- Authorization is permission.
- Both are required for secure apps.

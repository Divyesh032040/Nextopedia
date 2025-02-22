# Next.js Routing Overview

## 🚀 Introduction to Next.js Routing
Next.js uses **file-based routing**, where routes are automatically generated based on the folder and file structure inside the `app/` directory. Unlike React Router, there is no need to manually define routes.

### ✅ Key Features:
- **Automatic Route Generation**
- **Supports Static & Dynamic Routes**
- **Built-in API Routes**
- **Middleware for Request Handling**
- **Optimized for Server-Side & Client-Side Navigation**

---

## 🛠 Types of Routing in Next.js
### 1️⃣ **Static Routing (SR)**
- Simple pages where the route matches the file path.
- Example:
  ```
  📂 app
  ┣ 📜 about/page.tsx → `/about`
  ┣ 📜 contact/page.tsx → `/contact`
  ```

### 2️⃣ **Dynamic Routing (DR)**
- Routes that change dynamically based on parameters.
- Example:
  ```
  📂 app
  ┣ 📂 blog
  ┃ ┣ 📜 [id]/page.tsx → `/blog/1`, `/blog/2`
  ```

### 3️⃣ **Catch-All Routing (CAR)**
- Handles multiple segments in a single route.
- Example:
  ```
  📂 app
  ┣ 📂 docs
  ┃ ┣ 📜 [...slug]/page.tsx → `/docs/setup/install` or `/docs/api`
  ```

### 4️⃣ **Nested Routing (NR)**
- Organizes sections inside a parent folder.
- Example:
  ```
  📂 app
  ┣ 📂 dashboard
  ┃ ┣ 📜 page.tsx → `/dashboard`
  ┃ ┣ 📂 settings
  ┃ ┃ ┗ 📜 page.tsx → `/dashboard/settings`
  ```

### 5️⃣ **API Routing (AR)**
- Built-in API endpoints without needing a separate backend.
- Example:
  ```
  📂 app
  ┣ 📂 api
  ┃ ┣ 📂 auth
  ┃ ┃ ┗ 📜 route.ts → `/api/auth`
  ```

### 6️⃣ **Middleware Routing (MR)**
- Controls access before a request reaches a page.
- Example: Protecting `/dashboard` for logged-in users.
  ```ts
  import { NextResponse } from "next/server";

  export function middleware(req) {
    const isLoggedIn = req.cookies.get("token");
    if (!isLoggedIn && req.nextUrl.pathname.startsWith("/dashboard")) {
      return NextResponse.redirect(new URL("/login", req.url));
    }
    return NextResponse.next();
  }
  ```

### 7️⃣ **Parallel Routing (PR)**
- Renders multiple independent sections inside one layout.
- Example:
  ```
  📂 app
  ┣ 📂 dashboard
  ┃ ┣ 📂 @analytics
  ┃ ┃ ┗ 📜 page.tsx → `/dashboard` (Analytics section)
  ┃ ┣ 📂 @notifications
  ┃ ┃ ┗ 📜 page.tsx → `/dashboard` (Notifications section)
  ```

---

## 🔥 Next.js Routing vs. React Router
| Feature | Next.js (File-Based Routing) | React Router |
|---------|------------------------------|--------------|
| Route Definition | **Automatic** (files & folders) | **Manual** (`<Route path>` definitions) |
| Page Loading | **Server-side, client-side, hybrid** | **Always client-side** |
| Nested Routes | **Folders (`app/dashboard/page.tsx`)** | **`<Route>` components** |
| API Routes | **Built-in (`app/api/route.ts`)** | ❌ Not available (needs Express.js) |
| Middleware | **Built-in (`middleware.ts`)** | ❌ Not available |

---

## 🎯 How to Explain Next.js Routing in One Line?
> "Next.js uses **file-based routing**, where routes are automatically generated from the `app/` directory, supporting **static, dynamic, nested, API, and middleware-based routing**, and it optimizes loading by handling **server-side, client-side, and hybrid navigation** seamlessly."

🚀 Now you're ready to confidently talk about Next.js routing! 💡

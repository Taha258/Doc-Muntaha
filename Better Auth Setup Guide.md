# Better Auth with Next.js + Express.js - Complete Setup Guide

## 📋 Table of Contents
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Backend Setup (Express.js)](#backend-setup-expressjs)
- [Frontend Setup (Next.js)](#frontend-setup-nextjs)
- [Testing](#testing)
- [Common Issues](#common-issues)

---

## 🏗️ Project Structure

```
main-project/
├── frontend/          # Next.js application
│   ├── app/
│   ├── lib/
│   ├── .env.local
│   └── package.json
│
└── backend/           # Express.js server
    ├── src/
    │   ├── index.js
    │   └── auth.js
    ├── .env
    └── package.json
```

---

## ✅ Prerequisites

1. **Node.js** installed (v18 or higher)
2. **Neon Database** account aur database created
3. **Neon Connection String** ready (example: `postgresql://username:password@ep-xxx.us-east-2.aws.neon.tech/database`)

---

## 🔧 Backend Setup (Express.js)

### Step 1: Backend Folder Mein Jao

```bash
cd backend
```

### Step 2: Node Project Initialize Karo

```bash
npm init -y
```

**Kya hota hai:** `package.json` file ban jati hai jo project dependencies track karti hai.

---

### Step 3: Dependencies Install Karo

```bash
npm install express better-auth pg dotenv cors drizzle-orm
```

**Packages ka kaam:**
- **express** - Backend server framework
- **better-auth** - Authentication library
- **pg** - PostgreSQL database client (Neon ke liye)
- **dotenv** - Environment variables ko load karta hai
- **cors** - Frontend se backend ko requests allow karta hai
- **drizzle-orm** - Database ORM

---

### Step 4: Development Dependencies Install Karo

```bash
npm install -D nodemon
```

**Kya hota hai:** `nodemon` file changes detect karke server auto-restart karta hai.

---

### Step 5: Folder Structure Banana

```bash
mkdir src
```

**Kya hota hai:** `src` folder ban jayega jahan code files hongi.

---

### Step 6: Environment Variables (.env file)

Backend folder mein `.env` file banao:

```env
DATABASE_URL=postgresql://username:password@ep-xxx.us-east-2.aws.neon.tech/database
BETTER_AUTH_SECRET=apni-32-character-secret-key-yahan-paste-karo
BETTER_AUTH_URL=http://localhost:5000
PORT=5000
```

**Variables ka matlab:**
- **DATABASE_URL** - Neon database connection string
- **BETTER_AUTH_SECRET** - Data encryption ke liye secret key (32+ characters)
- **BETTER_AUTH_URL** - Backend ka URL
- **PORT** - Server kis port par run hoga

**Secret key generate karne ke liye:**
```bash
openssl rand -base64 32
```

---

### Step 7: Auth Configuration File (`src/auth.js`)

`src/auth.js` file banao:

```javascript
const { betterAuth } = require("better-auth");
const { drizzleAdapter } = require("better-auth/adapters/drizzle");
const { drizzle } = require("drizzle-orm/node-postgres");
const { Pool } = require("pg");

// Database connection setup
const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
});

const db = drizzle(pool);

// Better Auth configuration
const auth = betterAuth({
  database: drizzleAdapter(db, {
    provider: "pg", // PostgreSQL use kar rahe hain
  }),
  emailAndPassword: {
    enabled: true, // Email/password authentication enable
  },
  trustedOrigins: ["http://localhost:3000"], // Frontend URL (CORS ke liye)
});

module.exports = { auth };
```

**Code ka matlab:**
- **Pool** - Database connection pool banata hai (multiple requests efficiently handle karta hai)
- **drizzle(pool)** - Drizzle ORM instance
- **betterAuth()** - Auth system setup
- **trustedOrigins** - Konse URLs se requests accept karni hain

---

### Step 8: Main Server File (`src/index.js`)

`src/index.js` file banao:

```javascript
require("dotenv").config(); // .env file ko load karta hai
const express = require("express");
const cors = require("cors");
const { auth } = require("./auth");

const app = express();
const PORT = process.env.PORT || 5000;

// JSON body parser (IMPORTANT - ye add karo)
app.use(express.json());

// CORS Middleware - Frontend se requests allow karta hai
app.use(cors({
  origin: "http://localhost:3000", // Frontend URL
  credentials: true, // Cookies allow karta hai
}));

// Better Auth Handler - Sab auth routes handle karega ✅
// Example: /api/auth/sign-in, /api/auth/sign-up, /api/auth/sign-out
app.use("/api/auth", auth.handler);

// Health check route
app.get("/", (req, res) => {
  res.json({ message: "Backend is running!" });
});

// Server start
app.listen(PORT, () => {
  console.log(`🚀 Backend server running on http://localhost:${PORT}`);
});
```

**Code ka matlab:**
- **dotenv.config()** - Environment variables load karta hai
- **cors()** - Cross-Origin requests allow karta hai
- **app.all("/api/auth/*")** - Sab HTTP methods (GET, POST, etc.) handle karta hai
- **auth.handler()** - Better Auth ke saare endpoints handle karta hai

---

### Step 9: Package.json Scripts Add Karo

`package.json` file mein `"scripts"` section update karo:

```json
{
  "scripts": {
    "start": "node src/index.js",
    "dev": "nodemon src/index.js"
  }
}
```

**Scripts ka matlab:**
- **start** - Production mode mein server run karta hai
- **dev** - Development mode (auto-restart with nodemon)

---

### Step 10: Database Tables Banana

Better Auth ko kuch tables chahiye (user, session, account, verification).

```bash
npx @better-auth/cli migrate
```

**Kya hota hai:** 
- Better Auth CLI Neon database mein zaroori tables bana dega
- Tables automatically sahi structure ke saath ban jayengi

---

### Step 11: Backend Server Run Karo

```bash
npm run dev
```

**Expected Output:**
```
🚀 Backend server running on http://localhost:5000
```

Backend ready hai! ✅

---

## ⚛️ Frontend Setup (Next.js)

### Step 1: Frontend Folder Mein Jao

```bash
cd ../frontend
```

---

### Step 2: Dependencies Install Karo

```bash
npm install better-auth
```

**Kya hota hai:** Better Auth ka client-side library install hota hai.

---

### Step 3: Environment Variables (.env.local file)

Frontend folder mein `.env.local` file banao:

```env
NEXT_PUBLIC_API_URL=http://localhost:5000
```

**Variable ka matlab:**
- **NEXT_PUBLIC_API_URL** - Backend ka URL (frontend se API calls ke liye)

---

### Step 4: Auth Client Setup (`lib/auth-client.js` ya `lib/auth-client.ts`)

`lib/auth-client.js` file banao:

```javascript
import { createAuthClient } from "better-auth/react";

export const authClient = createAuthClient({
  baseURL: process.env.NEXT_PUBLIC_API_URL || "http://localhost:5000",
});

// Export useful functions
export const { signIn, signUp, signOut, useSession } = authClient;
```

**Code ka matlab:**
- **createAuthClient()** - Frontend auth client banata hai
- **baseURL** - Backend ka URL jahan auth API chal rahi hai
- **Export functions** - Components mein directly use kar sakte ho

---

### Step 5: Login/Signup Component Example

Example component (`app/login/page.jsx`):

```javascript
"use client";

import { useState } from "react";
import { signIn, signUp, useSession } from "@/lib/auth-client";

export default function LoginPage() {
  const { data: session, isPending } = useSession();
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [name, setName] = useState("");
  const [isSignUp, setIsSignUp] = useState(false);

  const handleAuth = async (e) => {
    e.preventDefault();
    
    try {
      if (isSignUp) {
        await signUp.email({
          email,
          password,
          name,
        });
        alert("Account created successfully!");
      } else {
        await signIn.email({
          email,
          password,
        });
        alert("Logged in successfully!");
      }
    } catch (error) {
      alert("Error: " + error.message);
    }
  };

  if (isPending) {
    return <div>Loading...</div>;
  }

  if (session) {
    return (
      <div className="p-8">
        <h1 className="text-2xl font-bold">Welcome, {session.user.name}!</h1>
        <p>Email: {session.user.email}</p>
        <button 
          onClick={() => authClient.signOut()}
          className="mt-4 px-4 py-2 bg-red-500 text-white rounded"
        >
          Logout
        </button>
      </div>
    );
  }

  return (
    <div className="min-h-screen flex items-center justify-center bg-gray-100">
      <div className="bg-white p-8 rounded-lg shadow-md w-96">
        <h1 className="text-2xl font-bold mb-6">
          {isSignUp ? "Sign Up" : "Login"}
        </h1>
        
        <form onSubmit={handleAuth} className="space-y-4">
          {isSignUp && (
            <input
              type="text"
              placeholder="Name"
              value={name}
              onChange={(e) => setName(e.target.value)}
              className="w-full px-4 py-2 border rounded"
              required
            />
          )}
          
          <input
            type="email"
            placeholder="Email"
            value={email}
            onChange={(e) => setEmail(e.target.value)}
            className="w-full px-4 py-2 border rounded"
            required
          />
          
          <input
            type="password"
            placeholder="Password"
            value={password}
            onChange={(e) => setPassword(e.target.value)}
            className="w-full px-4 py-2 border rounded"
            required
          />
          
          <button
            type="submit"
            className="w-full bg-blue-500 text-white py-2 rounded hover:bg-blue-600"
          >
            {isSignUp ? "Sign Up" : "Login"}
          </button>
        </form>
        
        <button
          onClick={() => setIsSignUp(!isSignUp)}
          className="mt-4 text-blue-500 hover:underline"
        >
          {isSignUp ? "Already have an account? Login" : "Need an account? Sign Up"}
        </button>
      </div>
    </div>
  );
}
```

**Code ka matlab:**
- **useSession()** - Current user ka data fetch karta hai
- **signUp.email()** - Naya account banata hai
- **signIn.email()** - Existing user ko login karta hai
- **signOut()** - User ko logout karta hai

---

### Step 6: Frontend Run Karo

```bash
npm run dev
```

**Frontend ready hai!** ✅

Visit: `http://localhost:3000/login`

---

## 🧪 Testing

### Test Backend:

1. Browser mein jao: `http://localhost:5000`
2. Response: `{"message": "Backend is running!"}`

### Test Authentication:

1. Frontend open karo: `http://localhost:3000/login`
2. Sign up karo (name, email, password)
3. Login karo
4. Session check karo (user details dikhni chahiye)

---

## 🐛 Common Issues

### Issue 1: CORS Error
**Error:** `Access to fetch blocked by CORS policy`

**Solution:** Backend ke `src/index.js` mein check karo:
```javascript
app.use(cors({
  origin: "http://localhost:3000", // Sahi URL hai?
  credentials: true,
}));
```

---

### Issue 2: Database Connection Error
**Error:** `Connection refused` ya `Invalid connection string`

**Solution:** 
1. `.env` file mein `DATABASE_URL` check karo
2. Neon dashboard mein connection string verify karo
3. Database running hai?

---

### Issue 3: Tables Nahi Ban Rahi
**Error:** `relation "user" does not exist`

**Solution:**
```bash
cd backend
npx @better-auth/cli migrate
```

---

### Issue 4: Session Nahi Mil Raha
**Error:** `useSession()` returns null

**Solution:**
1. Backend running hai? (`http://localhost:5000`)
2. Frontend ka `NEXT_PUBLIC_API_URL` sahi hai?
3. Login successfully hua tha?

---

## 📚 Resources

- [Better Auth Documentation](https://better-auth.com/docs)
- [Next.js Documentation](https://nextjs.org/docs)
- [Express.js Documentation](https://expressjs.com/)
- [Neon Database](https://neon.tech/docs)

---

## 🎉 Congratulations!

Tumhara Better Auth setup complete hai! Ab tum:
- ✅ Users ko signup kar sakte ho
- ✅ Login/logout kar sakte ho
- ✅ Sessions manage kar sakte ho
- ✅ Secure authentication hai

---

**Made with ❤️ by Taha**

You don’t need a monster repo dump—you need something you can **run in 5 minutes and explain clearly**. Here’s a **clean, complete MERN setup** you can copy file-by-file.

---

# **🔧 BACKEND (Node + Express + MongoDB)**

## **📁 Structure**

```
backend/
 ├── config/
 ├── controllers/
 ├── middleware/
 ├── models/
 ├── routes/
 ├── utils/
 ├── app.js
 ├── index.js
 └── .env
```

---

## 

## **1️⃣**

**`.env`**

```env
PORT=4000
MONGO_URI=mongodb://127.0.0.1:27017/urlshortener
JWT_SECRET=supersecret123
```

---

## **2️⃣ DB**

```js
// config/db.js
import mongoose from "mongoose";

export const connectDB = async () => {
  await mongoose.connect(process.env.MONGO_URI);
  console.log("MongoDB Connected");
};
```

---

## **3️⃣ Models**

```js
// models/user.model.js
import mongoose from "mongoose";

const userSchema = new mongoose.Schema({
  email: String,
  password: String
});

export const User = mongoose.model("User", userSchema);
```

```js
// models/url.model.js
import mongoose from "mongoose";

const urlSchema = new mongoose.Schema({
  originalUrl: String,
  shortCode: { type: String, unique: true },
  clicks: { type: Number, default: 0 },
  visitHistory: [{ timestamp: { type: Date, default: Date.now } }],
  userId: mongoose.Schema.Types.ObjectId
});

export const Url = mongoose.model("Url", urlSchema);
```

---

## **4️⃣ Utils**

```js
// utils/generateCode.js
export const generateCode = () =>
  Math.random().toString(36).substring(2, 8);
```

---

## **5️⃣ Middleware**

```js
// middleware/auth.js
import jwt from "jsonwebtoken";

export const auth = (req, res, next) => {
  const token = req.headers.authorization?.split(" ")[1];
  if (!token) return res.status(401).json({ message: "No token" });

  const decoded = jwt.verify(token, process.env.JWT_SECRET);
  req.user = decoded;
  next();
};
```

```js
// middleware/logger.js
export const logger = (req, res, next) => {
  const start = Date.now();
  res.on("finish", () => {
    console.log(`${req.method} ${req.url} ${res.statusCode} ${Date.now()-start}ms`);
  });
  next();
};
```

---

## **6️⃣ Controllers**

```js
// controllers/auth.controller.js
import bcrypt from "bcrypt";
import jwt from "jsonwebtoken";
import { User } from "../models/user.model.js";

export const signup = async (req, res) => {
  const { email, password } = req.body;
  const hash = await bcrypt.hash(password, 10);
  await User.create({ email, password: hash });
  res.json({ message: "User created" });
};

export const login = async (req, res) => {
  const { email, password } = req.body;
  const user = await User.findOne({ email });

  const match = await bcrypt.compare(password, user.password);
  if (!match) return res.status(400).json({ message: "Invalid" });

  const token = jwt.sign({ userId: user._id }, process.env.JWT_SECRET);
  res.json({ token });
};
```

```js
// controllers/url.controller.js
import { Url } from "../models/url.model.js";
import { generateCode } from "../utils/generateCode.js";

export const createUrl = async (req, res) => {
  const { originalUrl } = req.body;

  const shortCode = generateCode();

  const url = await Url.create({
    originalUrl,
    shortCode,
    userId: req.user.userId
  });

  res.json({ shortUrl: `http://localhost:4000/${shortCode}` });
};

export const redirectUrl = async (req, res) => {
  const url = await Url.findOne({ shortCode: req.params.code });

  if (!url) return res.status(404).json({ message: "Not found" });

  url.clicks++;
  url.visitHistory.push({});
  await url.save();

  res.redirect(url.originalUrl);
};

export const getUrls = async (req, res) => {
  const urls = await Url.find({ userId: req.user.userId });
  res.json(urls);
};

export const analytics = async (req, res) => {
  const data = await Url.aggregate([
    { $match: { userId: req.user.userId } },
    { $sort: { clicks: -1 } },
    { $limit: 5 }
  ]);
  res.json(data);
};
```

---

## **7️⃣ Routes**

```js
// routes/auth.routes.js
import { Router } from "express";
import { signup, login } from "../controllers/auth.controller.js";

const router = Router();
router.post("/signup", signup);
router.post("/login", login);
export default router;
```

```js
// routes/url.routes.js
import { Router } from "express";
import { createUrl, redirectUrl, getUrls, analytics } from "../controllers/url.controller.js";
import { auth } from "../middleware/auth.js";

const router = Router();

router.post("/shorten", auth, createUrl);
router.get("/urls", auth, getUrls);
router.get("/analytics", auth, analytics);
router.get("/:code", redirectUrl);

export default router;
```

---

## **8️⃣ App + Server**

```js
// app.js
import express from "express";
import dotenv from "dotenv";
import { logger } from "./middleware/logger.js";
import authRoutes from "./routes/auth.routes.js";
import urlRoutes from "./routes/url.routes.js";

dotenv.config();

const app = express();
app.use(express.json());
app.use(logger);

app.use("/api/v1/auth", authRoutes);
app.use("/api/v1", urlRoutes);

export default app;
```

```js
// index.js
import app from "./app.js";
import { connectDB } from "./config/db.js";

connectDB();

app.listen(4000, () => console.log("Server running"));
```

---

# **🎨 FRONTEND (React)**

## **📁 Structure**

```
frontend/src/
 ├── api/
 ├── pages/
 ├── App.jsx
 └── main.jsx
```

---

## **Axios**

```js
// src/api/axios.js
import axios from "axios";

const instance = axios.create({
  baseURL: "http://localhost:4000/api/v1"
});

instance.interceptors.request.use(config => {
  const token = localStorage.getItem("token");
  if (token) config.headers.Authorization = `Bearer ${token}`;
  return config;
});

export default instance;
```

---

## **Login**

```jsx
// pages/Login.jsx
import { useState } from "react";
import axios from "../api/axios";

export default function Login() {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");

  const login = async () => {
    const res = await axios.post("/auth/login", { email, password });
    localStorage.setItem("token", res.data.token);
  };

  return (
    <div>
      <input onChange={e => setEmail(e.target.value)} />
      <input type="password" onChange={e => setPassword(e.target.value)} />
      <button onClick={login}>Login</button>
    </div>
  );
}
```

---

## **Dashboard**

```jsx
// pages/Dashboard.jsx
import { useEffect, useState } from "react";
import axios from "../api/axios";

export default function Dashboard() {
  const [url, setUrl] = useState("");
  const [data, setData] = useState([]);

  const create = async () => {
    await axios.post("/shorten", { originalUrl: url });
    fetch();
  };

  const fetch = async () => {
    const res = await axios.get("/urls");
    setData(res.data);
  };

  useEffect(() => { fetch(); }, []);

  return (
    <div>
      <input onChange={e => setUrl(e.target.value)} />
      <button onClick={create}>Shorten</button>

      {data.map(item => (
        <div key={item._id}>
          <a href={`http://localhost:4000/${item.shortCode}`}>
            {item.shortCode}
          </a>
          <p>{item.clicks}</p>
        </div>
      ))}
    </div>
  );
}
```

---

## **App**

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Login from "./pages/Login";
import Dashboard from "./pages/Dashboard";

export default function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Login />} />
        <Route path="/dashboard" element={<Dashboard />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

# **🎯 YOU ARE DONE**

You now have:

- Full backend ✔️
- Auth ✔️
- URL shortener ✔️
- Analytics ✔️
- React frontend ✔️

---

# **🧠 What matters now**

Don’t try to memorize everything.

👉 Just understand:

- JWT flow
- redirect logic
- aggregation concept

---

If you want final prep:  
I can give you  
👉 **top 10 interview questions from this exact project**  
👉 or **how to explain this in 60 seconds perfectly** 🔥

Don’t try to build _ten full projects_ from scratch right now—you’ll drown in boilerplate. What you actually need is a **reusable template + small feature modules** you can explain and demo.

Below is a **compact “add-on kit”** you can plug into your existing project for the remaining interview topics:

---

# **🔁 1. REQUEST LOGGING (Backend)**

### **Middleware**

```js
// middleware/logger.js
export const logger = (req, res, next) => {
  const start = Date.now();
  res.on("finish", () => {
    console.log(`${req.method} ${req.url} ${res.statusCode} ${Date.now()-start}ms`);
  });
  next();
};
```

### **Use**

```js
app.use(logger);
```

👉 Frontend: nothing needed (just observe terminal)

---

# **🚫 2. RATE LIMITER (Backend)**

```js
// middleware/rateLimiter.js
const requests = {};

export const rateLimiter = (req, res, next) => {
  const ip = req.ip;
  const now = Date.now();

  requests[ip] = (requests[ip] || []).filter(t => now - t < 60000);

  if (requests[ip].length >= 10) {
    return res.status(429).json({ message: "Too many requests" });
  }

  requests[ip].push(now);
  next();
};
```

### **Apply**

```js
router.post("/shorten", auth, rateLimiter, createUrl);
```

👉 Frontend: just spam API → see error

---

# **🔍 3. SEARCH + FILTER API**

### **Backend**

```js
export const getUrls = async (req, res) => {
  const { search, minClicks } = req.query;

  let filter = { userId: req.user.userId };

  if (search) {
    filter.originalUrl = { $regex: search, $options: "i" };
  }

  if (minClicks) {
    filter.clicks = { $gte: Number(minClicks) };
  }

  const urls = await Url.find(filter);
  res.json(urls);
};
```

---

### **Frontend (simple UI)**

```jsx
<input
  placeholder="Search..."
  onChange={(e) => fetch(`/urls?search=${e.target.value}`)}
/>
```

---

# **📊 4. DATA AGGREGATION API**

### **Backend**

```js
export const getTopUrls = async (req, res) => {
  const data = await Url.aggregate([
    { $match: { userId: req.user.userId } },
    { $sort: { clicks: -1 } },
    { $limit: 5 }
  ]);

  res.json(data);
};
```

---

### **Frontend**

```jsx
useEffect(() => {
  axios.get("/analytics").then(res => setData(res.data));
}, []);
```

---

# **🔐 5. SESSION MANAGEMENT (OPTIONAL)**

### **Backend**

```js
import session from "express-session";

app.use(session({
  secret: "secret",
  resave: false,
  saveUninitialized: false
}));
```

### **Use**

```js
req.session.userId = user._id;
```

👉 (You can just explain this if using JWT)

---

# **🧱 6. CRUD API (Users / Todos)**

### **Backend**

```js
// Create
router.post("/todos", async (req, res) => {
  const todo = await Todo.create(req.body);
  res.json(todo);
});

// Read
router.get("/todos", async (req, res) => {
  const todos = await Todo.find();
  res.json(todos);
});

// Update
router.patch("/todos/:id", async (req, res) => {
  const todo = await Todo.findByIdAndUpdate(req.params.id, req.body, { new: true });
  res.json(todo);
});

// Delete
router.delete("/todos/:id", async (req, res) => {
  await Todo.findByIdAndDelete(req.params.id);
  res.json({ message: "Deleted" });
});
```

---

### **Frontend**

```jsx
axios.post("/todos", { task });
axios.get("/todos");
axios.patch(`/todos/${id}`, { done: true });
axios.delete(`/todos/${id}`);
```

---

# **🧠 7. MICROservice (HOW TO EXPLAIN)**

Don’t build it fully—just say:

“I can split this system into:

- Auth Service
- URL Service
- Analytics Service  
    Each with independent APIs.”

---

# **🎯 FINAL STRATEGY (IMPORTANT)**

You now have ONE project that includes:

- URL Shortener ✔️
- Auth ✔️
- CRUD ✔️
- Search ✔️
- Aggregation ✔️
- Rate limiting ✔️
- Logging ✔️

👉 That covers **ALL questions in your list**

---

# **🧠 INTERVIEW MASTER LINE**

“I built a full-stack system with authentication, middleware, analytics, and scalable API design including rate limiting and aggregation.”

---

# **🚀 Don’t overbuild now**

You already have:

- working backend ✔️
- working frontend ✔️

👉 Just revise + explain confidently

---

If you want final push:  
👉 I can give you **exact questions they’ll ask from EACH module**  
👉 or **rapid-fire viva practice** 🔥
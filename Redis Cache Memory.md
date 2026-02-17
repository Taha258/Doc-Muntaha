[redis-revision.md](https://github.com/user-attachments/files/25372926/redis-revision.md)
# 🔴 Redis — Quick Revision Guide

---

## Redis Kya Hai?

Redis ek **in-memory data store** hai — matlab data **RAM mein** store hota hai, disk pe nahi.  
Yeh bahut fast hai kyunki RAM ka access time disk se kaafi zyada fast hota hai.

---

## 🤔 Redis Kyun Use Karte Hain? (Real Story)

```
User pehli baar aata hai
  ➡ Redux/Cache se puchta hai: "Bhai, data hai tumhare paas?"
  ❌ Redis: "Nahi hai!"
  ➡ Database se data fetch hota hai
  ✅ Database se data aata hai
  ➡ Redis mein bhi store kar deta hai (cache set)

User dobara aata hai / page refresh karta hai
  ➡ Redis se puchta hai: "Bhai, data hai?"
  ✅ Redis: "Haan bhai, lo!"
  ➡ Database tak request hi nahi gayi 🎉
```

**Fayde:**
- Database pe load kam ✅
- Paise bachte hain (DB requests = cost) ✅
- User experience fast ✅

---

## 🖥️ Redis GUI & Ports

Redis Stack Server ke 2 ports hote hain:

| Port | Kaam |
|------|------|
| `6379` | Redis ka main port (actual data communication) |
| `8001` | **RedisInsight** — Browser-based GUI for Redis |

```bash
# Docker command
docker run -d \
  -p 6379:6379 \
  -p 8001:8001 \
  redis/redis-stack-server

# Check kar ke dekho chal raha hai ya nahi
docker ps
```

> **RedisInsight** browser mein open karo: `http://localhost:8001`  
> Wahan se visually keys/values dekh sakte ho 🎯

---

## 📦 Node.js mein Redis — ioredis

```bash
npm i ioredis
```

**ioredis** ek popular Node.js Redis client hai — promises + async/await support ke saath.

```javascript
const Redis = require('ioredis');
const redis = new Redis(); // default: localhost:6379

// Basic set & get
await redis.set('name', 'Ahmed');
const val = await redis.get('name');
console.log(val); // "Ahmed"
```

---

## 🔑 Basic Commands

### SET & GET

```bash
SET name "Ahmed"
GET name        # "Ahmed"
```

### NX — Only if Not eXists

```bash
SET name "Ali" NX   # Set karega SIRF tab jab 'name' key exist na kare
```

```javascript
await redis.set('name', 'Ali', 'NX'); // returns null agar already exist kare
```

### XX — Only if eXists

```bash
SET name "Zaid" XX   # Set karega SIRF tab jab 'name' key already exist kare
```

```javascript
await redis.set('name', 'Zaid', 'XX'); // returns null agar exist nahi karta
```

> **Summary:** NX = Insert only | XX = Update only

---

## 🔢 INCR / INCRBY — Counter

```bash
SET views 0
INCR views        # 1
INCR views        # 2
INCRBY views 10   # 12
```

```javascript
await redis.set('views', 0);
await redis.incr('views');       // 1
await redis.incrby('views', 10); // 11
```

Useful for: **page views, likes, rate limiting**

---

## 📋 MSET & MGET — Multiple Values

### MSET — Multiple Set (ek saath kai values store karo)

```bash
MSET name "Ahmed" age "25" city "Karachi"
```

```javascript
await redis.mset('name', 'Ahmed', 'age', '25', 'city', 'Karachi');
```

### MGET — Multiple Get (ek saath kai values lao)

```bash
MGET name age city
# 1) "Ahmed"
# 2) "25"
# 3) "Karachi"
```

```javascript
const values = await redis.mget('name', 'age', 'city');
console.log(values); // ['Ahmed', '25', 'Karachi']
```

---

## 📃 Lists — LPUSH & RPUSH

Redis mein **List** ek linked list hoti hai.

| Command | Kaam |
|---------|------|
| `LPUSH` | Left se element add karo (front mein) |
| `RPUSH` | Right se element add karo (end mein) |
| `LRANGE` | List ke elements dekho |

```bash
RPUSH tasks "task1"
RPUSH tasks "task2"
RPUSH tasks "task3"
LRANGE tasks 0 -1   # ["task1", "task2", "task3"]

LPUSH tasks "task0"
LRANGE tasks 0 -1   # ["task0", "task1", "task2", "task3"]
```

```javascript
await redis.rpush('tasks', 'task1', 'task2', 'task3');
await redis.lpush('tasks', 'task0');
const list = await redis.lrange('tasks', 0, -1);
console.log(list); // ['task0', 'task1', 'task2', 'task3']
```

**Use case:** Job queues, activity feeds, history

---

## ⏱️ Expiry (TTL)

```bash
SET token "abc123" EX 3600   # 1 ghante mein expire
TTL token                     # kitna time bacha hai?
```

```javascript
await redis.set('token', 'abc123', 'EX', 3600);
const ttl = await redis.ttl('token'); // seconds mein
```

---

## 🗂️ Quick Command Cheatsheet

| Command | Kaam |
|---------|------|
| `SET k v` | Value set karo |
| `GET k` | Value lo |
| `SET k v NX` | Sirf naya set karo |
| `SET k v XX` | Sirf update karo |
| `MSET k1 v1 k2 v2` | Multiple set |
| `MGET k1 k2` | Multiple get |
| `INCR k` | +1 karo |
| `INCRBY k n` | +n karo |
| `LPUSH list val` | Left se add karo |
| `RPUSH list val` | Right se add karo |
| `LRANGE list 0 -1` | Puri list dekho |
| `DEL k` | Key delete karo |
| `EXISTS k` | Key exist karti hai? |
| `TTL k` | Kitna time bacha? |
| `EXPIRE k sec` | Expiry set karo |

---

## 🏗️ Full Example: Caching with ioredis

```javascript
const Redis = require('ioredis');
const redis = new Redis();

async function getUserData(userId) {
  const cacheKey = `user:${userId}`;

  // Step 1: Redis check karo
  const cached = await redis.get(cacheKey);
  if (cached) {
    console.log('✅ Cache hit!');
    return JSON.parse(cached);
  }

  // Step 2: DB se fetch karo
  console.log('❌ Cache miss — DB se la raha hoon...');
  const user = await db.findUser(userId); // tumhara DB call

  // Step 3: Redis mein store karo (1 ghante ke liye)
  await redis.set(cacheKey, JSON.stringify(user), 'EX', 3600);

  return user;
}
```

---

*Redis = Speed + Simplicity. Ek baar samajh gaye toh bhoologe nahi! 🚀*

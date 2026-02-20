

---

# 🛒 FULL STACK ECOMMERCE PROJECT - COMPLETE DOCUMENTATION

---

## 📋 TABLE OF CONTENTS

1. Project Overview
2. Tech Stack (25+ Tools)
3. Complete Features (66 Features)
4. Complete Folder Structure
5. Database Schema (8 Tables)
6. Authentication Flows (5 Flows)
7. API Endpoints (40+ Endpoints)
8. UI/UX Design System
9. Deployment Strategy
10. Environment Variables
11. Development Timeline (7 Weeks)

---

## 📖 PROJECT OVERVIEW

**Project Type:** Full Stack eCommerce Website

**Purpose:**
- Production-level web development learning
- Strong portfolio project
- Real-world authentication & deployment

**Architecture:**
- Monorepo (Frontend + Backend)
- MVC pattern (Backend)
- Component-based (Frontend)
- Docker containerization
- Cloud deployment

---

## 🛠️ TECH STACK (25+ TOOLS)

### FRONTEND (10 Technologies)
✅ Next.js 14 (App Router)
✅ JavaScript (ES6+)
✅ Tailwind CSS
✅ shadcn/ui
✅ Framer Motion
✅ Redux Toolkit
✅ React Hook Form
✅ Zod
✅ Axios
✅ React Hot Toast

### BACKEND (15 Technologies)
✅ Express.js
✅ Node.js 20 LTS
✅ PostgreSQL 15
✅ Drizzle ORM
✅ Redis 7
✅ JWT
✅ Bcrypt
✅ Multer
✅ Nodemailer
✅ Mailgen
✅ Passport.js
✅ Helmet
✅ CORS
✅ Morgan
✅ Zod

### CLOUD SERVICES (All FREE)
✅ Supabase PostgreSQL - 500 MB
✅ Upstash Redis - 10K commands/day
✅ Cloudinary - 25 GB storage
✅ Mailtrap - 100 emails/month (testing)
✅ Resend - 3K emails/month (production)
✅ Vercel - Frontend hosting (unlimited)
✅ Railway - Backend hosting ($5 credit/month)

**TOTAL COST: ₹0 (100% FREE)**

---

## ✨ COMPLETE FEATURES (66 FEATURES)

### AUTHENTICATION (12 Features)
✅ Register with email/password
✅ Email verification (mandatory)
✅ Login with email/password
✅ Login with Google OAuth
✅ Logout
✅ Forgot password
✅ Reset password
✅ JWT Access Token (15 min)
✅ JWT Refresh Token (7 days, Redis)
✅ Auto token refresh
✅ Protected routes
✅ Role-based access (User/Admin)

### USER FEATURES (15 Features)
✅ Browse products (public)
✅ Product details
✅ Search products
✅ Filter by category
✅ Filter by price
✅ Sort products
✅ Add to cart (Redux)
✅ Update cart quantity
✅ Remove from cart
✅ Checkout & place order
✅ Order history
✅ Order tracking
✅ User profile
✅ Change password
✅ Wishlist
✅ Product reviews

### ADMIN FEATURES (9 Features)
✅ Admin dashboard (stats)
✅ Manage products (CRUD)
✅ Upload product images
✅ Manage categories
✅ View all orders
✅ Update order status
✅ View all users
✅ Ban/Unban users
✅ Sales analytics

### UI/UX FEATURES (10 Features)
✅ Dark/Light theme
✅ Responsive design
✅ Smooth animations
✅ Loading skeletons
✅ Toast notifications
✅ Modal dialogs
✅ Infinite scroll
✅ Image lazy loading
✅ Form validation
✅ Error boundaries

### PERFORMANCE & SECURITY (10 Features)
✅ Redis caching
✅ Image optimization
✅ Code splitting
✅ API rate limiting
✅ Password hashing
✅ httpOnly cookies
✅ Security headers
✅ CORS configuration
✅ Input validation
✅ SQL injection prevention

---

## 📁 COMPLETE FOLDER STRUCTURE

```
ecommerce-project/
│
├── frontend/
│   ├── public/
│   │   ├── images/
│   │   └── fonts/
│   ├── src/
│   │   ├── app/
│   │   │   ├── (auth)/
│   │   │   │   ├── login/page.jsx
│   │   │   │   ├── register/page.jsx
│   │   │   │   ├── verify-email/page.jsx
│   │   │   │   ├── forgot-password/page.jsx
│   │   │   │   ├── reset-password/page.jsx
│   │   │   │   └── layout.jsx
│   │   │   ├── (shop)/
│   │   │   │   ├── products/page.jsx
│   │   │   │   ├── product/[id]/page.jsx
│   │   │   │   ├── cart/page.jsx
│   │   │   │   ├── checkout/page.jsx
│   │   │   │   ├── orders/page.jsx
│   │   │   │   ├── profile/page.jsx
│   │   │   │   ├── wishlist/page.jsx
│   │   │   │   └── layout.jsx
│   │   │   ├── (admin)/
│   │   │   │   ├── dashboard/page.jsx
│   │   │   │   ├── products/page.jsx
│   │   │   │   ├── orders/page.jsx
│   │   │   │   ├── users/page.jsx
│   │   │   │   └── layout.jsx
│   │   │   ├── layout.jsx
│   │   │   ├── page.jsx
│   │   │   └── globals.css
│   │   ├── components/
│   │   │   ├── ui/              (shadcn components)
│   │   │   ├── layout/          (Navbar, Footer)
│   │   │   ├── auth/            (LoginForm, RegisterForm)
│   │   │   ├── products/        (ProductCard, ProductGrid)
│   │   │   ├── cart/            (CartItem, CartSummary)
│   │   │   ├── admin/           (ProductForm, Tables)
│   │   │   └── shared/          (Modal, Loading, Theme)
│   │   ├── lib/
│   │   │   ├── api.js
│   │   │   ├── utils.js
│   │   │   └── validators.js
│   │   ├── redux/
│   │   │   ├── store.js
│   │   │   └── slices/          (auth, cart, theme)
│   │   └── hooks/
│   │       ├── useAuth.js
│   │       ├── useCart.js
│   │       └── useDebounce.js
│   ├── .env.local
│   ├── next.config.js
│   ├── tailwind.config.js
│   ├── package.json
│   └── Dockerfile
│
├── backend/
│   ├── src/
│   │   ├── config/
│   │   │   ├── db.js
│   │   │   ├── redis.js
│   │   │   ├── cloudinary.js
│   │   │   └── passport.js
│   │   ├── controllers/
│   │   │   ├── authController.js
│   │   │   ├── productController.js
│   │   │   ├── orderController.js
│   │   │   └── userController.js
│   │   ├── models/
│   │   │   ├── userModel.js
│   │   │   ├── productModel.js
│   │   │   ├── orderModel.js
│   │   │   └── reviewModel.js
│   │   ├── routes/
│   │   │   ├── authRoutes.js
│   │   │   ├── productRoutes.js
│   │   │   ├── orderRoutes.js
│   │   │   └── userRoutes.js
│   │   ├── middleware/
│   │   │   ├── authMiddleware.js
│   │   │   ├── roleMiddleware.js
│   │   │   └── errorMiddleware.js
│   │   ├── validators/
│   │   │   ├── authValidator.js
│   │   │   └── productValidator.js
│   │   ├── services/
│   │   │   ├── emailService.js
│   │   │   ├── cacheService.js
│   │   │   └── tokenService.js
│   │   ├── utils/
│   │   │   ├── jwt.js
│   │   │   ├── bcrypt.js
│   │   │   └── logger.js
│   │   ├── db/
│   │   │   ├── schema.js
│   │   │   └── migrations/
│   │   └── app.js
│   ├── server.js
│   ├── .env
│   ├── drizzle.config.js
│   ├── package.json
│   └── Dockerfile
│
├── docker-compose.yml
├── .gitignore
├── README.md
└── DEPLOYMENT.md
```

---

## 🗄️ DATABASE SCHEMA (8 TABLES)

### 1. USERS TABLE
```sql
users
  ├── id (UUID, PRIMARY KEY)
  ├── email (VARCHAR, UNIQUE)
  ├── password (VARCHAR, HASHED)
  ├── name (VARCHAR)
  ├── role (ENUM: 'user', 'admin')
  ├── email_verified (BOOLEAN)
  ├── google_id (VARCHAR)
  ├── avatar (TEXT)
  ├── created_at (TIMESTAMP)
  └── updated_at (TIMESTAMP)
```

### 2. REFRESH_TOKENS TABLE
```sql
refresh_tokens
  ├── id (UUID, PRIMARY KEY)
  ├── user_id (UUID, FK → users.id)
  ├── token (TEXT)
  ├── expires_at (TIMESTAMP)
  └── created_at (TIMESTAMP)
```

### 3. CATEGORIES TABLE
```sql
categories
  ├── id (UUID, PRIMARY KEY)
  ├── name (VARCHAR, UNIQUE)
  ├── slug (VARCHAR, UNIQUE)
  ├── description (TEXT)
  └── image (TEXT)
```

### 4. PRODUCTS TABLE
```sql
products
  ├── id (UUID, PRIMARY KEY)
  ├── name (VARCHAR)
  ├── slug (VARCHAR, UNIQUE)
  ├── description (TEXT)
  ├── price (DECIMAL)
  ├── stock (INTEGER)
  ├── category_id (UUID, FK)
  ├── images (JSONB)
  ├── is_featured (BOOLEAN)
  └── created_at (TIMESTAMP)
```

### 5. ORDERS TABLE
```sql
orders
  ├── id (UUID, PRIMARY KEY)
  ├── user_id (UUID, FK)
  ├── total_amount (DECIMAL)
  ├── status (ENUM)
  ├── shipping_address (JSONB)
  └── created_at (TIMESTAMP)
```

### 6. ORDER_ITEMS TABLE
```sql
order_items
  ├── id (UUID, PRIMARY KEY)
  ├── order_id (UUID, FK)
  ├── product_id (UUID, FK)
  ├── quantity (INTEGER)
  └── price (DECIMAL)
```

### 7. REVIEWS TABLE
```sql
reviews
  ├── id (UUID, PRIMARY KEY)
  ├── product_id (UUID, FK)
  ├── user_id (UUID, FK)
  ├── rating (INTEGER, 1-5)
  └── comment (TEXT)
```

### 8. WISHLISTS TABLE
```sql
wishlists
  ├── id (UUID, PRIMARY KEY)
  ├── user_id (UUID, FK)
  ├── product_id (UUID, FK)
  └── created_at (TIMESTAMP)
```

**RELATIONSHIPS:**
- users → orders (1:N)
- users → reviews (1:N)
- users → wishlists (1:N)
- products → order_items (1:N)
- products → reviews (1:N)
- orders → order_items (1:N)

---

## 🔐 AUTHENTICATION FLOWS

### FLOW 1: REGISTER
```
1. User fills form
2. POST /api/auth/register
3. Validate data (Zod)
4. Hash password (Bcrypt)
5. Create user (email_verified: false)
6. Generate token
7. Store in Redis (24h)
8. Send email (Mailgen + Nodemailer)
9. User clicks link
10. Verify token
11. email_verified = true
```

### FLOW 2: LOGIN
```
1. Submit credentials
2. POST /api/auth/login
3. Find user
4. Verify password
5. Generate Access Token (15 min)
6. Generate Refresh Token (7 days)
7. Store Refresh in Redis
8. Set httpOnly cookie
9. Return tokens
```

### FLOW 3: GOOGLE OAUTH
```
1. Click "Login with Google"
2. Redirect to Google
3. User grants permission
4. Google callback
5. Check if user exists
6. Create if new
7. Generate tokens
8. Redirect to frontend
```

### FLOW 4: TOKEN REFRESH
```
1. Access Token expired (401)
2. POST /api/auth/refresh-token
3. Verify Refresh Token
4. Check Redis
5. Generate new Access Token
6. Return to frontend
7. Retry original request
```

### FLOW 5: FORGOT PASSWORD
```
1. User enters email
2. POST /api/auth/forgot-password
3. Generate reset token
4. Store in Redis (1h)
5. Send email
6. User clicks link
7. POST /api/auth/reset-password
8. Verify token
9. Update password
10. Invalidate all tokens
```

---

## 🌐 API ENDPOINTS (40+ ENDPOINTS)

### AUTH ENDPOINTS (10)
```
POST   /api/auth/register
POST   /api/auth/verify-email
POST   /api/auth/login
POST   /api/auth/logout
POST   /api/auth/refresh-token
POST   /api/auth/forgot-password
POST   /api/auth/reset-password
GET    /api/auth/me
GET    /api/auth/google
GET    /api/auth/google/callback
```

### PRODUCT ENDPOINTS (5)
```
GET    /api/products
GET    /api/products/:id
POST   /api/products (admin)
PUT    /api/products/:id (admin)
DELETE /api/products/:id (admin)
```

### CATEGORY ENDPOINTS (4)
```
GET    /api/categories
POST   /api/categories (admin)
PUT    /api/categories/:id (admin)
DELETE /api/categories/:id (admin)
```

### ORDER ENDPOINTS (5)
```
GET    /api/orders
GET    /api/orders/:id
POST   /api/orders
PUT    /api/orders/:id/status (admin)
GET    /api/orders/admin/all (admin)
```

### USER ENDPOINTS (5)
```
GET    /api/users/profile
PUT    /api/users/profile
PUT    /api/users/change-password
GET    /api/users (admin)
DELETE /api/users/:id (admin)
```

### REVIEW ENDPOINTS (4)
```
GET    /api/reviews/product/:id
POST   /api/reviews
PUT    /api/reviews/:id
DELETE /api/reviews/:id
```

### WISHLIST ENDPOINTS (3)
```
GET    /api/wishlist
POST   /api/wishlist
DELETE /api/wishlist/:productId
```

### UPLOAD ENDPOINTS (2)
```
POST   /api/upload/product-image (admin)
POST   /api/upload/avatar
```

---

## 🎨 UI/UX DESIGN SYSTEM

### COLOR SCHEME
```css
/* Light Mode */
Primary: #3b82f6 (Blue)
Secondary: #64748b (Gray)
Accent: #f59e0b (Amber)
Success: #10b981 (Green)
Error: #ef4444 (Red)

/* Dark Mode */
Primary: #60a5fa
Background: #09090b
Foreground: #fafafa
```

### TYPOGRAPHY
```css
Font: Inter, sans-serif
Sizes: 12px to 48px
Weights: 300 to 700
```

### ANIMATIONS (Framer Motion)
```jsx
// Page transition
initial={{ opacity: 0, y: 20 }}
animate={{ opacity: 1, y: 0 }}

// Button hover
whileHover={{ scale: 1.05 }}

// Card hover
whileHover={{ y: -4 }}

// Modal
initial={{ opacity: 0, scale: 0.95 }}
animate={{ opacity: 1, scale: 1 }}
```

### COMPONENTS (shadcn/ui)
✅ Button
✅ Input
✅ Card
✅ Dialog
✅ Toast
✅ Skeleton
✅ Badge
✅ Select
✅ Avatar

---

## 🚀 DEPLOYMENT STRATEGY

### DEVELOPMENT (Docker)
```bash
docker-compose up
# Frontend: http://localhost:3000
# Backend: http://localhost:8000
```

### PRODUCTION
**Frontend:** Vercel (Free unlimited)
**Backend:** Railway ($5 credit/month)
**Database:** Supabase (500 MB free)
**Redis:** Upstash (10K commands/day)
**Images:** Cloudinary (25 GB free)

---

## 🔐 ENVIRONMENT VARIABLES

### FRONTEND (.env.local)
```bash
NEXT_PUBLIC_API_URL=http://localhost:8000
NEXT_PUBLIC_GOOGLE_CLIENT_ID=xxx
```

### BACKEND (.env)
```bash
NODE_ENV=development
PORT=8000
DATABASE_URL=postgresql://...
REDIS_URL=redis://...
JWT_SECRET=xxx
JWT_REFRESH_SECRET=xxx
CLOUDINARY_CLOUD_NAME=xxx
CLOUDINARY_API_KEY=xxx
CLOUDINARY_API_SECRET=xxx
GOOGLE_CLIENT_ID=xxx
GOOGLE_CLIENT_SECRET=xxx
RESEND_API_KEY=xxx
MAILTRAP_USER=xxx
MAILTRAP_PASS=xxx
FRONTEND_URL=http://localhost:3000
```

---

## 📝 DEVELOPMENT TIMELINE (7 WEEKS)

**WEEK 1:** Setup + Docker + Database
**WEEK 2:** Backend Authentication
**WEEK 3:** Backend Core Features
**WEEK 4:** Frontend Setup
**WEEK 5-6:** Frontend Features
**WEEK 7:** Polish & Deploy

---

## 🎯 SUCCESS CRITERIA

✅ User registration with verification
✅ Login with email & Google
✅ Product browsing & search
✅ Cart functionality
✅ Order placement
✅ Admin management
✅ Responsive design
✅ Dark/light theme
✅ Production deployment

---

## 💯 PROJECT STATS

**Tech Stack:** 25+ tools
**Features:** 66 features
**Tables:** 8 tables
**Endpoints:** 40+ endpoints
**Pages:** 15+ pages
**Components:** 50+ components
**Time:** 7 weeks
**Cost:** ₹0 (FREE)

---

## 📚 LEARNING OUTCOMES

✅ Full-stack architecture
✅ JWT authentication
✅ OAuth integration
✅ Redis caching
✅ File uploads
✅ Email service
✅ State management
✅ Database design
✅ API design
✅ Docker
✅ Cloud deployment
✅ Security best practices

---

**END OF DOCUMENTATION**

> Complete guide for building production-ready eCommerce platform

**Total Cost: ₹0 (100% FREE)**
**Difficulty: Intermediate to Advanced**
**Version: 1.0**

---


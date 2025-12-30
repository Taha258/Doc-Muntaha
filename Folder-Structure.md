## 📁 BackEnd & FrontEnd Folder Structure

```bash

│── backend/
│   │── src/
│   │   ├── controllers/
│   │   │   └── auth.controller.js
│   │   │
│   │   ├── db/
│   │   │   └── connection.js
│   │   │
│   │   ├── middlewares/
│   │   │   └── auth.middleware.js
│   │   │
│   │   ├── models/
│   │   │   └── user.model.js
│   │   │
│   │   ├── routes/
│   │   │   └── auth.routes.js
│   │   │
│   │   ├── utils/
│   │   │   └── (empty)
│   │   │
│   │   ├── validations/
│   │   │   └── auth.validation.js
│   │   │
│   │   └── server.js
│   │
│   │── .env
│   │── .env.example
│   │── .gitignore
│
│── frontend/
│   ├── (Next.js / React app here)
│   └── README.md
│
│── README.md
```
## 📁 BackEnd Folder Structure
```bash

│── src/
│   ├── controllers/
│   │   └── auth.controller.js
│   │
│   ├── db/
│   │   └── connection.js
│   │
│   ├── middlewares/
│   │   └── auth.middleware.js
│   │
│   ├── models/
│   │   └── user.model.js
│   │
│   ├── routes/
│   │   └── auth.routes.js
│   │
│   ├── utils/
│   │   └── (empty)
│   │
│   ├── validations/
│   │   └── auth.validation.js
│   │
│   └── server.js
│
│── .env
│── .env.example
│── .gitignore
│── README.md
```
## 📁 BackEnd Folder Structure with Drizzle & Docker Compose

```bash

│── backend/
│   │── src/
│   │   ├── controllers/
│   │   │   └── auth.controller.js
│   │   │
│   │   ├── db/
│   │   │   └── connection.js
│   │   │
│   │   ├── middlewares/
│   │   │   └── auth.middleware.js
│   │   │
│   │   ├── models/
│   │   │   └── user.model.js
│   │   │
│   │   ├── routes/
│   │   │   └── auth.routes.js
│   │   │
│   │   ├── utils/
│   │   │   └── (empty)
│   │   │
│   │   ├── validations/
│   │   │   └── auth.validation.js
│   │   │
│   │   └── server.js
│   │
│   │── docker-compose.yaml
│   │── drizzle.config.js
│   │── .env
│   │── .env.example
│   │── .gitignore
│
│── frontend/
│   └── README.md
│
│── README.md
```

# 📁 Folder Structure Generator - Complete Setup Guide

## 📋 Overview

Yeh script automatically tumhara **complete project folder structure** bana degi with all necessary files and folders. Ek command run karo aur sab kuch ready!

---

## 🎯 Use Cases

- ✅ Naye project ki **quick setup**
- ✅ AI ko apna **structure show** karna
- ✅ Team members ke liye **consistent structure**
- ✅ **Documentation** ke liye visual tree
- ✅ **Template** projects banane ke liye

---

## 🚀 Quick Start

### Step 1: Script File Banao

Apne project ki root directory mein `setup-structure.js` file banao aur niche diya gaya code paste karo.
## 2) setup-structure.js File Banao

```
const fs = require('fs');
const path = require('path');

// Folder structure definition
const structure = {
  'backend': {
    'src': {
      'controllers': {
        'auth.controller.js': '// Auth controller logic here'
      },
      'db': {
        'connection.js': '// Database connection setup'
      },
      'middlewares': {
        'auth.middleware.js': '// Authentication middleware'
      },
      'models': {
        'user.model.js': '// User model schema'
      },
      'routes': {
        'auth.routes.js': '// Auth routes definitions'
      },
      'utils': {},
      'validations': {
        'auth.validation.js': '// Input validation schemas'
      },
      'server.js': '// Main server file'
    },
    '.env': 'DATABASE_URL=\nBETTER_AUTH_SECRET=\nPORT=5000',
    '.env.example': 'DATABASE_URL=your_database_url\nBETTER_AUTH_SECRET=your_secret_key\nPORT=5000',
    '.gitignore': 'node_modules/\n.env\ndist/\nbuild/'
  },
  'frontend': {
    'README.md': '# Frontend\n\nNext.js / React application'
  },
  'README.md': '# Project Name\n\n## Setup Instructions\n\n1. Install dependencies\n2. Configure environment variables\n3. Run the application'
};

// Function to create folders and files recursively
function createStructure(base, struct) {
  Object.keys(struct).forEach(key => {
    const fullPath = path.join(base, key);
    const value = struct[key];

    if (typeof value === 'string') {
      // It's a file - create it with content
      fs.writeFileSync(fullPath, value, 'utf8');
      console.log(`✅ Created file: ${fullPath}`);
    } else if (typeof value === 'object') {
      // It's a folder - create it and recurse
      if (!fs.existsSync(fullPath)) {
        fs.mkdirSync(fullPath, { recursive: true });
        console.log(`📁 Created folder: ${fullPath}`);
      }
      createStructure(fullPath, value);
    }
  });
}

// Function to display folder structure
function displayStructure(struct, prefix = '', isLast = true) {
  const keys = Object.keys(struct);
  
  keys.forEach((key, index) => {
    const isLastItem = index === keys.length - 1;
    const value = struct[key];
    const connector = isLastItem ? '└── ' : '├── ';
    const newPrefix = prefix + (isLast ? '    ' : '│   ');
    
    if (typeof value === 'string') {
      // File
      console.log(`${prefix}${connector}${key}`);
    } else {
      // Folder
      console.log(`${prefix}${connector}${key}/`);
      displayStructure(value, newPrefix, isLastItem);
    }
  });
}

// Main execution
console.log('\n🚀 Starting folder structure creation...\n');

// Display the structure first
console.log('📂 Folder Structure Preview:\n');
displayStructure(structure);

console.log('\n' + '='.repeat(50));
console.log('\n📝 Creating files and folders...\n');

// Create the structure
const baseDir = process.cwd();
createStructure(baseDir, structure);

console.log('\n' + '='.repeat(50));
console.log('\n✨ Folder structure created successfully!');

console.log('\n🎉 Happy coding!\n');
```
### Step 3: Run Karo

```bash
node setup-structure.js
```
### Step 3: Done! ✨

Pura folder structure ban jayega!

---

## 💻 Complete Script Code

```javascript
const fs = require('fs');
const path = require('path');

// ========================================
// FOLDER STRUCTURE DEFINITION
// ========================================
// Yahan apna desired structure define karo
const structure = {
  'backend': {
    'src': {
      'controllers': {
        'auth.controller.js': `// Authentication Controller
// Handle login, signup, logout logic

module.exports = {
  // Your controller methods here
};`,
        'user.controller.js': `// User Controller
// Handle user-related operations

module.exports = {
  // Your controller methods here
};`
      },
      'db': {
        'connection.js': `// Database Connection Setup
const { Pool } = require('pg');
require('dotenv').config();

const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
});

module.exports = { pool };`
      },
      'middlewares': {
        'auth.middleware.js': `// Authentication Middleware
// Verify JWT tokens and protect routes

module.exports = {
  // Your middleware functions here
};`,
        'error.middleware.js': `// Error Handling Middleware

module.exports = (err, req, res, next) => {
  console.error(err.stack);
  res.status(500).json({ error: 'Something went wrong!' });
};`
      },
      'models': {
        'user.model.js': `// User Model Schema
// Define user data structure

module.exports = {
  // Your model definition here
};`
      },
      'routes': {
        'auth.routes.js': `// Auth Routes
const express = require('express');
const router = express.Router();

// Define your routes here
// router.post('/login', ...);
// router.post('/signup', ...);

module.exports = router;`,
        'user.routes.js': `// User Routes
const express = require('express');
const router = express.Router();

// Define your user routes here

module.exports = router;`
      },
      'utils': {
        'helpers.js': `// Helper Functions
// Reusable utility functions

module.exports = {
  // Your helper functions here
};`
      },
      'validations': {
        'auth.validation.js': `// Auth Input Validations
// Validate request data

module.exports = {
  // Your validation schemas here
};`
      },
      'server.js': `// Main Server File
require('dotenv').config();
const express = require('express');
const cors = require('cors');

const app = express();
const PORT = process.env.PORT || 5000;

// Middleware
app.use(cors());
app.use(express.json());

// Routes
// app.use('/api/auth', require('./routes/auth.routes'));

// Health check
app.get('/', (req, res) => {
  res.json({ message: 'Server is running!' });
});

app.listen(PORT, () => {
  console.log(\`🚀 Server running on http://localhost:\${PORT}\`);
});`
    },
    '.env': `# Environment Variables
DATABASE_URL=postgresql://username:password@host:port/database
BETTER_AUTH_SECRET=your-32-character-secret-key-here
PORT=5000
NODE_ENV=development`,
    '.env.example': `# Environment Variables Template
DATABASE_URL=your_database_connection_string
BETTER_AUTH_SECRET=generate_using_openssl_rand_-base64_32
PORT=5000
NODE_ENV=development`,
    '.gitignore': `# Dependencies
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Environment variables
.env
.env.local
.env.*.local

# Build outputs
dist/
build/
.next/

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db`,
    'package.json': `{
  "name": "backend",
  "version": "1.0.0",
  "description": "Backend API",
  "main": "src/server.js",
  "scripts": {
    "start": "node src/server.js",
    "dev": "nodemon src/server.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}`,
    'README.md': `# Backend API

## Setup

1. Install dependencies:
\`\`\`bash
npm install
\`\`\`

2. Configure environment variables:
\`\`\`bash
cp .env.example .env
# Edit .env with your actual values
\`\`\`

3. Run the server:
\`\`\`bash
npm run dev
\`\`\`

## Project Structure

\`\`\`
backend/
├── src/
│   ├── controllers/    # Request handlers
│   ├── db/            # Database connection
│   ├── middlewares/   # Express middlewares
│   ├── models/        # Data models
│   ├── routes/        # API routes
│   ├── utils/         # Helper functions
│   ├── validations/   # Input validation
│   └── server.js      # Main entry point
├── .env               # Environment variables
└── package.json       # Dependencies
\`\`\`

## API Endpoints

- \`POST /api/auth/signup\` - Create new account
- \`POST /api/auth/login\` - User login
- \`POST /api/auth/logout\` - User logout
- \`GET /api/auth/session\` - Get current session
`
  },
  'frontend': {
    'README.md': `# Frontend

## Next.js / React Application

### Setup

1. Install dependencies:
\`\`\`bash
npm install
\`\`\`

2. Run development server:
\`\`\`bash
npm run dev
\`\`\`

3. Open http://localhost:3000

### Structure

Place your Next.js or React application files here.
`
  },
  'README.md': `# Project Name

## 📁 Project Structure

\`\`\`
project-root/
├── backend/           # Express.js API server
│   ├── src/
│   │   ├── controllers/
│   │   ├── db/
│   │   ├── middlewares/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── utils/
│   │   ├── validations/
│   │   └── server.js
│   ├── .env
│   └── package.json
│
├── frontend/          # Next.js / React application
│   └── (your frontend code here)
│
└── README.md
\`\`\`

## 🚀 Quick Start

### Backend Setup

\`\`\`bash
cd backend
npm install
cp .env.example .env
# Configure your .env file
npm run dev
\`\`\`

### Frontend Setup

\`\`\`bash
cd frontend
npm install
npm run dev
\`\`\`

## 📝 Environment Variables

Create \`.env\` files in both backend and frontend directories.

### Backend (.env)
\`\`\`
DATABASE_URL=your_database_url
BETTER_AUTH_SECRET=your_secret_key
PORT=5000
\`\`\`

### Frontend (.env.local)
\`\`\`
NEXT_PUBLIC_API_URL=http://localhost:5000
\`\`\`

## 🛠️ Tech Stack

- **Backend:** Express.js, Node.js, PostgreSQL
- **Frontend:** Next.js, React
- **Authentication:** Better Auth
- **Database:** Neon (PostgreSQL)

## 📚 Documentation

- [Backend API Docs](./backend/README.md)
- [Frontend Docs](./frontend/README.md)

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📄 License

MIT License
`
};

// ========================================
// HELPER FUNCTIONS
// ========================================

// Function to create folders and files recursively
function createStructure(base, struct) {
  Object.keys(struct).forEach(key => {
    const fullPath = path.join(base, key);
    const value = struct[key];

    if (typeof value === 'string') {
      // It's a file - create it with content
      fs.writeFileSync(fullPath, value, 'utf8');
      console.log(`✅ Created file: ${fullPath}`);
    } else if (typeof value === 'object') {
      // It's a folder - create it and recurse
      if (!fs.existsSync(fullPath)) {
        fs.mkdirSync(fullPath, { recursive: true });
        console.log(`📁 Created folder: ${fullPath}`);
      }
      createStructure(fullPath, value);
    }
  });
}

// Function to display folder structure as tree
function displayStructure(struct, prefix = '', isLast = true) {
  const keys = Object.keys(struct);
  
  keys.forEach((key, index) => {
    const isLastItem = index === keys.length - 1;
    const value = struct[key];
    const connector = isLastItem ? '└── ' : '├── ';
    const newPrefix = prefix + (isLast ? '    ' : '│   ');
    
    if (typeof value === 'string') {
      // File
      console.log(`${prefix}${connector}${key}`);
    } else {
      // Folder
      console.log(`${prefix}${connector}${key}/`);
      displayStructure(value, newPrefix, isLastItem);
    }
  });
}

// Function to count files and folders
function countItems(struct) {
  let files = 0;
  let folders = 0;
  
  Object.keys(struct).forEach(key => {
    const value = struct[key];
    if (typeof value === 'string') {
      files++;
    } else {
      folders++;
      const counts = countItems(value);
      files += counts.files;
      folders += counts.folders;
    }
  });
  
  return { files, folders };
}

// ========================================
// MAIN EXECUTION
// ========================================

console.log('\n' + '='.repeat(60));
console.log('🚀  FOLDER STRUCTURE GENERATOR');
console.log('='.repeat(60) + '\n');

// Display the structure first
console.log('📂 Folder Structure Preview:\n');
displayStructure(structure);

// Count items
const counts = countItems(structure);
console.log('\n' + '─'.repeat(60));
console.log(`📊 Summary: ${counts.folders} folders, ${counts.files} files`);
console.log('─'.repeat(60) + '\n');

// Ask for confirmation (optional - comment out if not needed)
console.log('⚠️  This will create the above structure in the current directory.');
console.log('📍 Current directory:', process.cwd());
console.log('\n💡 Press Ctrl+C to cancel, or wait 3 seconds to continue...\n');

setTimeout(() => {
  console.log('='.repeat(60));
  console.log('📝 Creating files and folders...\n');

  try {
    // Create the structure
    const baseDir = process.cwd();
    createStructure(baseDir, structure);

    console.log('\n' + '='.repeat(60));
    console.log('✨ SUCCESS! Folder structure created successfully!');
    console.log('='.repeat(60) + '\n');
    
    console.log('📋 Next Steps:\n');
    console.log('   1️⃣  Backend Setup:');
    console.log('      cd backend');
    console.log('      npm install express cors dotenv pg better-auth drizzle-orm');
    console.log('      npm install -D nodemon');
    console.log('');
    console.log('   2️⃣  Frontend Setup:');
    console.log('      cd frontend');
    console.log('      npx create-next-app@latest . --typescript --tailwind --app');
    console.log('');
    console.log('   3️⃣  Configure Environment:');
    console.log('      Edit .env files with your actual values');
    console.log('');
    console.log('   4️⃣  Start Development:');
    console.log('      Backend:  cd backend && npm run dev');
    console.log('      Frontend: cd frontend && npm run dev');
    console.log('\n🎉 Happy Coding!\n');
    
  } catch (error) {
    console.error('\n❌ ERROR:', error.message);
    console.log('\n💡 Tip: Make sure you have write permissions in this directory.\n');
  }
}, 3000);
```

---

## 📖 How It Works

### 1. **Structure Definition**
```javascript
const structure = {
  'folder-name': {
    'subfolder': {
      'file.js': 'file content here'
    }
  }
};
```

- **Object keys** = Folder/file names
- **String values** = File content
- **Object values** = Nested folders

### 2. **Recursive Creation**
Script recursively traverses the structure object and creates:
- **Folders** using `fs.mkdirSync()`
- **Files** using `fs.writeFileSync()`

### 3. **Visual Preview**
Before creating, displays a tree view of what will be created.

---

## 🎨 Customization

### Add New Folders/Files

```javascript
const structure = {
  'backend': {
    'src': {
      'services': {  // New folder
        'email.service.js': '// Email service code'
      }
    }
  }
};
```

### Change File Content

```javascript
'server.js': `// Your custom server code here
const express = require('express');
// ... rest of your code
`
```

### Skip Confirmation

Comment out the `setTimeout()` section and run immediately:

```javascript
// Remove or comment these lines:
// setTimeout(() => {
//   ...
// }, 3000);

// And directly call:
createStructure(process.cwd(), structure);
```

---

## 🔧 Advanced Usage

### Generate Structure for Multiple Projects

```javascript
const structures = {
  'ecommerce': { /* ecommerce structure */ },
  'blog': { /* blog structure */ },
  'dashboard': { /* dashboard structure */ }
};

// Select which one to create
const projectType = process.argv[2] || 'ecommerce';
createStructure(process.cwd(), structures[projectType]);
```

**Usage:**
```bash
node setup-structure.js blog
```

### Export Structure as JSON

```javascript
const structureJSON = JSON.stringify(structure, null, 2);
fs.writeFileSync('structure.json', structureJSON);
console.log('Structure exported to structure.json');
```

### Generate from Existing Project

```javascript
function scanDirectory(dir) {
  // Scan and create structure object from existing project
  // Useful for documentation
}
```

---

## 📊 Output Example

```
============================================================
🚀  FOLDER STRUCTURE GENERATOR
============================================================

📂 Folder Structure Preview:

├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   │   └── auth.controller.js
│   │   ├── db/
│   │   │   └── connection.js
│   │   ├── middlewares/
│   │   │   └── auth.middleware.js
│   │   ├── models/
│   │   │   └── user.model.js
│   │   ├── routes/
│   │   │   └── auth.routes.js
│   │   ├── utils/
│   │   ├── validations/
│   │   │   └── auth.validation.js
│   │   └── server.js
│   ├── .env
│   ├── .env.example
│   ├── .gitignore
│   └── package.json
├── frontend/
│   └── README.md
└── README.md

────────────────────────────────────────────────────────────
📊 Summary: 12 folders, 15 files
────────────────────────────────────────────────────────────

✨ SUCCESS! Folder structure created successfully!
```

---

## 🐛 Troubleshooting

### Error: EACCES (Permission Denied)
```bash
sudo node setup-structure.js
# Or change directory permissions
chmod +w .
```

### Error: File Already Exists
Script will overwrite existing files. Backup first if needed!

### Error: Cannot find module 'fs'
This is a Node.js built-in module. Make sure you're running Node.js v14+

---

## 💡 Pro Tips

1. **Version Control:** Add this script to your project templates
2. **Documentation:** Use the tree output for README.md
3. **CI/CD:** Integrate in automated project setup pipelines
4. **Team Onboarding:** Share with new developers for quick setup
5. **AI Prompts:** Copy tree output to show AI your project structure

---

## 📚 Use Cases in Detail

### 1. Quick Project Setup
```bash
mkdir my-new-project
cd my-new-project
node setup-structure.js
```

### 2. Show Structure to AI
```bash
node setup-structure.js > structure.txt
# Share structure.txt with AI
```

### 3. Documentation
```bash
# Copy the tree output to your README.md
```

### 4. Multiple Environments
```javascript
const structures = {
  dev: { /* development structure */ },
  prod: { /* production structure */ }
};
```

---

## 🎓 Learning Resources

- [Node.js fs Module](https://nodejs.org/api/fs.html)
- [Path Module](https://nodejs.org/api/path.html)
- [Project Structure Best Practices](https://github.com/goldbergyoni/nodebestpractices)

---

## 🤝 Contributing

Found a bug or want to add a feature?
1. Fork this gist
2. Make your changes
3. Share your improvements!

---

## 📄 License

MIT License - Free to use and modify!

---

## ✨ Credits

**Made with ❤️ by Taha**

Feel free to customize and share! 🚀

---

## 📞 Support

Agar koi issue ho to:
1. Check the troubleshooting section
2. Verify Node.js version (`node --version`)
3. Check file permissions
4. Try running in a fresh directory

Happy Coding! 🎉

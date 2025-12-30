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



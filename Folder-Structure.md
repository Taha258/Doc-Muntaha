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

// Ignore list (folders/files jo skip karne hain)
const IGNORE_LIST = [
  'node_modules',
  '.git',
  '.next',
  'dist',
  'build',
  '.DS_Store',
  'package-lock.json',
  'yarn.lock',
  'pnpm-lock.yaml',
  '.env.local',
  '.env.production',
  'coverage'
];

// Check if path should be ignored
function shouldIgnore(itemName) {
  return IGNORE_LIST.some(ignored => itemName.includes(ignored));
}

// Get file size in human readable format
function getFileSize(filePath) {
  try {
    const stats = fs.statSync(filePath);
    const bytes = stats.size;
    if (bytes === 0) return '(empty)';
    if (bytes < 1024) return `(${bytes}B)`;
    if (bytes < 1024 * 1024) return `(${(bytes / 1024).toFixed(1)}KB)`;
    return `(${(bytes / (1024 * 1024)).toFixed(1)}MB)`;
  } catch (err) {
    return '';
  }
}

// Scan directory and build structure
function scanDirectory(dirPath, relativePath = '') {
  const structure = {};
  
  try {
    const items = fs.readdirSync(dirPath);
    
    items.forEach(item => {
      if (shouldIgnore(item)) return;
      
      const fullPath = path.join(dirPath, item);
      const relPath = path.join(relativePath, item);
      const stats = fs.statSync(fullPath);
      
      if (stats.isDirectory()) {
        // It's a folder - recursively scan it
        structure[item] = scanDirectory(fullPath, relPath);
      } else {
        // It's a file - store size info
        structure[item] = getFileSize(fullPath);
      }
    });
  } catch (err) {
    console.error(`Error reading directory ${dirPath}:`, err.message);
  }
  
  return structure;
}

// Display tree structure with colors
function displayTree(struct, prefix = '', isRoot = true, isLast = true) {
  const keys = Object.keys(struct);
  const totalKeys = keys.length;
  
  keys.forEach((key, index) => {
    const isLastItem = index === totalKeys - 1;
    const value = struct[key];
    
    // Tree characters
    const connector = isLastItem ? '└── ' : '├── ';
    const extension = isLastItem ? '    ' : '│   ';
    
    if (typeof value === 'string') {
      // It's a file
      console.log(`${prefix}${connector}📄 ${key} ${value}`);
    } else if (typeof value === 'object') {
      // It's a folder
      const folderIcon = Object.keys(value).length === 0 ? '📂' : '📁';
      console.log(`${prefix}${connector}${folderIcon} ${key}/`);
      displayTree(value, prefix + extension, false, isLastItem);
    }
  });
}

// Count files and folders
function countItems(struct) {
  let files = 0;
  let folders = 0;
  
  Object.keys(struct).forEach(key => {
    const value = struct[key];
    if (typeof value === 'string') {
      files++;
    } else if (typeof value === 'object') {
      folders++;
      const childCounts = countItems(value);
      files += childCounts.files;
      folders += childCounts.folders;
    }
  });
  
  return { files, folders };
}

// Export structure to JSON file
function exportToJSON(structure, outputPath = 'structure.json') {
  try {
    fs.writeFileSync(outputPath, JSON.stringify(structure, null, 2), 'utf8');
    console.log(`\n💾 Structure exported to: ${outputPath}`);
  } catch (err) {
    console.error('Error exporting JSON:', err.message);
  }
}

// Generate code to recreate structure
function generateCreationCode(struct, indent = 0) {
  let code = '';
  const spaces = '  '.repeat(indent);
  
  Object.keys(struct).forEach(key => {
    const value = struct[key];
    
    if (typeof value === 'string') {
      // File
      code += `${spaces}'${key}': '',\n`;
    } else if (typeof value === 'object') {
      // Folder
      code += `${spaces}'${key}': {\n`;
      code += generateCreationCode(value, indent + 1);
      code += `${spaces}},\n`;
    }
  });
  
  return code;
}

// Main execution
console.log('\n' + '='.repeat(70));
console.log('📂 FOLDER STRUCTURE SCANNER');
console.log('='.repeat(70) + '\n');

// Get target directory (default: current directory)
const targetDir = process.argv[2] || process.cwd();
const projectName = path.basename(targetDir);

console.log(`📍 Scanning: ${targetDir}\n`);
console.log('⏳ Please wait...\n');

// Scan the directory
const structure = scanDirectory(targetDir);

// Display tree
console.log('='.repeat(70));
console.log(`\n📂 PROJECT STRUCTURE: ${projectName}\n`);
console.log(`${projectName}/`);
displayTree(structure);

// Count statistics
const counts = countItems(structure);
console.log('\n' + '='.repeat(70));
console.log('\n📊 STATISTICS:\n');
console.log(`   📁 Total Folders: ${counts.folders}`);
console.log(`   📄 Total Files: ${counts.files}`);
console.log(`   📦 Total Items: ${counts.files + counts.folders}`);

// Export options
console.log('\n' + '='.repeat(70));
console.log('\n💡 EXPORT OPTIONS:\n');
console.log('1️⃣  Export to JSON:');
console.log(`    node scan-structure.js ${targetDir === process.cwd() ? '' : targetDir} --json\n`);
console.log('2️⃣  Export creation code:');
console.log(`    node scan-structure.js ${targetDir === process.cwd() ? '' : targetDir} --code\n`);

// Handle export flags
if (process.argv.includes('--json')) {
  exportToJSON(structure, 'structure.json');
}

if (process.argv.includes('--code')) {
  console.log('\n📝 STRUCTURE CREATION CODE:\n');
  console.log('const structure = {');
  console.log(generateCreationCode(structure, 1));
  console.log('};\n');
}

console.log('='.repeat(70));
console.log('\n✨ Scan complete! 🎉\n');
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
# One More Copy File Structure 
```
#!/usr/bin/env node

const fs = require('fs');
const path = require('path');

/**
 * HARD BLOCK LIST
 * — yeh folders/files kabhi scan nahi honge
 */
const IGNORE_NAMES = new Set([
  // Node
  'node_modules',
  '.next',
  'dist',
  'build',
  'coverage',

  // Git
  '.git',

  // Python (IMPORTANT)
  '__pycache__',
  '.venv',
  'venv',
  'Lib',
  'Include',
  'Scripts',
  'site-packages',

  // Env / lock
  '.env',
  '.env.local',
  '.env.production',
  'package-lock.json',
  'yarn.lock',
  'pnpm-lock.yaml',

  // OS
  '.DS_Store'
]);

/**
 * Decide whether to ignore an item
 */
function shouldIgnore(name, fullPath) {
  // Exact name ignore
  if (IGNORE_NAMES.has(name)) return true;

  // Python compiled files
  if (name.endsWith('.pyc')) return true;

  // Any python internal path (extra safety)
  if (fullPath.includes('site-packages')) return true;
  if (fullPath.includes('__pycache__')) return true;

  return false;
}

/**
 * Human-readable file size
 */
function getFileSize(filePath) {
  try {
    const bytes = fs.statSync(filePath).size;
    if (bytes === 0) return '(empty)';
    if (bytes < 1024) return `(${bytes}B)`;
    if (bytes < 1024 * 1024) return `(${(bytes / 1024).toFixed(1)}KB)`;
    return `(${(bytes / (1024 * 1024)).toFixed(1)}MB)`;
  } catch {
    return '';
  }
}

/**
 * Recursively scan directory
 */
function scanDirectory(dirPath) {
  const structure = {};

  let items;
  try {
    items = fs.readdirSync(dirPath);
  } catch {
    return structure;
  }

  for (const item of items) {
    const fullPath = path.join(dirPath, item);

    if (shouldIgnore(item, fullPath)) continue;

    let stats;
    try {
      stats = fs.statSync(fullPath);
    } catch {
      continue;
    }

    if (stats.isDirectory()) {
      const child = scanDirectory(fullPath);

      // ❌ empty folders skip
      if (Object.keys(child).length > 0) {
        structure[item] = child;
      }
    } else {
      structure[item] = getFileSize(fullPath);
    }
  }

  return structure;
}

/**
 * Pretty tree output
 */
function displayTree(struct, prefix = '') {
  const entries = Object.entries(struct);

  entries.forEach(([name, value], index) => {
    const isLast = index === entries.length - 1;
    const connector = isLast ? '└── ' : '├── ';
    const nextPrefix = prefix + (isLast ? '    ' : '│   ');

    if (typeof value === 'string') {
      console.log(`${prefix}${connector}📄 ${name} ${value}`);
    } else {
      console.log(`${prefix}${connector}📁 ${name}/`);
      displayTree(value, nextPrefix);
    }
  });
}

/**
 * MAIN
 */
const targetDir = process.argv[2];

if (!targetDir) {
  console.error('\n❌ ERROR: folder name do');
  console.error('👉 Example: node scan-structure.js backend\n');
  process.exit(1);
}

const absPath = path.resolve(targetDir);

if (!fs.existsSync(absPath)) {
  console.error('\n❌ ERROR: folder exist nahi karta\n');
  process.exit(1);
}

console.log('\n📂 PROJECT STRUCTURE\n');
console.log(`${path.basename(absPath)}/`);

const tree = scanDirectory(absPath);
displayTree(tree);

console.log('\n✅ Scan complete\n');

```
## Run Command Above Script
```
node scan-structure.js .

```



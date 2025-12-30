## 📦 Project Code Export Guide

Is guide ka purpose poore project ka **important code ek hi file** mein export karna hai,  
bina **sensitive** ya **unnecessary files** ke.

---

## ❌ Excluded Folders

Yeh folders automatically ignore ho jaate hain:

- node_modules
- .git
- .next
- dist

---

## ❌ Excluded Files

Yeh files export nahi hoti:

- .env
- package.json
- package-lock.json
- .gitignore
- dump-code.js

---

## ✅ Allowed File Types

Sirf yeh extensions wali files export hoti hain:

- `.js`
- `.ts`
- `.py`
- `.md`

---

## 📝 all_file_code.js File Banao

```
import fs from "fs";
import path from "path";

const ROOT_DIR = process.cwd();
const OUTPUT_FILE = "project_code.txt";

// ❌ folders to ignore
const IGNORE_FOLDERS = [
  "node_modules",
  ".git",
  ".next",
  "dist"
];

// ❌ files to ignore (exact names)
const IGNORE_FILES = [
  ".env",
  "package.json",
  "package-lock.json",
  ".gitignore",
  "dump-code.js" 
];

// ✅ allowed file extensions
const ALLOWED_EXT = [
  ".js",
  ".ts",
  ".py",
  ".md"
];

function walkDir(dir, output) {
  const items = fs.readdirSync(dir);

  for (const item of items) {
    const fullPath = path.join(dir, item);
    const stat = fs.statSync(fullPath);

    if (stat.isDirectory()) {
      if (!IGNORE_FOLDERS.includes(item)) {
        walkDir(fullPath, output);
      }
    } else {
      const ext = path.extname(item);

      if (
        !IGNORE_FILES.includes(item) &&
        ALLOWED_EXT.includes(ext)
      ) {
        const relativePath = path.relative(ROOT_DIR, fullPath);

        output.push(
          `\n//================== ${relativePath}\n`
        );

        const content = fs.readFileSync(fullPath, "utf-8");
        output.push(content);
      }
    }
  }
}

// run script
const output = [];
walkDir(ROOT_DIR, output);

fs.writeFileSync(OUTPUT_FILE, output.join("\n"));
console.log(`✅ Code safely exported to ${OUTPUT_FILE}`);

```
▶️ Step 3: Script Run Karo
```
node all_file_code.js
```
#📄 Output
## project_code.txt file generate ho jayegi
```
//================== routes/index.js
(code here)

```


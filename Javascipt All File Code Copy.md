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

## 📝 Step 1: Script File Banao

Project ke **root folder** mein ek nayi file banao:

```bash
all_file_code.js


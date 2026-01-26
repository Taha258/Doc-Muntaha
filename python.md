Done 👍
Neeche **tumhari hi language + clean Markdown notes** bana di hain — exam / revision friendly 😄

---

# 🐍 Python Basics – Short Notes (Markdown)

---

## 🔹 Interpreter Language

* Python **interpreted language** hai
* Line by line code execute hota hai
* Compile pehle nahi hota, run time par hota hai

---

## 🔹 `.pyc` File

* Python source code ka **bytecode** hota hai
* Faster execution ke liye use hota hai
* Automatically create hoti hai

---

## 🔹 Numeric Types

* `int` → whole number
* `float` → decimal number
* `complex` → real + imaginary ( `3 + 4j` )

---

## 🔹 Sequence Types

* `str`
* `list`
* `tuple`

---

## 🔹 List

* **Mutable** (change ho sakti hai)
* Value **reassign** kar sakte hain
* **Duplicate values allowed**
* Index hota hai

```python
a = [1, 2, 2, 3]
a[0] = 10
```

---

## 🔹 Tuple

* **Immutable** (change nahi hoti)
* Order hota hai
* Reassign **nahi** hota
* Duplicate allowed
* Index fix hota hai
* Value ek dafa set ho jaye to change nahi hoti

```python
t = (1, 2, 3)
# t[0] = 10 ❌
```

---

## 🔹 Set

* **Unordered**
* **Duplicate allowed nahi**
* Mutable hai (add / remove)
* Index / order fix nahi hota
* Reassign nahi hoti, sirf modify hoti hai

```python
s = {1, 2, 3}
s.add(4)
s.remove(2)
```

> Print karte waqt koi bhi value pehle aa sakti hai

---

## 🔹 Mapping Type (Dictionary)

* Key : Value pair
* Mutable
* Key unique hoti hai

```python
d = {"a": 1, "b": 2}
```

---

## 🔹 Integer Memory Cache

* Python **-5 to 256** tak ke integers same memory mein rakhta hai
* Performance optimize karne ke liye

---

## 🔹 Type Casting

* Ek data type ko doosri data type mein convert karna

### ✔ Permanent

```python
i = str(i)
```

### ✔ Temporary

```python
str(i)
```

---

## 🔹 Implicit Type Casting

* Python **khud** type convert karta hai

```python
i = 10      # int
j = 20.6    # float
f = i + j   # int → float
```

---

## 🔹 Explicit Type Casting

* User **khud** type change karta hai

```python
x = int("10")
y = float("5.6")
```

---

## 🔹 NOT Operator

* Value ko opposite bana deta hai

```python
not True   # False
```

---

## 🔹 Operator & Operand

* **Operator** → +, -, *, /
* **Operand** → values

```python
5 + 2
```

---

## 🔹 Formula

```python
-(x + 1)
```

---

## 🔹 Floor Division

* Decimal hata deta hai

```python
5 // 2   # 2
```

---

## 🔹 Identity Operator

* Memory location check karta hai

```python
a is b   # True / False
```

---

## 🔹 Membership Operator

* Value exist karti hai ya nahi

```python
"a" in "apple"
```

---

## 🔹 Keywords

* Python ke **reserved words**

```python
import keyword
print(keyword.kwlist)
```

---

## 🔹 del Keyword

* Variable delete karta hai

```python
del x
```

---

Agar chaho to:

* 📄 **PDF bana doon**
* 🧠 **MCQs + tricks**
* 🎯 **Interview one-liners**

bas bolo 🔥

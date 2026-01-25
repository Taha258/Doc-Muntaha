Perfect 👍
Main **ek complete Markdown (`.md`) file** bana raha hoon — **simple, clean, ek hi flow me**,
aur **tumhara jo point hai woh bilkul tumhari language me add** kar raha hoon ✨

Tum isko **direct GitHub / VS Code / Notion / MD file** me paste kar sakte ho.

---

````md
# OOP (Object Oriented Programming) – Complete Notes (Simple Language)

---

## new keyword

`new` keyword ka use **class ka object (instance)** banane ke liye hota hai.

```ts
const acc1 = new BankAccount(1000);
````

* `acc1` → object / instance
* constructor automatically call hota hai

👉 **instance = object (dono ek hi cheez hain)**

---

## Constructor

* Constructor class ke andar hota hai
* Object bante hi run hota hai
* Instance variables ko initial value dene ke liye use hota hai

```ts
class BankAccount {
  private balance: number;

  constructor(balance: number) {
    this.balance = balance;
  }
}
```

---

## Instance Variable

* Object ke sath attach hota hai
* Har object ki **apni alag value** hoti hai
* Mostly constructor ke through set hota hai

```ts
private balance: number;
```

---

## Class Variable (Static Variable)

* `static` keyword se banta hai
* **Sab objects ke liye same hota hai**
* Object ke sath nahi, **class ke sath attach hota hai**

```ts
class Bank {
  static bankName = "My Bank";
}
```

👉 **Class variable ko bahar access kar sakhta ho without object banaye**

```ts
console.log(Bank.bankName);
```

---

## Instance Variable vs Class Variable

* **Instance variable** → object ke liye
* **Class variable (Static)** → sab objects ke liye same

---

## Static Method

### Static Method ka Rule

* Static method = **Class method**
* Object ke sath nahi, **direct class se call hota hai**
* Mostly **static variables** ke sath kaam karta hai
* Instance variables ko directly access nahi kar sakta

```ts
class Bank {
  static bankName = "My Bank";

  static getBankName() {
    return Bank.bankName;
  }
}
```

```ts
Bank.getBankName(); // ✔️
```

❌ Object se call nahi hota:

```ts
const b = new Bank();
b.getBankName(); // ❌
```

---

## Class Method vs Instance Method

* **Instance Method** → object ke sath call hota hai
* **Class Method (Static)** → class ke sath call hota hai

---

## Access Modifiers

### Private Variable ka Rule

Agar ek class ke andar **private variable** hai
aur koi dusri class usse **inherit** kar rahi hai (child class)

👉 **Child class us private variable ko access nahi kar sakti**

```ts
private balance: number;
```

---

### Protected Variable

* Class ke andar ✔️
* Child class me ✔️
* Class ke bahar ❌

👉 Private se **thoda relaxed** hai
👉 Inheritance me kaam aata hai

```ts
protected accountNumber: number;
```

> Protected variable inheritance to ho sakhta hai
> magar agar dusri class jis ke andar inheritance hui ho
> woh bhi use bahar use karna chahe
> **to use nahi kar sakhti**

---

### Public Variable / Method

* Class ke andar ✔️
* Child class me ✔️
* Class ke bahar ✔️

👉 Sab jagah access ho sakta hai

---

## Encapsulation

**Definition:**

> Data hide karna + safe access dena

* Private / Protected variables
* Public methods
* Getters & Setters

```ts
class Account {
  private balance: number;

  getBalance() {
    return this.balance;
  }
}
```

---

## Inheritance

**Definition:**

> Parent class ka code reuse karna

```ts
class Vehicle {
  start() {
    console.log("Vehicle started");
  }
}

class Car extends Vehicle {}
```

---

## super()

Jab hum **Child class ka object** banate hain,

👉 Parent class ka constructor automatically run nahi hota

Isliye `super()` ka use hota hai

```ts
class Parent {
  constructor(name: string) {}
}

class Child extends Parent {
  constructor(name: string) {
    super(name);
  }
}
```

---

## Abstraction

**Definition:**

> Only essential details show, unnecessary hide

* Abstract class
* Interface

### Important Rule

👉 Abstract class jis class me inherit hogi
👉 **Us class ko abstract class ke sare methods banana lazmi hoga**

```ts
abstract class Vehicle {
  abstract start(): void;
}
```

```ts
class Car extends Vehicle {
  start(): void {
    console.log("Car engine started");
  }
}
```

---

### Tumhara Example (Client wali story)

Client aaya aur bola:

> “Bhai mujhe falani website jaisi website chahiye
> — login ho
> — authentication ho
> — cards ho
> — buttons ho
> — pages ho
> lekin mujhe yeh nahi pata ke andar backend ka logic kya hai”

👉 **YEH ABSTRACTION HAI**

Client ko sirf **features pata hain**,
andar ka logic hide hai.

---

## Polymorphism

**Definition:**

> Same interface, multiple forms

### Example

| Vehicle | Result              |
| ------- | ------------------- |
| Car     | Car engine started  |
| Bike    | Bike engine started |
| Bus     | Bus engine started  |

```ts
class Vehicle {
  start() {}
}

class Car extends Vehicle {
  start() {
    console.log("Car engine started");
  }
}
```

---

## OOP Summary Table

| Concept       | Focus                                         | Example                                                   |
| ------------- | --------------------------------------------- | --------------------------------------------------------- |
| Encapsulation | Data hiding + safe access                     | Private / Protected / Public variables, getters & setters |
| Inheritance   | Code reuse                                    | Child class inherits from parent class                    |
| Abstraction   | Only essential details show, unnecessary hide | Abstract class, interface                                 |
| Polymorphism  | Same interface, multiple forms                | Method overriding, method overloading                     |

---

```

---

Agar chaho next:
- 📌 **Interview version (short & sharp)**
- 📌 **Only TypeScript examples**
- 📌 **Diagram + real-world mapping**
- 📌 **MCQs (tumhari purani preference 👀)**

Bas bol do 👍
```

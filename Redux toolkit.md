# Complete Redux Toolkit Guide with Next.js

## Installation

```bash
npm install @reduxjs/toolkit react-redux
```

---

## File Structure

```
my-app/
├── src/
│   ├── app/
│   │   ├── layout.js
│   │   └── page.js
│   │
│   └── redux/
│       ├── store.js
│       ├── provider.js
│       │
│       └── features/
│           ├── counter/
│           │   └── counterSlice.js
│           │
│           └── user/
│               └── userSlice.js
```

---

## Core Files

### 1. store.js (Main Store)
```javascript
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './features/counter/counterSlice';
import userReducer from './features/user/userSlice';

export const store = configureStore({
  reducer: {
    counter: counterReducer,
    user: userReducer,
  },
});
```

### 2. provider.js (Redux Provider)
```javascript
'use client';
import { Provider } from 'react-redux';
import { store } from './store';

export function ReduxProvider({ children }) {
  return <Provider store={store}>{children}</Provider>;
}
```

### 3. counterSlice.js (Example Slice)
```javascript
import { createSlice } from '@reduxjs/toolkit';

const initialState = {
  value: 0,
};

export const counterSlice = createSlice({
  name: 'counter',
  initialState,
  reducers: {
    increment: (state) => {
      state.value += 1;
    },
    decrement: (state) => {
      state.value -= 1;
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload;
    },
    reset: (state) => {
      state.value = 0;
    },
  },
});

export const { increment, decrement, incrementByAmount, reset } = counterSlice.actions;
export default counterSlice.reducer;
```

### 4. layout.js (Wrap App)
```javascript
import { ReduxProvider } from '@/redux/provider';

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>
        <ReduxProvider>
          {children}
        </ReduxProvider>
      </body>
    </html>
  );
}
```

### 5. page.js (Use in Component)
```javascript
'use client';
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement, incrementByAmount } from '@/redux/features/counter/counterSlice';

export default function HomePage() {
  const count = useSelector((state) => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={() => dispatch(increment())}>Increment</button>
      <button onClick={() => dispatch(decrement())}>Decrement</button>
      <button onClick={() => dispatch(incrementByAmount(5))}>Add 5</button>
    </div>
  );
}
```

---

## Core Concepts

### What is State?
```javascript
// Global data storage
{
  counter: { value: 0 },
  user: { name: "John", age: 25 }
}
```

### What is an Action?
```javascript
// Event/Message that tells what to do
{ type: 'counter/increment' }
{ type: 'counter/decrement' }
{ type: 'user/setName', payload: "Ali" }
```

### What is a Reducer?
```javascript
// Function that updates state based on action
function counterReducer(state, action) {
  switch(action.type) {
    case 'increment':
      return { value: state.value + 1 };
    default:
      return state;
  }
}
```

### What is a Slice?
A complete package that contains:
- Initial state
- Reducer functions
- Action creators
All in one file using `createSlice()`

---

## How to Use

### Step 1: Create a Slice
```javascript
// features/todo/todoSlice.js
import { createSlice } from '@reduxjs/toolkit';

const todoSlice = createSlice({
  name: 'todos',
  initialState: [],
  reducers: {
    addTodo: (state, action) => {
      state.push(action.payload);
    },
    removeTodo: (state, action) => {
      return state.filter(todo => todo.id !== action.payload);
    },
  },
});
```

### Step 2: Register in Store
```javascript
// store.js
import todoReducer from './features/todo/todoSlice';

export const store = configureStore({
  reducer: {
    todos: todoReducer,
  },
});
```

### Step 3: Use in Component
```javascript
// Component.js
'use client';
import { useSelector, useDispatch } from 'react-redux';
import { addTodo } from '@/redux/features/todo/todoSlice';

function TodoComponent() {
  const todos = useSelector((state) => state.todos);
  const dispatch = useDispatch();
  
  const handleAdd = () => {
    dispatch(addTodo({ id: 1, text: 'Learn Redux' }));
  };
  
  return (
    <div>
      <button onClick={handleAdd}>Add Todo</button>
      {todos.map(todo => <div key={todo.id}>{todo.text}</div>)}
    </div>
  );
}
```

---

## Async Operations with createAsyncThunk

### Create Async Slice
```javascript
import { createSlice, createAsyncThunk } from '@reduxjs/toolkit';

export const fetchUsers = createAsyncThunk(
  'users/fetchUsers',
  async () => {
    const response = await fetch('https://api.example.com/users');
    return response.json();
  }
);

const userSlice = createSlice({
  name: 'users',
  initialState: {
    data: [],
    loading: false,
    error: null,
  },
  extraReducers: (builder) => {
    builder
      .addCase(fetchUsers.pending, (state) => {
        state.loading = true;
      })
      .addCase(fetchUsers.fulfilled, (state, action) => {
        state.loading = false;
        state.data = action.payload;
      })
      .addCase(fetchUsers.rejected, (state, action) => {
        state.loading = false;
        state.error = action.error.message;
      });
  },
});
```

### Use Async Action
```javascript
function UsersComponent() {
  const dispatch = useDispatch();
  const { data, loading, error } = useSelector((state) => state.users);
  
  useEffect(() => {
    dispatch(fetchUsers());
  }, [dispatch]);
  
  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;
  
  return (
    <div>
      {data.map(user => <div key={user.id}>{user.name}</div>)}
    </div>
  );
}
```

---

## Common Patterns

### 1. Selector Functions
```javascript
// selectors.js
export const selectCount = (state) => state.counter.value;
export const selectUser = (state) => state.user.data;

// In component
const count = useSelector(selectCount);
const user = useSelector(selectUser);
```

### 2. Payload Action
```javascript
// In slice
reducers: {
  setUser: (state, action) => {
    state.name = action.payload.name;
    state.age = action.payload.age;
  },
}

// In component
dispatch(setUser({ name: 'Ali', age: 25 }));
```

### 3. Reset State
```javascript
reducers: {
  resetState: () => initialState,
}
```

---

## Rules to Remember

1. **Slices are features** - One slice per feature
2. **Client components only** - Use `'use client'` with Redux hooks
3. **Direct mutation allowed** - Thanks to Immer in Redux Toolkit
4. **One store per app** - ConfigureStore creates single store
5. **Provider wraps everything** - In layout.js

---

## Quick Reference

| Term | What it does | Example |
|------|--------------|---------|
| **Store** | Holds global state | `configureStore()` |
| **Slice** | Feature logic package | `createSlice()` |
| **Reducer** | Updates state | `(state) => state.value++` |
| **Action** | Event description | `{type: 'increment'}` |
| **Dispatch** | Sends action | `dispatch(increment())` |
| **Selector** | Gets data from store | `useSelector(state => state.value)` |
| **Payload** | Extra data with action | `dispatch(addTodo({text: '...'}))` |

---

## Troubleshooting

### Problem: "No store found"
**Solution:** Make sure Provider wraps your app in layout.js

### Problem: Hooks not working
**Solution:** Add `'use client'` at top of component file

### Problem: State not updating
**Solution:** Check if reducer is properly defined in slice

### Problem: Type errors
**Solution:** Use TypeScript or check action payload types

---

## Best Practices

1. **Keep state minimal** - Only store what's needed globally
2. **Use createEntityAdapter** - For normalized data (todos, users, products)
3. **Memoize selectors** - With `createSelector` for performance
4. **Split logic** - Separate slices for different features
5. **Use Redux DevTools** - For debugging (automatically included)

---

## Example: Complete Shopping Cart

### cartSlice.js
```javascript
import { createSlice } from '@reduxjs/toolkit';

const cartSlice = createSlice({
  name: 'cart',
  initialState: {
    items: [],
    total: 0,
  },
  reducers: {
    addItem: (state, action) => {
      state.items.push(action.payload);
      state.total += action.payload.price;
    },
    removeItem: (state, action) => {
      const item = state.items.find(item => item.id === action.payload);
      state.items = state.items.filter(item => item.id !== action.payload);
      state.total -= item.price;
    },
    clearCart: (state) => {
      state.items = [];
      state.total = 0;
    },
  },
});
```

### CartComponent.js
```javascript
'use client';
import { useSelector, useDispatch } from 'react-redux';
import { addItem, removeItem } from '@/redux/features/cart/cartSlice';

export default function Cart() {
  const cart = useSelector((state) => state.cart);
  const dispatch = useDispatch();
  
  return (
    <div>
      <h2>Cart Total: ${cart.total}</h2>
      <button onClick={() => dispatch(addItem({ id: 1, name: 'Product', price: 10 }))}>
        Add Product
      </button>
      {cart.items.map(item => (
        <div key={item.id}>
          {item.name} - ${item.price}
          <button onClick={() => dispatch(removeItem(item.id))}>Remove</button>
        </div>
      ))}
    </div>
  );
}
```

---

## Final Notes

*Redux Toolkit simplifies traditional Redux by:*
- **Less boilerplate** - No action types, action creators separately
- **Direct state mutation** - Immer handles immutability
- **Built-in thunk** - Async logic support
- **DevTools integration** - Debugging made easy

*Start with:*
1. Create store.js
2. Create provider.js  
3. Create your first slice
4. Wrap app with Provider
5. Use useSelector and useDispatch

Practice with a counter, then move to todos, then to API calls with createAsyncThunk!

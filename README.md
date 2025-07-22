
# 📘 React Hooks Cheat Sheet with Examples

React Hooks let you use state and other React features without writing a class.
Below is a list of the most commonly used built-in hooks in React.

---

## 🔹 1. useState 🛠️
Allows you to add state to functional components.

```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
```

---

## 🔹 2. useEffect ⚡
Performs side effects in function components (e.g., data fetching, subscriptions).

```jsx
import { useEffect, useState } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => setSeconds(s => s + 1), 1000);
    return () => clearInterval(interval); // Cleanup
  }, []); // Empty dependency array = run once on mount

  return <p>Seconds: {seconds}</p>;
}
```

---

## 🔹 3. useContext 🌐
Accesses context values directly inside a functional component.

```jsx
import { useContext } from 'react';
import { ThemeContext } from './ThemeContext';

function ThemedComponent() {
  const theme = useContext(ThemeContext);

  return <div style={{ background: theme.background }}>Hello</div>;
}
```

---

## 🔹 4. useRef 🎯
Creates a mutable reference that persists across renders.

```jsx
import { useRef, useEffect } from 'react';

function InputFocus() {
  const inputRef = useRef();

  useEffect(() => {
    inputRef.current.focus();
  }, []);

  return <input ref={inputRef} placeholder="Focus me" />;
}
```

---

## 🔹 5. useReducer 🎛️
Manages more complex state logic using a reducer function.

```jsx
import { useReducer } from 'react';

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <button onClick={() => dispatch({ type: 'increment' })}>
      Count: {state.count}
    </button>
  );
}
```

---

## 🔹 6. useMemo 🧠
Memoizes expensive calculations so they only re-run when needed.

```jsx
import { useMemo, useState } from 'react';

function ExpensiveComponent({ number }) {
  const factorial = useMemo(() => {
    let result = 1;
    for (let i = 1; i <= number; i++) {
      result *= i;
    }
    return result;
  }, [number]);

  return <p>Factorial: {factorial}</p>;
}
```

---

## 🔹 7. useCallback 🔁
Returns a memoized version of the callback function.

```jsx
import { useCallback, useState } from 'react';

function Parent() {
  const [count, setCount] = useState(0);

  const increment = useCallback(() => {
    setCount(c => c + 1);
  }, []);

  return <Child onClick={increment} />;
}

function Child({ onClick }) {
  return <button onClick={onClick}>Click me</button>;
}
```

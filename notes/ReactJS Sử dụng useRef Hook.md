---
title: 'React: Sử dụng useRef Hook'
date: '2021-01-19'
type: programing 
---

# ReactJS Sử dụng useRef Hook

## Cú pháp useRef
` const nameRef = React.useRef(default_value)`

Ví dụ : 

```jsx
function Counter() {
  const [count, setCount] = React.useState(0);
  const id = React.useRef(null);

  const clearInterval = () => {
    window.clearInterval(id.current);
  };

  React.useEffect(() => {
    id.current = window.setInterval(() => {
      setCount((c) => c + 1);
    }, 1000);

    return clearInterval;
  }, []);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={clearInterval}>Stop</button>
    </div>
  );
}
```

### Hàm `useRef` nhận tham số gì ?
Hàm `useRef` chỉ nhận 1 tham số đầu vào, tham số đó là giá trị khởi tạo ban đầu. Nó có thể là 1 giá trị bất kỳ. 

### Hàm useState trả về cái gì? 
Hàm `useRef` trả về 1 giá trị hiện tại của biến qua các lần re-render.

### Dùng `useRef` truy xuất tới DOM
Ví dụ : Sử dụng `useRef` để focus input

```jsx
function Form() {
  const nameRef = React.useRef();
  const emailRef = React.useRef();
  const passwordRef = React.useRef();

  const handleSubmit = (e) => {
    e.preventDefault();

    const name = nameRef.current.value;
    const email = emailRef.current.value;
    const password = passwordRef.current.value;

    console.log(name, email, password);
  };

  return (
    <React.Fragment>
      <label>
        Name:
        <input placeholder="name" type="text" ref={nameRef} />
      </label>
      <label>
        Email:
        <input placeholder="email" type="text" ref={emailRef} />
      </label>
      <label>
        Password:
        <input placeholder="password" type="text" ref={passwordRef} />
      </label>

      <hr />

      <button onClick={() => nameRef.current.focus()}>Focus Name Input</button>
      <button onClick={() => emailRef.current.focus()}>
        Focus Email Input
      </button>
      <button onClick={() => passwordRef.current.focus()}>
        Focus Password Input
      </button>

      <hr />

      <button onClick={handleSubmit}>Submit</button>
    </React.Fragment>
  );
}
```

---
Tags: [[ReactJS]]
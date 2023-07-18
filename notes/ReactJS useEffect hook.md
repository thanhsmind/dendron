---
title: 'useEffect: Tương tác với vòng đời của components'
date: '2021-01-19'
type: programing
---

# ReactJS useEffect hook

## Mục đích sử dụng
Khi thực hiện lấy data, đăng ký, hay thay đổi DOM thủ công từ React components. Các hoạt động này sẽ gây ra ảnh hưởng tới các components khác, các hoạt động đó là  ==side effects== hay thường được gọi là ==effect==. 

**useEffect** thường phục vụ các mục đích: 
- componentDidMount
- componentDidUpdate
- componentWillUnmount

## Cú pháp
```javascript
import React, { useState, useEffect } from 'react';

function Example(){
	const [count, setCount] = useState(0);
	
	// Tương tự các componentDidMount và componentDidUpdate:
	useEffect(() => {
		// Cập nhật document title sử dụng browser API
		document.title = `You clicked ${count} times`;
	});
	
	return (
		<div>
			<p>You clicked {count} times</p>
			<button onClick={() => setCount(count+1)}>
				Click me
			</button>
		</div>
	);
}
```

### useEffect hoạt động thế nào ? 
`useEffect` là cách thông báo với React rằng compoent cần thực hiện 1 tác vụ gì đó sau khi render. React sẽ ghi nhớ lại hàm được truyền vào trong hàm `useEffect`, hàm này(thường được gọi chung là 1 *effect* ) sẽ được gọi lại khi DOM update xong. 
### Tại sao `useEffect` lại được gọi bên trong function component?
`useEffect` được đặt bên trong function component cho phép có thể truy xuất tới tất cả các props của function component. Hook tận dụng Javascript closures để có thể truy xuất dễ dàng.
### `useEffect` chạy sau tất cả những lần render?
Hàm được khai báo trong `useEffect` mặc định sẽ được chay sau lần render đầu tiên và mỗi lần update của component. 

## Effect cần phải Cleanup
1 vài Effect đòi hỏi cần phải cleanup DOM trước khi thay đổi data. 
```javascript
import React, { useState, useEffect } from 'react'

function FriendStatus(props){
	const [isOnline, setIsOnline] = useState(null);
	
	useEffect(() => {
		function handleStateChange(status){
			setIsOnline(status.isOnline);
		}
		ChatAPI.subcribleToFriendStatus(props.friend.id, handleStatusChange);
		
		// Chỉ định sẽ gọi hàm này cleanup sau khi gọi effect:
		return function cleanup(){
			ChatAPI.unsubcribleFromFriendStatus(props.friend.id, handleStatusChange);
		};
	});
	
	if ( isOnline === null){
		return 'Loading...';
	}
	return isOnline? 'Online' :'Offline';
}
```

### Hàm trả về trong `useEffect` có ý nghĩa gì ?
Khi `useEffect` trả về 1 hàm. Hàm này sẽ được hiểu như hàm cleanup effect. 
### Khi nào React cleanup một effect?
React thực hiện cleanup khi component unmount. effect trên tất cả những lần render.

### Mục đích sử dụng `useEffect` nhiều lần ? 
```javascript
function FriendStatusWithCounter(props) {
  const [count, setCount] = useState(0);
  useEffect(() => {    
  	document.title = `You clicked ${count} times`;
  });

  const [isOnline, setIsOnline] = useState(null);
  useEffect(() => {    
  	function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }

    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });
  // ...
}
```

Hook cho phép tách code ==dựa trên cái nó đang làm== chứ không theo phương thức lifecycle. 

## Tối ưu Performance bằng cách bỏ qua Effect
Trong 1 vài trường hợp cần việc thường xuyên chạy *effect* sẽ ảnh hưởng tới performance. 

### `useEffect` chỉ chạy cụ thể khi 1 giá trị thay đổi 
```javascript
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count]); // Chỉ re-run effect nếu giá trị count thay đổi

```
### `useEffect` chỉ chạy khi *mount* và *unmount*
Khi truyên vào với giá trị array rỗng ([]). Điều này báo với React rằng effect này không phụ thuộc vào *bất kỳ* props hoặc state, do đó không bao giờ cẩn re-run. 
```javascript
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, []); // Chỉ re-run effect khi mount, unmount

```


---
Tags: [[ReactJS]]
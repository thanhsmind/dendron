---
title: 'ReactJS Hook'
date: '2021-01-19'
type: programing
---

# ReactJS Hook

## Hook là gì?
Hook là 1 hàm đặc biệt cho phép chúng ta sử dụng các tính năng của React mà ==không cần phải tạo class==. 


## Mục đích của React Hooks
React Hook chỉ được sử dụng cho **function component**. React Hook giúp tách logic ra khỏi việc render component. Nó giúp code Component gọn gàng hơn, tái sử dụng các logic code. 

Team React ==khuyến khích== developer khi viết component mới nên ==chuyển qua viết function component== và sử dụng ==Hook==. 

## Convension khi viết Hook
- Các hàm bắt đầu bằng **use** và được VIẾT HOA chữ cái ngay sau đó là 1 hook. Ví dụ: useWindowWidth(). Lưu ý: đây chỉ là convension khi viết code và ESLint sẽ báo lỗi khi viết.
## Các loại Hook có sẵn

https://reactjs.org/docs/hooks-reference.html
### Basic Hooks
- [[ReactJS Sử dụng State Hook]]: Dùng để tương tác với các State.
- [[ReactJS useEffect hook]]: Tương tác với vòng đời của components
- [[useContext]]: 

### Additional Hooks
- [[ReactJS Sử dụng useRef Hook]]: Sử dụng cố định dữ liệu trong các lần re-render
- [[useMemo]]:
- [[useLayoutEffect]]:
- [[useReducer]]:
- [[useCallback]]:
- [[useImperativeHandle]]:
- [[useDebugValue]]:


---
Tags: [[ReactJS]]
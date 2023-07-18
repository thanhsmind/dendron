---
title: 'Function Component'
date: '2020-01-02'
type: programing
---

# ReactJS Function Component
```javascript
// ./src/Header.tsx
import React from 'react';

interface IProps{
	name?: string;
}

const Header: React.FC<IProps> = (props: IProps) => {
	return <h1> Hello, {props.name}! Welcome to Lazy-Cat project.</h1>
};

Header.defaultProps = {
	name: 'world',
}

export default Header;
```

Khi tạo `Header` component sử dụng `React.FC<IProps>`  (==FC: React.FunctionComponent interface==).

 ---
 Tags: [[ReactJS Component]], [[Typescript Component]]
---
title: 'NextJS: Data Fetching- getServerSideProps'
date: '2020-11-26'
type: programing
---

# NextJS Server Generation: getServerSideProps

## Cú pháp
Khi có function `async` có tên là `getServerSideProps` xuất hiện trong page, NextJs sẽ pre-render lại page tại mỗi request dựa trên data được trả về bởi hàm `getServerSideProps`. 
```javascript
export async function getServerSideProps(context){
	return {
		props: {}, NextJs sẽ pass props này vào trong page component
	}
}

```
#### Tham số `context` chứa các thông tin: 
- `params`:  Nếu page này là 1 dynamic route, `params` sẽ chắc các tham số chứa trong route. Nếu page name là `[id].js`, thì `params` sẽ chứa `{id: ...}`. 
- `req`: [[the-http-incomming-message-object]]
- `res`: [[the-http-response-object]]
- `query`:  1 object chứa các query string
- `preview`: là 1 cờ chứa 1 trong 2 giá trị là `true` hoặc `false`. Thể hiện page này có đang trong mode review hay không.
- `locale` chứa active locale
- `locale` chứa tất cả các locales đang được hỗ trợ

#### `getServerSideProps` trả về 1 object:
- `props`: **Bắt buộc**  phải có giá trị này. `props` sẽ được truyền vào page component.
- `notFound`: 
- `redirect`: 

## Khi nào sử dụng `getServerSideProps` ?
`getServerSideProps` nên được sử dụng khi cần phải lấy  mới data trong mỗi request time. `getServerSideProps` sẽ thường chậm hơn [[getStaticPaths]] bởi vì server phải thực hiện tính toán trong mỗi lần request, result cũng không cached được bởi các CDN.
## TypeScript: Use `GetServerSideProps`
```ts
import { GetServerSideProps } from 'next'

export const getServerSideProps: GetServerSideProps = async (context) => {
  // ...
}
```
Nếu bạn muốn inferred typings props thì có thể sử dụng
```ts
import { InferGetServerSidePropsType } from 'next'

type Data = { ... }

export const getServerSideProps = async () => {
	const res = await fetch('https://.../data')
	const data: Data = await res.json()
	
	return {
		props: {
			data, 
		}
	}
}

function Page({ data }: InferGetServerSidePropsType<typeof getServerSideProps ) {
	// will resolve posts to type Data
}

export default Page
```

---
Tags: [[NextJS]]
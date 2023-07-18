---
title: 'NextJS: Data Fetching- getStaticProps'
date: '2020-11-26'
type: programing 
---

# NextJS Static Generation: getStaticProps

## Cú pháp
Khi export 1 `async` function với tên là `getStaticProps` trong page. Nextjs sẽ pre-render page này khi build. `props` sẽ được gán vào trong page.

```javascript
export async function getStaticProps(context){
	return {
		props: {}, // đối số này sẽ được passed tới page component như là props
	}
}
```
#### Tham số truyền vào `context`

Tham số `context` là 1 object chứa các thông tin: 
- `params`: Chứa route parameters của dynamic routes. Ví dụ : `[id].js`, thì `params` sẽ là `{ id: ...}`
- `preview`: có giá trị `true` nếu page đang trong preview mode ngược lại  `undefined`
- `previewData` chứa preview data được set bởi `setPreviewData`.
- `locale` chứa active locale

#### Kết quả trả ra của hàm `getStaticProps`
Kết quả trả ra là 1 object:
- `props`: ==Bắt buộc== phải có thuộc tính này. Đối số này sẽ được truyền vào trong *page component*
- `revalidate`: Đợi 1 khoảng thời gian bao nhiêu second khi pre-render
- `notFound`: có trả về là 404 hay không
- `redirect`: cho phép redirect tới internal hay external resource


## Khi nào sử dụng `getStaticProps` ?
- data được lấy từ headless CMS
- data có thể public trên cached
- page này bắt buộc phải được render trước cho SEO. generate nhanh với HTML và JSON. có thể cached trên CDN tăng performance.

## TypeScript: Use `GetStaticProps`
```javascript
import { GetStaticProps } from 'next'

export const getStaticProps: GetStaticProps = async (context) => {

}
```

---
Tags: [[NextJS]]
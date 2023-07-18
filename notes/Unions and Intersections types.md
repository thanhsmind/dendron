---
title: 'Unions and Intersections types'
date: '2020-01-02'
type: programing 
---

# Typescript Unions and Intersections types

Trong lập trình, có nhiều lúc ta muốn phối hợp nhiều type sẵn có lại với nhau. TypeScript đưa ra 2 phương pháp để chúng ta có thể vận dụng : 
- Unions: Biến khi sử dụng union có thể chấp nhận type này hoặc type khác
- Intersections: Intersect sẽ combines tất cả các types liên quan vào thành 1 . 

## Union Types
TypeScript sử dụng `|` để nối các types lại với nhau
```typescript
/**
 * Takes a string and adds "padding" to the left.
 * If 'padding' is a string, then 'padding' is appended to the left side.
 * If 'padding' is a number, then that number of spaces is added to the left side.
 */
function padLeft(value: string, padding: string | number) {
  // ...
}

let indentedString = padLeft("Hello world", true);
Argument of type 'boolean' is not assignable to parameter of type 'string | number'.
```

## Intersection Types

```typescript
interface ErrorHandling {
  success: boolean;
  error?: { message: string };
}

interface ArtworksData {
  artworks: { title: string }[];
}

interface ArtistsData {
  artists: { name: string }[];
}

// These interfaces are composed to have
// consistent error handling, and their own data.

type ArtworksResponse = ArtworksData & ErrorHandling;
type ArtistsResponse = ArtistsData & ErrorHandling;

const handleArtistsResponse = (response: ArtistsResponse) => {
  if (response.error) {
    console.error(response.error.message);
    return;
  }

  console.log(response.artists);
};
```


---
Tags: [[TypeScript Types]]
---
title: 'NextJS: Data Fetching'
date: '2020-11-26'
type: programing
---

# NextJS Data Fetching

Được sử dụng để lấy data trước khi pre-rendering
#### Static Generation: Generate trước các page này, thường sử dụng để generate 
- [[NextJS Static Generation getStaticProps]] Fetching data khi **build time**. Khi build prod, node sẽ tự động generate sẵn ra các static page cho trang này.
- [[NextJS getStaticPaths]] Fetch data cụ thể theo từng path

#### Server-side Rendering: Fetch data mỗi request
- [[NextJS Server Generation getServerSideProps]] Hàm này sẽ được chạy mỗi lần request.

---
Tags: [[NextJS]] 

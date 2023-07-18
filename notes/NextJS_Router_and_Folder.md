---
title: 'NextJS: Router and Folder'
date: '2021-1-25'
type: programing
---

# NextJS Router and Folder



| Type                       | Folder                               | Url                                 |     |
| -------------------------- | ------------------------------------ | ----------------------------------- | --- |
| **Index routers**          | pages/index.js                       | /                                   |     |
|                            | pages/blog/index.js                  | /blog                               |     |
| **Nested routes**          | pages/blog/first-post.js             | /blog/first-post                    |     |
|                            | pages/dashboard/settings/username.js | /dashboard/settings/username        |     |
| **Dynamic route segments** | pages/blog/[slug].js                 | /blog/:slug (/blog/hello-world)     |     |
|                            | pages/[username]/settings.js         | /:username/settings (/foo/settings) |     |
|                            | pages/post/[...all].js               | /post/** (/post/2020/id/title)      |     |

---
Tags: [[NextJS]] - [[Dynamic Routers]] - [[Nested Routes]], [[Index Routers]]
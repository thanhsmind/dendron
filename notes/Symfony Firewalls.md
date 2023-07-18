---
title: 'Symfony Firewalls'
date: '2020-01-02'
type: programing 
---

# Symfony Firewalls

```json
# config/packages/security.yaml
security:
    firewalls:
        dev:
            pattern: ^/(_(profiler|wdt)|css|images|js)/
            security: false
        main:
            anonymous: true
            lazy: true

```

### Firewall là gì ?
**Firewall** là hệ thống dùng để authentication, định nghĩa cách làm sao user có thể authenticate ( e.g. login form, API token, etc).

**1 Firewall** chỉ active mới từng request. Symfony dùng `pattern` property để tìm ra request phù hợp. 
-`dev` firewall là 1 fake firewall. nó dùng để block Symfony dev tool khi chạy trên live.
-`main` firewall sẽ handle tất cả các URL. ==`pattern`  không cấu hình tương đương sẽ xử lý tất cả các URL==. 


---
Tags: [[Symfony]]
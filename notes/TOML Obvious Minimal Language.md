---
alias:
- Tom's Obvious Minimal Language
- Toml file
type: programing 
---
# TOML
```toml
# This is a TOML document.

title = "TOML Example"

[owner]
name = "Tom Preston-Werner"
dob = 1979-05-27T07:32:00-08:00 # First class dates

[database]
server = "192.168.1.1"
ports = [ 8000, 8001, 8002 ]
connection_max = 5000
enabled = true

[servers]

  # Indentation (tabs and/or spaces) is allowed but not required
  [servers.alpha]
  ip = "10.0.0.1"
  dc = "eqdc10"

  [servers.beta]
  ip = "10.0.0.2"
  dc = "eqdc10"

[clients]
data = [ ["gamma", "delta"], [1, 2] ]

# Line breaks are OK when inside arrays
hosts = [
  "alpha",
  "omega"
]


```

## Một số điểm lưu ý
- TOML phân biệt chữ hoa chữ thường.
- File TOML phải là tài liệu Unicode được mã hoá `UTF-8` hợp lệ.
- Khoảng trắng được TOML hiểu là ký tự `tab (0x09)` hoặc `dấu cách (0x20)`.
- Dòng mới được hiểu là ký tự `LF (0x0A)` hoặc `CRLF (0x0D0A)`.
- Comment đến hết dòng được sử dụng bằng dấu `#`.

---
Tags: [[DevOps]]
References:
- https://toml.io/en/
Related:
- [[Traefik]]
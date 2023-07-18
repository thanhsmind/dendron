---
type: programing 
---
# State
State là data | information được sử dụng để trigger Flutter _rebuild_ lại toàn bộ UI, hoặc 1 phần UI. 

## App-Wide State
Các values này có tầm ảnh hưởng tới toàn bộ ứng dụng. Thường được fetched từ backend, như: User is authenticated.

## Widget State
- Những data sẽ show ra UI được fetched từ backed/server
- Những giá trị được nhập vào bởi user.

Widget states thường xuyên bị thay đổi

---
title: 'Stateless Widget'
date: '2020-01-02'
type: programing 
---

# Flutter Stateless Widget
Tất cả các widget `extends StatelessWidget` đều là stateless widget. Các widget này không rebuild khi user tương tác với chúng, kể cả khi dữ liệu bên trong 
```dart
import 'package:flutter/material.dart';

class DummyWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      // your nested widgets and children
      child: ...
    );
  }
}

```
- Stateless widgets chỉ render 1 lần duy nhất trên màn hình. Chúng không rerender lại cho đế khi có tác động từ dữ liệu truyền vào khi khởi tạo.
- Build method có thể được trigger khi parent của widget này rebuild, hoặc dữ liệu được cung cấp thông qua hàm construct thay đổi.
- Nếu Stateless widget có parent là 1 statefull widget, Khi Stateful widget thay đổi, và rebuild, thì các child stateless widget cũng rebuild.

Các Stateless Widgets tiêu biểu: Text(), Column(), Row()...

https://api.flutter.dev/flutter/widgets/StatelessWidget-class.html


---
Tags: [[Flutter]] - [[Flutter Widgets]]
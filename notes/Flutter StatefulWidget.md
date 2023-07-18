---
title: 'StatefulWidget'
date: '2020-01-02'
type: programing 
---

# Flutter StatefulWidget
![[flutter-stateful-widget-life-cycle.png]]

Các widget extends StatefulWidget thì được gọi là stateful Widget. 
StatefulWidget sẽ được trigger rebuild lại khi data bên trong widget đó thay đổi, hoặc biến trong khi khởi tạo thay đổi --> Khi đó build(){...} sẽ được kích hoạt .
```dart
class DummyWidget extends StatefulWidget {
  @override
  _DummyWidgetState createState() => _DummyWidgetState();
}

class _DummyWidgetState extends State<DummyWidget> {
  bool _isGreen = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: _isGreen ? Colors.green : Colors.red,
      appBar: AppBar(
        title: Text('Your First App'),
      ),
      body: Center(
          child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: <Widget>[
          TextButton(
            onPressed: () {
              setState(() {
                _isGreen = !_isGreen;
              });
            },
            child: Text(_isGreen ? "TURN RED" : 'TURN GREEN'),
          ),
        ],
      )),
    );
  }
}

```

https://api.flutter.dev/flutter/widgets/StatefulWidget-class.html


---
Tags: [[Flutter]] - [[Flutter Widgets]]
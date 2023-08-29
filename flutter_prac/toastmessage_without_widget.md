# toastmessage_without_widget

- pubspec.yaml 파일에 fluttertoast 패키지를 추가하기 위해

```yaml
dependencies:
  flutter:
    sdk: flutter
  fluttertoast: ^8.0.8
```

- 이후 터미널에서

```yaml
$ flutter pub get
명령 실행하여 패키지 가져온다.
```

```dart
import 'package:flutter/material.dart';
import 'package:fluttertoast/fluttertoast.dart';
// flutter pub get을 터미널에서 명령 실행을 하여 패키지를 가져온다.

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Snack Bar',
      theme: ThemeData(primarySwatch: Colors.red),
      home: NewPage(),
    );
  }
}

class NewPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Snack Bar'),
        centerTitle: true,
      ),
      body: MyBar(),
    );
  }
}

class MyBar extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(
      child: ElevatedButton(
        child: Text('Show'),
        onPressed: () {
          ScaffoldMessenger.of(context).showSnackBar(
            SnackBar(
              content: Text('Hello world',
              textAlign: TextAlign.center,
              style: TextStyle(
                color: Colors.white
              ),
              ),
              backgroundColor: Colors.teal,
              duration: Duration(milliseconds: 1000),
            ),
          );
        },
      ),
    );
  }
}
```

![Alt text](assets/image18.png)
# toast message

```dart
import 'package:flutter/material.dart';
import 'package:fluttertoast/fluttertoast.dart';
// flutter pub get을 터미널에서 명령 실행을 하여 패키지를 가져온다.

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('FlutteraToast Example'),
        ),
        body: Center(
          child: ElevatedButton(
            onPressed: () {
              showToast('hello world i am toast');
            },
            child: Text('Show Toast'),
          ),
        ),
      ),
    );
  }

  void showToast(String message) {
  Fluttertoast.showToast(
    msg: message,
    toastLength: Toast.LENGTH_SHORT,
    gravity: ToastGravity.BOTTOM,
    timeInSecForIosWeb: 1,
    backgroundColor: Colors.black54,
    textColor: Colors.white,
    );
  }
}

```

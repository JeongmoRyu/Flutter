# flutter phone call

- dependency에 추가

```dart
flutter_phone_direct_caller: ^2.1.1
```

- flutter pub get 실행

```dart
$flutter pub get
```

- IOS일 경우

```dart
dict아래부분에
info.plist를 추가해준다.

<key>LSApplicationQueriesSchemes</key>
<array>
  <string>tel</string>
</array>
```

- 기본 example

```dart
import 'package:flutter/material.dart';
import 'package:flutter_phone_direct_caller/flutter_phone_direct_caller.dart';

void main() {
  runApp(Scaffold(
    body: Center(
      child: RaisedButton(
        onPressed: _callNumber,
        child: Text('Call Number'),
      ),
    ),
  ));
}

_callNumber() async{
  const number = '01000000000'; //set the number here
  bool res = await FlutterPhoneDirectCaller.callNumber(number);
}
```

- 전화연결하는 버튼도 만들어주고 연습페이지

```dart
import 'package:flutter/material.dart';
import 'package:flutter_phone_direct_caller/flutter_phone_direct_caller.dart';

class prac8 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('prac8'),
      ),
      body: Center(
        child: ElevatedButton(
          onPressed: () async {
            const number = '01000000000';
            bool? res = await FlutterPhoneDirectCaller.callNumber(number);
            if (res != null && res) {
              // 전화가 성공적으로 걸렸을 때 처리할 로직 추가
            } else {
              // 전화가 실패했을 때 처리할 로직 추가
            }
          },
          child: Icon(Icons.phone),
        ),
      ),
    );
  }
}
```

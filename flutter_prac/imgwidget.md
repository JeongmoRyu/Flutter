# img widget

- assets dir을 만든다.
- pubspec.yaml 설정 파일에서
    
    ```dart
    asset:
    	- assets/
    ```
    
- google 혹은 자신이 가진 gif 파일을 asset에 넣어준다.

```dart
import 'package:flutter/material.dart';

void main() {
  // main 스레드는 runApp을 실행시키고 종료된다.
  runApp(FirstApp());
}
class FirstApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: SafeArea(
        child: Scaffold(
          body: Center(
            // 가운데 정렬 widget
            child: Image.asset(
              'assets/pikachugif.gif',
              width:300,
              fit: BoxFit.contain,),
          ),
      ),
      ),
    );
  }
}

```
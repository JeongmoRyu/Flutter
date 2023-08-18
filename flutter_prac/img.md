# img

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
          body: Column(
            children: [
              Image.asset('assets/basketball_court.png'),
              Text("Want to Play"),
              Text('But it is rainy day :('),
            ],
          ),
      ),
      ),
    );
  }
}

```

![Alt text](image10.png)
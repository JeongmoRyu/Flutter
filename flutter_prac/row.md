# row
```dart
import 'package:flutter/material.dart';
import 'dart:io';
// Duration을 위한 import

void main() {
  // main 스레드는 runApp을 실행시키고 종료된다.
  runApp(FirstApp());
  // runApp(const MyApp());
  // sleep(Duration(seconds:3));
  // 비동기 느낌
  print('main terminate');
}
class FirstApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: SafeArea(
        child:Scaffold(
          appBar: AppBar(
            backgroundColor: Colors.blue,
            title: Text('First App'),
            leading:Icon(Icons.menu),
          ),
          body:Container(
            // Row 자체도 alt enter -> widget으로 감싸줄 수 있다.
            height: 150,
            child: Row(
              children: [
                Expanded(
                  child: Container(
                    width: 100,
                    color:Colors.red,
                  ),
                ),
                Expanded(
                  child: Container(
                    width: 100,
                    color:Colors.orange,
                  ),
                ),
                Expanded(
                  child: Container(
                    width: 100,
                    color:Colors.yellow,
                  ),
                )
              ],
            ),
          ),
          floatingActionButton: FloatingActionButton(
            child: Text("button"),
            onPressed: () {
              print('button clicked');
            },
          ),
          bottomNavigationBar: BottomNavigationBar(
            items:[
              BottomNavigationBarItem(
                label:"hello",
                icon:Icon(
                  Icons.access_alarm_rounded
              )),
              BottomNavigationBarItem(
              label:"hello",
              icon:Icon(
                Icons.access_alarm_rounded
              )),
            ],
          backgroundColor:Colors.yellow,
        ),
      ),
      ));
  }
}

```

![Alt text](image4.png)

```dart
...

body:Container(
            // Row 자체도 alt enter -> widget으로 감싸줄 수 있다.
            height: 150,
            child: Row(
              children: [
                Expanded(
                  child: Container(
                    height: 50,
										// 작게는 설정가능하지만 부모 제약을 넘어서는 
										// 크기를 설정해도 넘어서지를 못한다.
                    width: 100,
                    color:Colors.red,
                  ),

...
```

![Alt text](image5.png)
# column axis

## mainAxisAlignment:

- mainAxisAlignment MainAxisAlignment.spaceAround, (수직 방향)
    - .end
    - .start
    - .center
    - .spaceEvenly
    - .spaceAround
    - .spaceBetween

## crossAxisAlignment

- crossAxisAlignment: CrossAxisAlignment.stretch, (수평 방향)
    - .end
    - .start
    - .center
    - .basement
    - .stretch
    - .values(?)
    

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
          body:Column(
            mainAxisAlignment: MainAxisAlignment.spaceAround,
            // 수직 방향
            //.end, .start, .center
            // .spaceEvenly, .spaceAround, .spaceBetween
            crossAxisAlignment: CrossAxisAlignment.stretch,
            // 수평 방향
            //.end, .start, .center
            // .basement, .stretch, .values(?)
            // 기본 크기가 없기에 높이를 넣어줘야한다.
            children:[
              Container(
                width: 100,
                height: 100,
                color:Colors.brown,
              ),
              Container(
                width: 100,
                height: 100,
                color:Colors.black,
              ),
              Container(
								// 부모 조건이 stretch이기에 child에 넓이를 주지 않아도 적용된다.
                height: 100,
                color:Colors.green,
              ),
            ],
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
![Alt text](image3.png)
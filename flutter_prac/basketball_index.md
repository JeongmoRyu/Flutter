# basketball index

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
      title: 'First App',
      home: MyHomePage(),
    );
  }
}
class MyHomePage extends StatelessWidget {
  // const MyHomePage({super.key});
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.blue[800],
      appBar: AppBar(
        title: Text("Basketball_Court"),
        backgroundColor: Colors.blue[700],
        centerTitle: true,
        elevation: 0.0,
      ),
      body: Padding(
        padding: EdgeInsets.fromLTRB(30.0, 40.0, 0.0, 0.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Center(
              child: CircleAvatar(
                backgroundImage: AssetImage('assets/ball.png'),
                // 이미지 불러오기
                radius: 50.0,
              //  반지름 크기를 통해 크기를 키운다.
              ),
            ),
            Divider(
              height: 60.0,
              color:Colors.grey[850],
              thickness: 1.0,
            //  굵기
              endIndent: 30.0,
            //  끝부분 띄우기 정도
            ),
            // 구분선 만들기
            Text('Name',
              style: TextStyle(
                color:Colors.white,
                letterSpacing: 2.0,
              ),
            ),
            SizedBox(
              height: 10.0,
            ),
            Text('BasketballCourt',
            style: TextStyle(
              color: Colors.white,
              letterSpacing: 2.0,
              fontSize: 30.0,
              fontWeight: FontWeight.bold
            ),
            ),
            SizedBox(
              height: 30.0,
            ),
            Text('Where to Play',
              style: TextStyle(
                color:Colors.white,
                letterSpacing: 2.0,
                fontSize: 20.0,
              ),
            ),
            SizedBox(
              height: 10.0,
            ),
            Text('Basketball',
              style: TextStyle(
                  color: Colors.white,
                  letterSpacing: 2.0,
                  fontSize: 30.0,
                  fontWeight: FontWeight.bold
              ),
            ),
            SizedBox(
              height: 20.0,
            ),
            Row(
              children: [
                Icon(Icons.check_circle_outline),
                SizedBox(
                  width: 10.0,
                ),
                Text(
                  'Gym?!',
                style: TextStyle(
                  fontSize: 15.0,
                  letterSpacing: 1.0
                ),)
              ],
            ),
            Row(
              children: [
                Icon(Icons.check_circle_outline),
                SizedBox(
                  width: 10.0,
                ),
                Text(
                  'riverside court?!',
                  style: TextStyle(
                      fontSize: 15.0,
                      letterSpacing: 1.0
                  ),)
              ],
            ),
            Row(
              children: [
                Icon(Icons.check_circle_outline),
                SizedBox(
                  width: 10.0,
                ),
                Text(
                  'training center?!',
                  style: TextStyle(
                      fontSize: 15.0,
                      letterSpacing: 1.0
                  ),)
              ],
            ),
            SizedBox(
              height: 10.0,
            ),
            Center(
              child: Image.asset(
                  'assets/basketball_court.png',
                width: 290.0,
                fit: BoxFit.contain,
              ),
            )
          ],
        )
      ),
    );
  }
}

```

![Alt text](assets/image12.png)
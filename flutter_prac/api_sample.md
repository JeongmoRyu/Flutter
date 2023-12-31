# api 연결한 기본 페이지 만들기

api 데이터 받은 기본 

```dart
import 'package:flutter/material.dart';
import 'dart:convert';
import 'package:http/http.dart' as http;
import 'package:go_router/go_router.dart';
import 'package:frontend/molecules/top_bar_main.dart';

class ApiTemp extends StatefulWidget {

  // ApiTemp({this.Id = 0});

  @override
  _ApiTempState createState() => _ApiTempState();
}
class _ApiTempState extends State<ApiTemp> {
  Map<String, dynamic> tempList = {};

  @override
  void initState() {
    super.initState();
    fetchData();  // 데이터를 가져오는 함수 호출
  }

  Future<void> fetchData() async {
    final String apiUrl = "";

    // 'Authorization' 헤더 추가 부분
    final headers = {
      "Content-Type": "application/json",
      "Authorization": "",
    };

    final response = await http.get(Uri.parse(apiUrl), headers: headers);

    if (response.statusCode == 200) {
      // 데이터를 정상적으로 가져온 경우
      String body = utf8.decode(response.bodyBytes); // UTF-8 디코딩 추가
      final Map<String, dynamic> data = json.decode(body);

      setState(() {
        tempList = data;  // houseList 업데이트
      });
      print('data: $tempList');
    } else {
      // 200 코드가 아닐 경우
    }
  }

  @override
  Widget build(BuildContext context) {

    return Scaffold(
        appBar: TopBarMain(appBar: AppBar(),),

        body: Container(
          height: 500,
          child: Text('${tempList}'),
        )
    );
  }
}
```

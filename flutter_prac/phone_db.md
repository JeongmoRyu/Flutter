# 휴대폰 기기 저장소에 저정하기


- 최근 검색어와 같은 용도로 사용하기 위해서

shared_preferences dependency를 사용한다.

```dart
import 'package:flutter/material.dart';
import 'dart:convert';
import 'package:http/http.dart' as http;
import 'package:go_router/go_router.dart';
import 'package:frontend/molecules/top_bar_sub.dart';
import 'package:frontend/util/custom_box.dart';
import 'package:shared_preferences/shared_preferences.dart';

class SearchPage extends StatefulWidget {
  @override
  _SearchPageState createState() => _SearchPageState();
}

class _SearchPageState extends State<SearchPage> {
  String keyValue = '';
  List<String> searchDataList = [];
  int maxDataCount = 10;

  @override
  void initState() {
    super.initState();
    keyValue = '';
  }

  void saveSearchData(String data) {
    if (searchDataList.length >= maxDataCount) {
      searchDataList.removeAt(0);
    }
    searchDataList.add(data);
  }

  Future<Map<String, dynamic>> fetchData() async {
    final String apiUrl = "http://j9a505.p.ssafy.io:8080/api/product/1";

    final headers = {
      "Access-Control-Allow-Origin": "*",
      'Content-Type': 'application/json',
      'Accept': '*/*'
    };

    final response = await http.get(Uri.parse(apiUrl), headers: headers);

    if (response.statusCode == 200) {
      String body = utf8.decode(response.bodyBytes);
      final Map<String, dynamic> data = json.decode(body);
      return data;
    } else {
      throw Exception('Failed to load data');
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.white,
        actions: <Widget>[
          Expanded(
            child: Padding(
              padding: const EdgeInsets.all(8.0),
              child: TextField(
                onSubmitted: (value) {

                  setState(() {
                    keyValue = value;
                    saveSearchData(value);
                  });
                },
                onChanged: (value) {
                  setState(() {
                    keyValue = value;
                  });
                },
                decoration: InputDecoration(
                  filled: true,
                  fillColor: Color.fromRGBO(241, 241, 241, 1.0),
                  prefixIcon: IconButton(
                    onPressed: () {
                      Navigator.of(context).pop();
                    },
                    icon: Icon(Icons.arrow_back_ios_new),
                  ),
                  border: InputBorder.none,
                ),
              ),
            ),
          ),
          IconButton(
            onPressed: () {
              context.go('/scrapbook');
            },
            icon: Icon(Icons.bookmark_outline),
          ),
          IconButton(
            onPressed: () {
              context.go('/cart');
            },
            icon: Icon(Icons.interests_outlined),
          ),
        ],
      ),
      body: FutureBuilder(
        future: fetchData(),
        builder: (context, snapshot) {
          if (snapshot.connectionState == ConnectionState.waiting) {
            // 데이터 로딩 중인 경우 로딩 스피너를 표시
            return Center(child: CircularProgressIndicator());
          } else if (snapshot.hasError) {
            // 데이터 로딩 중 오류가 발생한 경우 오류 메시지 표시
            return Center(child: Text('Error: ${snapshot.error}'));
          } else {
            // 데이터 로딩이 완료된 경우 화면에 데이터 표시
            final AllProduct = snapshot.data as Map<String, dynamic>;

            return ListView(
              children: [
                Container(
                  height: 30,
                  child: Text('$keyValue'),
                ),
                if (keyValue.isNotEmpty)
                  Container(
                    height: 550,
                    child: Text('$AllProduct'),
                  )
                else
                  Container(
                    height: 550,
                    child: Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text('최근 검색 데이터:'),
                        SizedBox(height: 10,),
                        Column(
                          children: searchDataList.map((data) {
                            return ListTile(
                              leading: Icon(Icons.search),
                              title: Text(data),
                            );
                          }).toList(),
                        ),
                      ],
                    ),
                  ),
              ],
            );
          }
        },
      ),
    );
  }
}
```

```dart
import 'package:flutter/material.dart';
import 'dart:convert';
import 'package:http/http.dart' as http;
import 'package:go_router/go_router.dart';
import 'package:frontend/molecules/top_bar_sub.dart';
import 'package:frontend/util/custom_box.dart';
import 'package:shared_preferences/shared_preferences.dart';
import 'package:flutter/services.dart';

class SearchPage extends StatefulWidget {
  @override
  _SearchPageState createState() => _SearchPageState();
}

class _SearchPageState extends State<SearchPage> {
  String keyValue = '';
  List<String> searchDataList = [];
  List<String> relatedDataList = [];
  int maxSearchDataCount = 8;
  int maxrelatedDataList = 8;

  @override
  void initState() {
    super.initState();
    keyValue = '';
    loadSearchData();
  }

  void saveSearchData(String data) async {
    if (searchDataList.length >= maxSearchDataCount) {
      searchDataList.removeAt(0);
    }
    searchDataList.add(data);

    // SharedPreferences에 검색어 데이터 저장
    SharedPreferences prefs = await SharedPreferences.getInstance();
    prefs.setStringList('keyword', searchDataList);
  }

  void loadSearchData() async {
    // SharedPreferences에서 검색어 데이터 불러오기
    SharedPreferences prefs = await SharedPreferences.getInstance();
    searchDataList = prefs.getStringList('keyword') ?? [];

    // 최대 검색어 개수를 초과하면 삭제
    if (searchDataList.length > maxSearchDataCount) {
      searchDataList = searchDataList.sublist(searchDataList.length - maxSearchDataCount);
    }
  }

  Future<Map<String, dynamic>> fetchData() async {
    final String apiUrl = "http://j9a505.p.ssafy.io:8080/api/product/1";

    final headers = {
      "Access-Control-Allow-Origin": "*",
      'Content-Type': 'application/json',
      'Accept': '*/*'
    };

    final response = await http.get(Uri.parse(apiUrl), headers: headers);

    if (response.statusCode == 200) {
      String body = utf8.decode(response.bodyBytes);
      final Map<String, dynamic> data = json.decode(body);
      return data;
    } else {
      throw Exception('Failed to load data');
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.white,
        actions: <Widget>[
          Expanded(
            child: Padding(
              padding: const EdgeInsets.all(8.0),
              child: TextField(
                inputFormatters: [
                  LengthLimitingTextInputFormatter(50),
                ],
                onSubmitted: (value) {
                  setState(() {
                    keyValue = value;
                    saveSearchData(value);
                  });
                },
                onChanged: (value) {
                  setState(() {
                    keyValue = value;
                  });
                },
                decoration: InputDecoration(
                  filled: true,
                  fillColor: Color.fromRGBO(241, 241, 241, 1.0),
                  prefixIcon: IconButton(
                    onPressed: () {
                      Navigator.of(context).pop();
                    },
                    icon: Icon(Icons.arrow_back_ios_new),
                  ),
                  border: InputBorder.none,
                ),
              ),
            ),
          ),
          IconButton(
            onPressed: () {
              context.go('/scrapbook');
            },
            icon: Icon(Icons.bookmark_outline),
          ),
          IconButton(
            onPressed: () {
              context.go('/cart');
            },
            icon: Icon(Icons.interests_outlined),
          ),
        ],
      ),
      body: FutureBuilder(
        future: fetchData(),
        builder: (context, snapshot) {
          if (snapshot.connectionState == ConnectionState.waiting) {
            return Center(child: CircularProgressIndicator());
          } else if (snapshot.hasError) {
            return Center(child: Text('Error: ${snapshot.error}'));
          } else {
            final AllProduct = snapshot.data as Map<String, dynamic>;

            return ListView(
              children: [
                Container(
                  height: 30,
                  child: Text('$keyValue'),
                ),
                if (keyValue.isNotEmpty)
                  Container(
                    height: 550,
                    child: Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text('  '+'$keyValue ' + ' 와 관련한 데이터 :'),
                        SizedBox(height: 10,),
                        Column(
                          children: relatedDataList.map((data) {
                            return ListTile(
                              leading: Icon(Icons.search),
                              title: Text(data),
                            );
                          }).toList(),
                        ),
                      ],
                    ),
                    // Text('$AllProduct'),
                  )
                else
                  Container(
                    height: 550,
                    child: Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text('  ' + '최근 검색 데이터 :'),
                        SizedBox(height: 10,),
                        Column(
                          children: searchDataList.map((data) {
                            return ListTile(
                              leading: Icon(Icons.search),
                              title: Text(data),
                            );
                          }).toList(),
                        ),
                      ],
                    ),
                  ),
              ],
            );
          }
        },
      ),
    );
  }
}
```

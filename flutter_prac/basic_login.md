# 기본 로그인 구현

```dart
import 'package:flutter/material.dart';
import 'package:go_router/go_router.dart';
import 'package:pracforcvs/appbar.dart';
import 'package:pracforcvs/singin.dart';

class Login extends StatelessWidget {
  const Login({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: CustomAppBar(),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(
              '로그인',
              style: TextStyle(
                fontSize: 24,
                fontWeight: FontWeight.bold,
              ),
            ),
            SizedBox(height: 20),

            Column(
              children: [
                Container(
                  width: MediaQuery.of(context).size.width * 0.8,
                  child: TextFormField(
                    decoration: InputDecoration(
                        prefixIcon: Icon(
                          Icons.account_circle,
                        ),
                        enabledBorder: OutlineInputBorder(
                          borderRadius: BorderRadius.all(
                            Radius.circular(10.0),
                          ),
                        ),
                        focusedBorder: OutlineInputBorder(

                          borderRadius: BorderRadius.all(
                            Radius.circular(10.0),
                          ),
                        ),
                        hintText: '이메일',
                        hintStyle: TextStyle(
                          fontSize: 14,
                        ),
                        contentPadding: EdgeInsets.all(10)),
                  ),
                ),
                SizedBox(height: 5,),
                Container(
                  width: MediaQuery.of(context).size.width * 0.8,
                  child: TextFormField(
                    decoration: InputDecoration(
                        prefixIcon: Icon(
                          Icons.key,
                        ),
                        enabledBorder: OutlineInputBorder(
                          borderRadius: BorderRadius.all(
                            Radius.circular(10.0),
                          ),
                        ),
                        focusedBorder: OutlineInputBorder(

                          borderRadius: BorderRadius.all(
                            Radius.circular(10.0),
                          ),
                        ),
                        hintText: '비밀번호',
                        hintStyle: TextStyle(
                          fontSize: 14,
                        ),
                        contentPadding: EdgeInsets.all(10)),
                  ),
                ),
                SizedBox(height: 10,),
                Container(
                  width: MediaQuery.of(context).size.width * 0.8,
                  child: ElevatedButton(
                    onPressed: () {
                    },
                    style: ElevatedButton.styleFrom(
                      primary: Colors.grey, // 원하는 색상으로 변경
                    ),
                    child: Text('로그인'),
                  ),
                ),
                SizedBox(height: 20,),
                TextButton(
                  onPressed: () {
                    context.go('/singin');
                  },
                  child: Text('회원가입'), // '회원가입' 텍스트 추가
                ),
              ],

            ),

          ],
        ),
      ),
    );
  }
}

```

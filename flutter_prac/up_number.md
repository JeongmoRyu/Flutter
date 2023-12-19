# dart에서 반올림하기

- .toStringAsFixed(3)

- example)

```dart
Container(
                      height: 250,
                      width: 250,
                      child: Center(
                        child: Column(
                          mainAxisAlignment: MainAxisAlignment.center,
                          crossAxisAlignment: CrossAxisAlignment.center,
                          children: [
                            ListTile(
                              leading: Icon(Icons.circle, color: Colors.red),
                              title: Text('순탄수 : ' + '${carbRatio.toStringAsFixed(3)} %'),
                            ),
                            ListTile(
                              leading: Icon(Icons.circle, color: Colors.green),
                              title: Text('단백질 : ' '${proteinRatio.toStringAsFixed(3)}' + ' %'),
                            ),
                            ListTile(
                              leading: Icon(Icons.circle, color: Colors.blue),
                              title: Text('지방 : '+'${fatRatio.toStringAsFixed(3)}' + ' %'),
                            ),
                            ListTile(
                              leading: Icon(Icons.circle, color: Colors.orange),
                              title: Text('나트륨 : '+'${sodiumRatio.toStringAsFixed(3)}' + ' %'),
                            )
                          ],
                        ),
                      ),
                    )
```

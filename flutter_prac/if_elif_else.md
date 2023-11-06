# json파일을 바탕으로 if elif else practice

- 함수를 만들거나 OX일 경우 직접 bool 형식으로 가져올 수 있다.

```dart
Row(
  children: [
    Text(
      _getContractInfo(), // contractcode에 따라 다른 내용을 반환하는 함수 호출
      style: TextStyle(
        color: Colors.black,
        fontSize: 20,
        letterSpacing: 2.0,
        fontWeight: FontWeight.bold,
      ),
    ),
    SizedBox(width: 10), // 두 Text 위젯 사이에 간격을 줄 수 있습니다.
    Text(
      houseList['contractInfo']['maintenance'] != null
          ? '관리비 ' + houseList['contractInfo']['maintenance'].toString()
          : '', // maintenance가 존재하면 해당 값을 출력, 그렇지 않으면 빈 문자열 출력
      style: TextStyle(
        color: Colors.grey[500],
        fontSize: 13,
        letterSpacing: 2.0,
        fontWeight: FontWeight.bold,
      ),
    ),
  ],
)
```

- getContractInfo 함수 만들기

```dart

String _getContractInfo() {
  int contractCode = houseList['contractCode'];
  if (contractCode == 3) {
    return '매매 ' + houseList['contractInfo']['salePrice'].toString();
  } else if (contractCode == 2) {
    return '전세 ' + houseList['contractInfo']['deposit'].toString();
  } else {
    return '월세 ' + houseList['contractInfo']['deposit'].toString() +
        '/' + houseList['contractInfo']['monthlyRent'].toString();
  }
}
```

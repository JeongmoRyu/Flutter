# container에 따른 높이 정렬하는 방법들

```dart
Container(
              height: ProductDetail['productName'].length > 20 ? 55 : 25,
              padding: EdgeInsets.only(left: 20),
              child: Align(
                alignment: Alignment.centerLeft,
                child: Text(
                  '제품 명 :  ${ProductDetail['productName']}',
                  style: TextStyle(
                    color: Colors.black,
                    fontSize: 20,
                    fontWeight: FontWeight.bold,
                    backgroundColor: Colors.white,
                  ),
                ),
              ),
            )
```

- 만약 길이만 긴 게 아니라 다른 내용들도 들어간다면
    - shrink() 사용하는 것도 방법이다.

```dart
Expanded(
        child: houseList['contractInfo']['maintenance'] != null
            ? Container(
          alignment: Alignment.centerLeft,
          child: Text(
            '관리비 ' + houseList['contractInfo']['maintenance'].toString(),
            style: TextStyle(
              color: Colors.grey[500],
              letterSpacing: 2.0,
              fontWeight: FontWeight.bold,
            ),
          ),
        )
            : SizedBox.shrink(),
      ),
```

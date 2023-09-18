# collection generic

### **Collection**

- 데이터들을 모아서 가지고 있는 자료구조

### **Generic**

- Collection이 가지고 있는 데이터들의 데이터 타입을 지정

```dart
void main(){
  String name = 'JM';
  print(name);

  print('hi! I am $name')
}

```

- Collection and Generic example
    - hello $name -> hello JM

### interpolation : 보간법

- your score point is $score and your level is $level
    - your score point is 85 and your level is 7

```dart
void main() {
  List number = new List();

  number.add(2);
  number.add('test');
  number.add(7.4);
  number.add(addNubmer(3, 4));
  number.add(true);
  print(number)
}
```

→ [2, test, 7.4, 7, true]

```dart
void printNumber(List<int> a) {
  print(a);
}

void main() {
  List<int> number = List();

  number.add(5);
  printNumber(nubmer);
}
```

→ [5]

```dart
void main() {
  List<String> names = List();
  names.addAll(['Jordan', 'James', 'Magic']);
  print(names);
}
```

→ [Jordan, James, Magic]

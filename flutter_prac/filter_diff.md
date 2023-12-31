# 필터 두개 연동되지 안되게

```dart
import 'package:flutter/material.dart';

class prac19 extends StatefulWidget {
  const prac19({Key? key}) : super(key: key);

  @override
  _prac19State createState() => _prac19State();
}

class _prac19State extends State<prac19> {
  int? startIndex;
  int? endIndex;
  List<String> clickList = [];
  List<String> allButtons = List.generate(20, (index) => 'Button ${index + 1}');
  List<String> allButtonTwos = List.generate(20, (index) => 'Button2 ${index + 1}');
  List<String> clickList_2 = [];

  void selectButtonsBetween(int startIndex, int endIndex) {
    setState(() {
      clickList.clear();
      clickList.addAll(allButtons.sublist(startIndex, endIndex + 1));
    });
  }

  void selectallButtonTwosBetween(int startIndex, int endIndex) {
    setState(() {
      clickList_2.clear();
      clickList_2.addAll(allButtonTwos.sublist(startIndex, endIndex + 1));
    });
  }

  void selectAllButtons() {
    setState(() {
      clickList.clear();
      clickList.addAll(allButtons);
    });
  }

  void selectAllTwoButtons() {
    setState(() {
      clickList_2.clear();
      clickList_2.addAll(allButtonTwos);
    });
  }

  void resetSelection() {
    setState(() {
      clickList.clear();
      startIndex = null;
      endIndex = null;
    });
  }

  void resetSelectionTwo() {
    setState(() {
      clickList_2.clear();
      startIndex = null;
      endIndex = null;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('보여줘왓슨'),
      ),
      body: Column(
        children: [
          Row(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: [
              ElevatedButton(
                onPressed: selectAllButtons,
                child: Text('전체 선택'),
              ),
              ElevatedButton(
                onPressed: resetSelection,
                child: Text('초기화'),
              ),
            ],
          ),
          Expanded(
            child: Container(
              child: GridView.builder(
                shrinkWrap: true,
                gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
                  crossAxisCount: 5,
                  crossAxisSpacing: 5.0,
                  mainAxisSpacing: 5.0,
                ),
                itemCount: allButtons.length,
                itemBuilder: (context, index) {
                  final button = allButtons[index];
                  final isSelected = clickList.contains(button);

                  return Container(
                    height: 10,
                    child: ElevatedButton(
                      onPressed: () {
                        if (clickList.isEmpty) {
                          setState(() {
                            clickList.add(button);
                            startIndex = index;
                            endIndex = index;
                          });
                        } else {
                          if (startIndex != null && endIndex != null) {
                            int currentIndex = allButtons.indexOf(button);

                            if (currentIndex < startIndex!) {
                              setState(() {
                                startIndex = currentIndex;
                                clickList.clear();
                                clickList.addAll(allButtons.sublist(currentIndex, endIndex! + 1));
                              });
                            } else if (currentIndex > endIndex!) {
                              setState(() {
                                endIndex = currentIndex;
                                clickList.clear();
                                clickList.addAll(allButtons.sublist(startIndex!, currentIndex + 1));
                              });
                            } else {
                              selectButtonsBetween(startIndex!, endIndex!);
                            }
                          }
                        }
                      },
                      style: ElevatedButton.styleFrom(
                        primary: isSelected ? Colors.brown[300] : Colors.grey[300],
                        textStyle: TextStyle(
                          fontSize: 10,
                        ),
                      ),
                      child: Text(button),
                    ),
                  );
                },
              ),
            ),
          ),
          Text(
            '${clickList}',
            style: TextStyle(
              color: Colors.black,
              letterSpacing: 2.0,
              fontSize: 10,
              fontWeight: FontWeight.bold,
            ),
          ),

          SizedBox(height: 20),
          Row(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: [
              ElevatedButton(
                onPressed: selectAllTwoButtons,
                child: Text('two 전체 선택'),
              ),
              ElevatedButton(
                onPressed: resetSelectionTwo,
                child: Text('two 초기화'),
              ),
            ],
          ),
          Expanded(
            child: Container(
              child: GridView.builder(
                shrinkWrap: true,
                gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
                  crossAxisCount: 5,
                  crossAxisSpacing: 5.0,
                  mainAxisSpacing: 5.0,
                ),
                itemCount: allButtonTwos.length,
                itemBuilder: (context, index) {
                  final button = allButtonTwos[index];
                  final isSelected = clickList_2.contains(button);

                  return Container(
                    height: 10,
                    child: ElevatedButton(
                      onPressed: () {
                        if (clickList_2.isEmpty) {
                          setState(() {
                            clickList_2.add(button);
                            startIndex = index;
                            endIndex = index;
                          });
                        } else {
                          if (startIndex != null && endIndex != null) {
                            int currentIndex = allButtonTwos.indexOf(button);

                            if (currentIndex < startIndex!) {
                              setState(() {
                                startIndex = currentIndex;
                                clickList_2.clear();
                                clickList_2.addAll(allButtonTwos.sublist(currentIndex, endIndex! + 1));
                              });
                            } else if (currentIndex > endIndex!) {
                              setState(() {
                                endIndex = currentIndex;
                                clickList_2.clear();
                                clickList_2.addAll(allButtonTwos.sublist(startIndex!, currentIndex + 1));
                              });
                            } else {
                              selectallButtonTwosBetween(startIndex!, endIndex!);
                            }
                          }
                        }
                      },
                      style: ElevatedButton.styleFrom(
                        primary: isSelected ? Colors.brown[300] : Colors.grey[300],
                        textStyle: TextStyle(
                          fontSize: 10,
                        ),
                      ),
                      child: Text(button),
                    ),
                  );
                },
              ),
            ),
          ),
          SizedBox(height: 20),

          Text(
            '${clickList_2}',
            style: TextStyle(
              color: Colors.black,
              letterSpacing: 2.0,
              fontSize: 10,
              fontWeight: FontWeight.bold,
            ),
          ),
        ],
      ),
    );
  }
}

void main() {
  runApp(MaterialApp(
    home: prac19(),
  ));
}
```

![image](assets/image40.PNG)

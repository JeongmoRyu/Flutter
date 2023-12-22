# 차트 안에 글자 넣는 것처럼 쌓기

```dart
Container(
                      height: 250,
                      color: Colors.grey[200],
                      child: Stack(
                        alignment: Alignment.center, // 텍스트를 중앙에 배치
                        children: [
                          Container(
                            height: 250,
                            color: Colors.grey[200],
                            child: SfCircularChart(
                              series: <CircularSeries>[
                                DoughnutSeries<ChartData, String>(
                                  // gap: '5%',
                                  dataSource: chartData,
                                  pointColorMapper: (ChartData data, _) => data.color,
                                  xValueMapper: (ChartData data, _) => data.x,
                                  yValueMapper: (ChartData data, _) => data.y,
                                  radius: '90%',
                                  innerRadius: '85%',
                                ),
                              ],
                            ),
                          ),
                          Text(
                            'Hello',
                            style: TextStyle(
                              fontSize: 18, // 텍스트 크기 설정
                              fontWeight: FontWeight.bold, // 텍스트 굵기 설정
                            ),
                          ),
                        ],
                      ),
                    )
```

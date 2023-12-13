# img temp 페이지 만들기

```dart
import 'package:flutter/material.dart';
import 'dart:convert';
import 'package:dio/dio.dart';
import 'dart:typed_data';

String imageUrl = 'https://image.woodongs.com/imgsvr/item/GD_8801007922195_001.jpg';

class ImageWidget extends StatefulWidget {
  const ImageWidget({Key? key, required this.index}) : super(key: key);
  final int index;

  @override
  _ImageWidgetState createState() => _ImageWidgetState();
}

class _ImageWidgetState extends State<ImageWidget> {
  Response<List<int>>? response;

  @override
  void initState() {
    super.initState();
    _loadImage();
  }

  Future<void> _loadImage() async {
    try {
      response = await Dio().get<List<int>>(
        imageUrl,
        options: Options(
            responseType: ResponseType.bytes
        ),

      );
      if (mounted) {
        setState(() {});
      }
    } catch (e) {
      // Handle errors here
      print('Error loading image: $e');
    }
  }

  @override
  Widget build(BuildContext context) {
    return SizedBox(
      height: 200,
      width: double.infinity,
      child: Column(
        children: [
          Expanded(
            flex: 2,
            child: Card(
              child: AspectRatio(
                aspectRatio: 16 / 9,
                child: response != null && response!.statusCode == 200
                    ? Image.memory(
                  Uint8List.fromList(response!.data ?? []),
                  fit: BoxFit.cover,
                )
                    : Center(
                        child: CircularProgressIndicator(),
                ),
              ),
            ),
          ),
          SizedBox(height: 10),
          Expanded(
            flex: 1,
            child: Text(
              '남양)프렌치카푸치노200ml',
              style: TextStyle(
                fontSize: 18,
                fontWeight: FontWeight.bold,
              ),
            ),
          ),
        ],
      ),
    );
  }
}

```

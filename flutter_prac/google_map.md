# google map 기초 연습

```dart
import 'package:flutter/material.dart';
import 'package:google_maps_flutter/google_maps_flutter.dart';
import 'package:prac2/base/appbar.dart';
import 'package:prac2/screens/home_screen.dart';
import 'package:go_router/go_router.dart';
import 'package:prac2/real_estate_agent/screen/estate_home_screen.dart';

class MapScreen extends StatefulWidget {
  const MapScreen({Key? key}) : super(key: key);

  @override
  _MapScreenState createState() => _MapScreenState();
}

class _MapScreenState extends State<MapScreen> {
  late GoogleMapController mapController;

  final LatLng _center = const LatLng(37.50125, 127.03969);

  void _onMapCreated(GoogleMapController controller) {
    mapController = controller;
  }
  // '서울특별시'
  // '부산광역시'
  // '대구광역시'
  // '인천광역시'
  // '광주광역시'
  // '대전광역시'
  // '울산광역시'
  // '세종특별자치시'
  // '경기도'
  // '북부출장소'
  // '충청북도'
  // '충청남도'
  // '전라북도'
  // '전라남도'
  // '경상북도'
  // '경상남도'
  // '제주특별자치도'
  // '강원특별자치도'
  // '동해출장소'

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: CustomAppBar(
          onLeadingPressed: () {
            context.go('/');
          },
          showEstateHomeButton: true,
          onEstateHomePressed: () {
            context.go('/estate_home');
          },
        ),
        body: GoogleMap(
          onMapCreated: _onMapCreated,
          initialCameraPosition: CameraPosition(
            target: _center,
            zoom: 14.0,
          ),
          minMaxZoomPreference: MinMaxZoomPreference(12.0, 16.0),
        ),

      ),
    );
  }
}
void main() {
  runApp(MaterialApp(
    home: MapScreen(),
  ));
}
```

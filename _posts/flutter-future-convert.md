
# How To Convert Future<String> to String?

```
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  Future<String> fetchData() async {
    // 비동기 작업을 수행하는 가상의 함수
    await Future.delayed(Duration(seconds: 2)); // 예시 비동기 대기 시간
    return '로드된 데이터';
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('FutureBuilder 예제'),
      ),
      body: Center(
        child: FutureBuilder<String>(
          future: fetchData(), // 비동기 작업을 수행할 Future
          builder: (context, snapshot) {
            if (snapshot.connectionState == ConnectionState.waiting) {
              // 데이터가 아직 로드 중인 경우
              return CircularProgressIndicator();
            } else if (snapshot.hasError) {
              // 에러가 발생한 경우
              return Text('에러 발생: ${snapshot.error}');
            } else {
              // 데이터가 로드된 경우
              return Text('로드된 데이터: ${snapshot.data}');
            }
          },
        ),
      ),
    );
  }
}

```
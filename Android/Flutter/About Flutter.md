# Flutter 기본 소개

## Flutter란?

Flutter는 ==구글에서 개발==한 오픈 소스 UI 소프트웨어 개발 키트입니다. iOS와 Android를 포함한 여러 플랫폼을 위한 아름다운 네이티브 앱을 빠르게 개발할 수 있게 해주는 도구입니다.

## 주요 특징

1. **크로스 플랫폼 개발**: 단일 코드베이스를 사용하여 iOS, Android, 웹, 그리고 데스크톱 앱을 개발할 수 있습니다. - 최근 확장됨. 빠른 발전.
2. **핫 리로드**: 코드 변경 사항을 즉시 앱에 반영하여, 개발 과정에서 시간을 크게 단축시킵니다.
3. **풍부한 위젯**: 매우 풍부한 위젯 라이브러리를 제공하여, 복잡한 사용자 인터페이스를 쉽게 구성할 수 있습니다.
4. **높은 성능**: Dart 언어로 작성되며, 네이티브 성능을 제공합니다.



## 개발 환경 설정

Flutter 개발을 시작하기 위해서는 다음과 같은 도구들이 필요합니다.

1. **Flutter SDK**: 공식 [Flutter 웹사이트](https://flutter.dev/)에서 SDK를 다운로드 받을 수 있습니다.
2. **IDE**: ==Android Studio==, VSCode, IntelliJ 등이 Flutter 개발에 사용될 수 있습니다. 각 IDE에는 Flutter와 Dart를 위한 플러그인을 설치해야 합니다.

React Native의 경우는 Android Studio 사용 불가.

## 간단한 예제

dart

Copy code

`import 'package:flutter/material.dart';  void main() {   runApp(MyApp()); }  class MyApp extends StatelessWidget {   @override   Widget build(BuildContext context) {     return MaterialApp(       home: Scaffold(         appBar: AppBar(           title: Text('Welcome to Flutter'),         ),         body: Center(           child: Text('Hello World'),         ),       ),     );   } }`

이 코드는 'Hello World' 텍스트를 화면 가운데에 표시하는 간단한 Flutter 앱을 만듭니다. `MaterialApp` 위젯을 사용하여 기본적인 Material 디자인의 앱을 구성할 수 있습니다.

#Flutter #Mobile #Android

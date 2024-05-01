How to import Flutter platform in Android Studio.

0. Set Android Studio
1. **Download Flutter SDK : Flutter 공식 웹사이트에서 Flutter SDK를 다운로드하고, 압축을 풀어 적절한 위치에 저장합니다.
2. Set Flutter file in somewhere like C://Users//YOURNAME//flutter
    
3. **환경 변수 설정**: 시스템의 환경 변수에 Flutter의 bin 디렉토리 경로를 추가
    
4.  **Android Studio에 Flutter 플러그인 설치**: Android Studio를 열고 'Plugins' 메뉴에서 'Marketplace'를 선택한 후 'Flutter'를 검색하여 설치합니다. 이 플러그인 설치 시 Dart 플러그인도 함께 설치됩니다.
5. Flutter 프로젝트 생성: 이제 새 프로젝트를 생성하려 할때 Flutter 프로젝트 생성란이 생김.



#### Difference between SDK and plugin
- **Flutter SDK**: 이것은 Flutter 프레임워크 자체입니다. 애플리케이션 개발을 위한 핵심 도구와 라이브러리, Dart 언어를 포함하고 있습니다. 이 SDK는 Flutter 앱을 개발할 때 필요한 모든 기능을 제공합니다.
    
- **Flutter plugin for Android Studio**: 이 플러그인은 Android Studio 내에서 Flutter 애플리케이션을 개발, 실행, 디버그하는 데 필요한 기능을 제공합니다. 플러그인은 Android Studio를 Flutter 개발에 최적화된 환경으로 만들어주며, 코드 편집, 앱 실행, 성능 모니터링 등을 지원합니다.
    

Flutter SDK는 프레임워크 자체를 제공하고, Flutter 플러그인은 그 프레임워크를 사용하여 Android Studio에서 개발할 수 있도록 돕는 역할을 합니다.
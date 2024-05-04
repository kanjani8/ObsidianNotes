# pubspec.yaml 구성요소 설명

## 기본 정보 설정
- `name`: 패키지의 이름을 정의합니다.
- `description`: 패키지의 간단한 설명을 제공합니다.
- `version`: 애플리케이션의 버전을 지정합니다. `major.minor.patch+build` 형식을 따릅니다.
- `environment`: Dart SDK의 버전 범위를 지정합니다. sdk: '>=3.3.4 <4.0.0'

## 발행 방지 설정
- `publish_to`: `'none'`으로 설정하면 실수로 패키지가[ pub.dev](https://pub.dev/)에 발행되는 것을 방지할 수 있습니다. 공개적으로 배포하고 싶지 않은 프라이빗 패키지에 유용합니다.

## 종속성 관리
- `dependencies`: 앱이 정상적으로 작동하기 위해 필요한 외부 패키지들을 명시합니다.
	- 패키지 종속성을 최신 버전으로 자동 업그레이드
		 `flutter pub upgrade --major-versions'`
	 -  pub.dev에서 사용 가능한 최신 버전을 확인하여 종속성을 수동으로 업데이트
		  `flutter pub outdated` 
  - `flutter`: Flutter SDK를 종속성으로 명시합니다.
  - `cupertino_icons`: iOS 스타일 아이콘을 사용할 수 있는 패키지입니다.

## 개발 종속성
- `dev_dependencies`: 개발 중에만 필요하고, 앱 실행 시에는 필요하지 않은 패키지들을 명시합니다.
  - `flutter_test`: 플러터 앱을 테스트하기 위한 도구들을 포함합니다.
  - `flutter_lints`: 코드 품질을 관리하기 위한 린트(정적 분석 도구) 규칙을 제공합니다.

## Flutter 특정 설정
- `flutter`: Flutter 관련 설정을 명시합니다.
  - `uses-material-design`: Material 디자인 아이콘을 앱에서 사용 가능하게 합니다.
  - `assets`: 앱에서 사용할 자산(이미지, 파일 등)을 등록할 수 있습니다.
  - `fonts`: 사용자 지정 폰트를 앱에 추가할 수 있습니다. 폰트 파일과 스타일을 정의할 수 있습니다.

## 버전 및 빌드 관리
- `version`: 앱의 버전을 설정하며, 이는 Android의 `versionName`과 iOS의 `CFBundleShortVersionString`에 해당합니다.
- `build-number`: 빌드 번호로, Android의 `versionCode`와 iOS의 `CFBundleVersion`에 사용됩니다.

## 추가 참고
- 각 설정 옵션에 대한 자세한 설명과 사용법은 [Flutter 공식 문서](https://flutter.dev/docs)에서 찾아볼 수 있습니다.

이 파일을 통해 Flutter 앱의 설정과 종속성 관리를 중앙에서 쉽게 할 수 있으며, 앱의 빌드와 배포 과정을 효율적으로 관리할 수 있습니다.

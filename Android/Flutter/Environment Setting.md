with Android Studio. - to use Emulator and ect

1. **Download the latest Flutter SDK**(프레임워크) https://docs.flutter.dev/get-started/install/windows/mobile?tab=download#download-then-install-flutter
2. sdk 압축 해제후 개발 프로그램 등이 저장되기 적정한 위치로 이동. ex. C://, 10345
	C://Users//10345//flutter
3. Update your Windows PATH variable
	혹시 몰라 재부팅
4. 안드로이드 스튜디오에서 필요 sdk들 확인 및 설치 
	- **Android SDK Platform, API 34.0.0**
	- **Android SDK Command-line Tools**
	- **Android SDK Build-Tools**
	- **Android SDK Platform-Tools**
	- **Android Emulator**
5. Android Studio의 플러그인 설정에서 Flutter 플러그인 설치
	이거하면 dart plugin도 자동 설치됨.
	![[Pasted image 20240501171742.png|400]]
	[[Flutter SDK와 Plugin 차이]]
6. Agree to Android licenses
	C:> flutter doctor --android-licenses 명령어 안드로이드 스튜디오 콘솔에서 돌려서 전부 동의로 선택하기.
7. Create New Flutter project
	아래와 같이 New Flutter project 를 선택할 수 있게된다.
	![[Pasted image 20240501171950.png]]
8. 그 외 Flutter를 위한 환경 확인
	콘솔에서  C:> flutter doctor 돌리면 체크해줌. - 하지만  Visual Studio, Desktop development with C++ 를 설치하라는 안내문은 데스크톱 앱을 개발하지 않는 한 필요없음.
9. 프로젝트 생성하기 [[How to Create a Flutter app]]
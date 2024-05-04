<uses-permission android:name="android.permission.BODY_SENSORS"/>  
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"  
    tools:ignore="CoarseFineLocation" />  
### 1. 환경 설정

1. **Android Studio 설치**: 최신 버전의 Android Studio를 설치합니다.
2. **Wear OS Emulator 설정**: Wear OS 앱을 테스트하기 위해 Android Studio에서 Wear OS Emulator를 설정합니다.
3. **실제 Wear OS 디바이스 설정 (선택 사항)**: 실제 장치에서 테스트하려면, Wear OS 디바이스를 준비하고 개발 컴퓨터에 연결합니다.

### 2. Wear OS 앱 개발

1. **새 프로젝트 생성**:
    
    - Android Studio에서 "Start a new Android Studio project" 선택
    - Wear OS와 Mobile을 모두 포함하는 프로젝트 구조를 선택
2. **권한 설정**:   [[How to take a data from sensor of Smart watch]]
    
    - Wear OS 앱과 스마트폰 앱의 `AndroidManifest.xml` 파일에 필요한 권한 추가:
        - 위치 정보: `android.permission.ACCESS_FINE_LOCATION`
        - 심박수 측정: `android.permission.BODY_SENSORS`
    - 권한 요청 코드 추가: Android 6.0(API 레벨 23) 이상에서는 런타임 권한 요청이 필요합니다.
3. **센서 데이터 읽기**:
    
    - **심박수 측정**: `SensorManager`와 `Sensor.TYPE_HEART_RATE`를 사용하여 심박수 데이터를 취득합니다.
    - **체온 및 혈압 측정**: 현재 Wear OS에서는 직접적으로 체온이나 혈압을 측정할 수 있는 표준 API를 제공하지 않습니다. 이를 위해서는 외부 장치를 사용하거나, 장치가 제공하는 별도의 API를 활용해야 합니다.
    - **GPS 위치 정보**: `LocationManager`를 사용하여 위치 정보를 취득합니다.
4. **데이터 전송 (Data Layer API 사용)**:
    
    - Wear OS 앱에서 측정된 데이터를 `DataMap` 객체에 포장하여 스마트폰 앱으로 전송합니다.
    - `DataClient`를 사용하여 데이터를 전송합니다.

### 3. 스마트폰 앱 개발

1. **데이터 수신 리스너 설정**:
    
    - 스마트폰 앱에서 `WearableListenerService`를 확장하는 서비스를 구현하고, `onDataChanged` 메서드를 오버라이드하여 Wear OS 앱으로부터 전송된 데이터를 수신하고 처리합니다.
2. **UI 업데이트**:
    
    - 수신된 데이터를 사용하여 UI를 업데이트합니다. 예를 들어, 심박수, GPS 위치 등의 정보를 화면에 표시합니다.

### 4. 테스트 및 디버깅

1. **에뮬레이터 또는 실제 디바이스에서 테스트**: Wear OS 앱과 스마트폰 앱이 제대로 동작하는지 확인합니다.
2. **로그 및 디버깅**: Logcat을 활용하여 앱 실행 중 발생하는 이벤트와 오류를 모니터링합니다.

### 5. 배포 준비

- PoC가 성공적으로 완성되면, 앱을 Play Store에 배포하기 전에 최적화, 보안 검토, 및 사용자 테스트 단계를 거칩니다.

이 과정은 PoC 프로젝트에 필요한 기본적인 단계를 요약한 것입니다. 실제 개발 과정에서는 프로젝트의 요구 사항과 특성에 따라 추가적인 작업이 필요할 수 있습니다. Android 개발에 관련된 최신 가이드와 API 문서를 참고하면, 효율적으로 개발할 수 있습니다.



There are some cases that  you want to additianally support previous Android version.
For example, you made a Prototype with Newest Android version(Android14, APK 34)
But you now want to add Android 11~13.

One of my test environment was Android 12, so This is how I add Android 12 to the Android project.


라이브러리(SDK) + 샘플 앱 구성이었다.

1. 프로젝트에 해당하는 사설 라이브러리의 minSdk(gradle파일에 있다.) 를 31( Android12가 SDK로서 31)로 낮추고, build 버전을 Release로 변경한 후 AAR로 추출하여 어플에 옮겨넣는다. 

2. 어플의 minSdk를 31로 낮춘다. 

3. 그닥필요는 없지만 ,이때 Virtual device에서라도 돌아가는지 미리 확인해도 좋을 듯하다. 

4. Generate Signed app bundle/APK에서 사인을 생성해준다. 이거 안하면 테스트폰에서 절대 다운안됨. 

5. 테스트폰에서 출처를 알 수 없는 APK로 앱 설치 등을 가능하게 다 변경한다. 

6. APK를 테스트폰에서 실행해서 어플리케이션 설치. 여기서 제품반에서 지원한다고 할 경우 테스트 등을 제대로 수행하면 될 것으로 보인다. 또, permission이 android12에서 새로 개편되는 등 새로 지원하고 싶은 버전의 permission에 변경이 있을 지 확인 해야한다.
Android 스튜디오에서 **View > Tool Windows > Resource Manager**(보기 > 도구창 > Resource Manager)를 클릭하거나
**Project**(프로젝트) 창 옆에 있는 **Resource Manager** 탭을 클릭합니다.



6. **+(모듈에 리소스 추가) > Import Drawables**(드로어블 가져오기)를 클릭합니다.

![a85b707150fcff9a.png](https://developer.android.com/static/codelabs/basic-android-kotlin-compose-add-images/img/a85b707150fcff9a.png?hl=ko| 40m)




간단한 프로젝트에서 볼 수 있는 파일 계층 구조의 예는 다음과 같습니다.

```
MyProject/
	src/        
		MyActivity.kt   
	res/        
		drawable/           이미지 리소스용
			 graphic.png        
		mipmap/            런처 아이콘용
			icon.png        
		values/             문자열 리소스용
			strings.xml
```

### 리소스 액세스

Jetpack Compose -  Android 프로젝트에 정의된 리소스에 접근 가능.
프로젝트의 `R` 클래스에서 생성된 리소스 ID로 리소스에 액세스

`R` Class ->  Android에서 자동으로 생성되는 클래스
프로젝트에 있는 모든 리소스의 ID를 포함

대부분의 경우 리소스 ID는 파일 이름과 동일
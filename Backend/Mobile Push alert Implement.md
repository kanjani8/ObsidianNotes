가능한 방식 중 대표적인 4가지

1. FCM 직접 사용 - AWS Lambda 함수에서  FCM 어세스 토큰을 최신으로 갱신한 후,데이터베이스에서 필요 그룹을 찾아 해당 그룹의 FCM 디바이스 토큰을 모아서 FCM에 직접 전송하는 방식. 
	- 기존 서비스가 이미 구축되었을 경우, 그리고 모바일 푸쉬 알림만을 사용하는 경우 쓸만함.
	- FCM의 경우 아래 SNS, OneSignal,Firestore과 달리 완전히 제한없이 무료임. 즉, 람다함수를 돌리는데만 비용이 듬.
2. AWS SNS, OneSignal 등 알림 송신 서비스를 이용하는 방식. 
		 안드로이드 모바일 푸쉬 알림 뿐만 아니라 메일 알림, SMS 알림 등 다른 여러가지 알림 서비스를 함께 이용할 때 관리하기 편함. 모바일 푸쉬 알림만을 사용하는 경우 불필요하게 추가 서비스를 경유하는 형태이기 때문에 전혀 필요 없음.

3. Firestore을 사용하는 방식.
		Firebase의 데이터베이스인데, 데이터를 등록함에 맞춰 이벤트를 발생시킬 수 있고, 이 이벤트를 FCM을 통해 던지던(?), 코틀린언어로 던지던 할 수 있는것으로 보임. 하지만 이것은 데이터베이스를 아직 구축하기 전에 더 쓸모 있을 것으로 보이며, Firestore데이터베이스의 무료 사용가능 용량이 매우 적음.



-----------------------

#### 0. 안드로이드  라이브러리: FCM SDK 설정 및 디바이스 토큰 발급:

- 안드로이드 앱에 FCM SDK를 설치: Gradle 파일에 필요한 종속성을 포함하고 사용하도록 구성하여 FCM SDK를 안드로이드 프로젝트에 추가
디바이스 토큰 요청: 나중에 특정 디바이스로 푸시 알림을 전송하는 데 사용할 디바이스 토큰을 요청하고 받으려면 FCM SDK를 사용합니다.
새로운 HTTP 호출 알림 버튼: 알림 버튼을 누를 때 트리거되는 새로운 HTTP 호출을 Android 앱 내에서 구현합니다. 이 호출은 백엔드에 요청을 전송하여 디바이스 토큰 및 그룹 정보를 기반으로 푸시 알림을 전송하는 프로세스를 시작합니다.
#### 1. 백엔드: Firebase 프로젝트 생성 및 기본 설정:

Firebase 콘솔에서 Firebase 프로젝트를 생성합니다: Firebase 콘솔에 액세스하여 새 프로젝트를 생성합니다(Firebase 프로젝트는 Google Cloud 프로젝트의 일부이므로 표준 Google 계정이 필요합니다).
서비스 계정을 만듭니다: Google Cloud 콘솔에서 이전에 만든 프로젝트를 선택하고 새 서비스 계정을 만듭니다.
서비스 계정 자격 증명 다운로드: 서비스 계정 생성에서 JSON 형식의 자격 증명 파일을 다운로드합니다. 이 파일은 나중에 OAuth 2.0 인증에 사용됩니다.
#### 2.  백엔드: 람다 함수 만들기 함수를 수정합니다:

RDS에 장치 토큰 저장: 사용자 정보를 RDS에 저장하는 람다 함수를 수정하여 장치 토큰도 저장합니다(고유한 값이므로 기존 장치 UUID를 대체할 수 있음).


#### 4.  Backend:  alert 람다함수 생성
- FCM HTTP v1 API 사용: Alert 버튼을 누르면 호출될 람다함수 생성. 
##### SNS를 사용하지 않는 경우
- OAuth 2.0 인증 설정: 매번 서비스 계정 자격 증명(JSON 파일)을 사용하여  OAuth 2.0 액세스 토큰이 만료되었는지 확인 후 필요시 새로 액세스 토큰을 발급받도록 설정. 
- **푸시 알림 전송:** RDS에서 같은 비콘과 가까이 있는 사용자들의 디바이스 토큰을 검색한 후, FCM HTTP v1 API 엔드포인트(`https://fcm.googleapis.com/v1/projects/PROJECT_ID/messages:send`)로 직접 푸시 알림 요청 
##### SNS를 사용할 경우 
4-1 AWS SNS에서 Topic을 생성 해둔다. 

Case 1:  Alert 버튼을 눌렀을 때 SNS 그룹 설정 후 메시지 전송 
- **Alert-Lambda 함수:** alert버튼이 눌리면 호출됨. 
- **그룹 검색:** Alert 버튼이 눌리면 RDS에서 같은 비콘 근처에 있는 사용자들을 검색 
- **SNS 호출:** 검색된 디바이스 토큰을 SNS 주제에 구독자로 등록하고, FCM OAuth 2.0 토큰을 SNS에 추가하여, SNS가 푸시 알림을 전송하도록 요청 
- **SNS-Lambda 함수:** SNS에 의해 호출됨: 
- **OAuth 2.0 인증:** 이 함수는 OAuth 2.0 액세스 토큰이 만료되었는지 확인하고, 필요 시 새로 발급받은 후, FCM HTTP v1 API 엔드포인트로 푸시 알림을 전송합니다. Note: This method is inefficient as there's no need to register tokens to the SNS Topic for every alert. It could also be time-consuming.

Case 2: 정기적으로 그룹 설정 
- **Alert-Lambda 함수 (정기적 업데이트):** 다음을 수행하는 Lambda 함수를 생성합니다: 
- **정기적 그룹 검색:** 일정 주기(예: 30분)마다 RDS에서 같은 비콘 근처에 있는 사용자들을 검색 
- **SNS 호출:** 검색된 디바이스 토큰을 SNS 주제에 구독자로 등록하고, FCM OAuth 2.0 토큰을 SNS에 추가하여, SNS가 FCM HTTP v1 API 엔드포인트로 푸시 알림을 전송하도록 요청 
- **SNS-Lambda 함수:** Case 1과 유사하게, 이 함수는:
- **OAuth 2.0 인증:** 액세스 토큰을 확인하고, 필요시 갱신하여 FCM HTTP v1 API 엔드포인트로 푸시 알림을 전송합니다.
Note: Regular updates need to occur as frequently as location updates (e.g., every 30 seconds), which might be inefficient.
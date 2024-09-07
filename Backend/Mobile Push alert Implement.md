
# FCM vs AWS SNS vs OneSignal vs Firestore 리얼타임 메시징 서비스 비교

## 개요

리얼타임 메시징 서비스는 광의적으로 이메일, SMS, 푸시 알림, HTTP 등 다양한 형태로 제공될 수 있습니다. 하지만, 본 보고서에서는 보다 협의적인 의미로서 앱 내에서 사용자에게 리얼타임으로 제공되는 푸시 알림에 초점을 맞추어 다루겠습니다.

이 문서의 목적은 다음 리얼타임 메시징 서비스의 장점과 단점을 제시하는 것입니다:

- **OneSignal**
- **Amazon SNS (Simple Notification Service)**
- **Google FCM (Firebase Cloud Messaging)**
- **Google Firestore**: Google Firestore는 데이터베이스 서비스로, 메시징 서비스는 아니지만 이벤트에 기반한 알림 트리거 기능을 제공합니다.

## 푸시 알림 메시지 전송 서비스

다음 푸시 알림 서비스 중 하나를 사용하여 모바일 디바이스와 데스크탑에 푸시 알림 메시지를 전송할 수 있습니다:

- Amazon Device Messaging (ADM)
- Apple Push Notification Service (APNs) for iOS and Mac OS X
- Baidu Cloud Push (Baidu)
- Firebase Cloud Messaging (FCM)
- Microsoft Push Notification Service for Windows Phone (MPNS)
- Windows Push Notification Services (WNS)

**FCM (Firebase Cloud Messaging)**은 Google이 제공하는 무료 크로스 플랫폼 메시징 솔루션으로, 이전의 Google Cloud Messaging(GCM)에서 확장된 형태입니다. 주로 Android 디바이스에 푸시 알림을 전송하는 데 널리 사용됩니다.

OneSignal이나 Amazon SNS를 사용하는 경우에도 Android 푸시 알림에는 FCM이 사용되므로, 어떤 서비스를 사용하든 Firebase 계정(일반적인 Google 계정)의 제공이 필요합니다.

## 서비스 비교

| 서비스      | 플랜         | 가격     | 라이선스                | 난이도 | 장점                                                                                       | 단점                                                                                             | 알림 전송 수         |
|-------------|--------------|----------|-------------------------|--------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|---------------------|
| **OneSignal** | Free Plan    | 무료     | Modified MIT License     | 중      | - 향후 모바일 Push 알림 외의 알림 서비스 추가 시 유용<br>- 엔지니어에게 경험 있음          | - 알림 전송 수 제한<br>- Firebase 및 OneSignal 계정 필요<br>- FCM 단독 구성보다 Lambda 구조 복잡 및 비용 발생 | 매 초 최대 150건<br>15분마다 각 디바이스에 최대 10건 전송 가능 |
| **Google Firestore** | Spark Plan   | 무료     | 사유 소프트웨어 (라이선스 없음) | 높음   | - 향후 Firebase 시스템을 사용하는 경우 시스템 통합에 유리                                      | - 동시 디바이스 연결 최대 100대<br>- Firestore를 데이터베이스로 구축 및 사용해야 함<br>- 1일 최대 50K 읽기, 20K 쓰기, 20K 삭제 | 월 최대 10GB 데이터 전송 가능 |
| **Google FCM** (추천) | -            | 무료     | 사유 소프트웨어 (라이선스 없음) | 낮음   | - 완전 무료<br>- Lambda 함수 비교적 간단<br>- Firebase 계정만 필요                               | - 향후 크로스 플랫폼 지원 시 재구축 필요성 있음                                                      | 매 분 최대 60만 요청 |
| **Amazon SNS** | Free Tier   | 무료     | 사유 소프트웨어 (라이선스 없음) | 중      | - 향후 모바일 Push 알림 외의 알림 서비스 추가 시 유용<br>- AWS에 구축된 백엔드와 쉽게 통합 가능 | - FCM 단독 구성보다 Lambda 구조 복잡 및 비용 발생<br>- SNS에 보내는 사용자 그룹 매번 등록 비효율적       | 매 초 최대 1500건<br>총 100만 건의 알림까지 무료 |

**비교되는 장점과 단점은 프로젝트에 관련된 기능만 다루었습니다.**

## 결론

- ==**Google FCM**==: 제한 없이 완전 무료이며, Lambda 함수도 비교적 간단하게 설정 가능하고, 전체 비용도 발생하지 않기 때문에 모바일 Push 알림만 사용하는 PoC(Proof of Concept)에서는 가장 추천됩니다.
- **Amazon SNS**: AWS에 구축된 백엔드와 쉽게 통합 가능하며, FCM의 액세스 토큰 발급도 지원하지만, Lambda와 FCM만으로도 충분히 구현 가능하기 때문에, 모바일 Push 알림만 사용하는 PoC에서는 추천되지 않습니다.
- **OneSignal**: 무료이고 백엔드 엔지니어가 이 서비스의 사용 경험이 있어 Amazon SNS와의 구성 난이도가 크게 차이나지 않지만, 마찬가지로 Lambda와 FCM만으로도 충분히 구현 가능하기 때문에 모바일 Push 알림만 사용하는 PoC에서는 추천되지 않습니다.
- **Google Firestore**: 무료이지만 데이터베이스 재구축 등의 작업이 필요하여 이미 구축된 시스템 설계를 크게 변경해야 하는 점이 우려됩니다.

## 참고 자료

| 서비스 이름   | 기본 서비스                  | 사용 기술                                          | 설명                                                                  |
|--------------|------------------------------|--------------------------------------------------|----------------------------------------------------------------------|
| **OneSignal** | FCM (Firebase Cloud Messaging) | FCM, 독자적인 BaaS 기능                             | 독자적인 BaaS 기능을 제공하며, FCM을 통해 푸시 알림을 전송합니다.         |
| **Amazon SNS** | FCM (Firebase Cloud Messaging) | 다양한 프로토콜 지원 + FCM                          | 다양한 프로토콜을 지원하지만, Android 푸시 알림에는 FCM을 사용합니다.   |
| **Firestore** | FCM (Firebase Cloud Messaging) | Firestore + Cloud Functions + FCM                 | Firestore 변경 이벤트를 Cloud Functions로 처리하며, FCM을 통해 푸시 알림을 전송합니다. |

**BaaS(Backend as a Service)**
클라우드 기반 서비스로, 개발자가 서버 사이드 코드를 직접 작성하지 않고도 백엔드 기능을 쉽게 이용할 수 있게 해줍니다. 예를 들어, 데이터베이스 관리, 사용자 인증, 서버 측 로직 등의 기능이 BaaS에서 제공됩니다. 
**OneSignal**
 푸시 알림 서비스와 함께 푸시 알림에 특화된 BaaS 기능을 제공하여 백엔드 서버 측 기능을 쉽게 다룰 수 있게 합니다. 예를 들어, 사용자가 직접 서버를 관리하지 않고도, OneSignal을 통해 알림 설정, 사용자 세분화, 분석 등을 간편하게 관리할 수 있습니다.

## Push Notification System Setup (SNS, direct FCM case)

1. **Library**: FCM SDK 설치 및 디바이스 토큰 발급
   - Android 앱에 FCM SDK 설치: Gradle 파일에 필요한 종속성을 추가하고, FCM SDK를 프로젝트에 설정합니다.
   - 디바이스 토큰 요청: FCM SDK를 사용하여 디바이스 토큰을 요청하고 발급받습니다.
   - 알림 버튼을 위한 새로운 HTTP 호출 구현: 알림 버튼이 눌렸을 때 트리거되는 새로운 HTTP 호출을 구현합니다.
   - FCM SDK를 사용하여 알림 수신 기능 구현: FCM SDK를 사용하여 Android 앱에서 푸시 알림을 수신하는 기능을 구현합니다. 앱은 SNS 또는 FCM에서 메시지를 수신하면 경고를 표시해야 합니다.

2. **Backend**: Firebase 프로젝트 생성 및 기본 설정
   - Firebase Console에서 Firebase 프로젝트 생성: Firebase 콘솔에 접근하여 새 프로젝트를 생성합니다(표준 Google 계정 필요).
   - 서비스 계정 생성: Google Cloud Console에서 이전에 생성한 프로젝트를 선택하고 새 서비스 계정을 생성합니다.
   - 서비스 계정 자격 증명 다운로드: 서비스 계정 생성 시 JSON 형식의 자격 증명 파일을 다운로드합니다. 이 파일은 OAuth 2.0 인증에 사용됩니다.

3. **Backend**: Lambda 함수 수정
   - RDS에 디바이스 토큰 저장: 사용자 정보를 RDS에 저장하는 Lambda 함수를 수정하여 디바이스 토큰도 저장하도록 합니다(이 값은 고유하므로 기존 디바이스 UUID를 대체할 수 있습니다).

4. **Backend**: 알림 Lambda 함수 생성 - FCM HTTP v1 API 사용
   - 알림 버튼이 눌렸을 때 트리거되는 Lambda 함수를 생성합니다.
     - SNS를 사용하지 않는 경우:
       - OAuth 2.0 인증: 서비스 계정 자격 증명(JSON 파일)을 사용하여 OAuth 2.0 액세스 토큰이 만료되었는지 확인하고, 필요 시 갱신합니다.
       - 푸시 알림 전송: RDS에서 동일한 비콘 근처의 사용자 디바이스 토큰을 검색하고, FCM HTTP v1 API 엔드포인트(예: https://fcm.googleapis.com/v1/projects/PROJECT_ID/messages:send)에 직접 푸시 알림 요청을 전송합니다.
     - SNS를 사용하는 경우:
       - 알림 버튼이 눌렸을 때 SNS 그룹 설정 후 메시지 전송
       - SNS에서 플랫폼 애플리케이션 생성: Amazon SNS에서 플랫폼 애플리케이션 객체를 설정하고, 인증 방법으로 "토큰"을 선택합니다.
       - 서비스계정 자격 증명 등록: 서비스 계정 자격 증명(JSON 파일)을 사용하여 SNS에 인증 및 등록합니다.
       - RDS에서 디바이스 토큰 조회: RDS 데이터베이스에서 관련 비콘(위치 테이블의 비콘 ID로 식별됨) 근처의 사용자 디바이스 토큰을 검색합니다.
       - 플랫폼 엔드포인트 생성: 디바이스 토큰과 PlatformApplicationArn을 사용하여 각 사용자를 위한 플랫폼 엔드포인트 객체(EndpointArn)를 생성합니다.
       - 푸시 알림 전송: EndpointArn을 사용하여 Amazon SNS를 통해 사용자의 모바일 디바이스에 앱으로 메시지를 게시합니다.

## 결론
 모바일 푸시 알림만 전송하며, 전송 대상 그룹이 시시각각 변하는 경우, 직접 FCM을 사용하는 것이 SNS(및 아마도 OneSignal)보다  더 적합합니다.

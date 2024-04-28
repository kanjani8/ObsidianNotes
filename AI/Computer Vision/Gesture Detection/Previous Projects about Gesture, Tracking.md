## 행동 감지 관련 이전 프로젝트

### 

Jetson 양산형 하드웨어 솔루션 제공 , AI solution, 영상 처리  A회사
+RealSenseカメラのご提供

하드웨어（ワイドアングルカメラ、エッジAIボード）
#### 1-1. COVID-19対応入退出システム
2020년 프로젝트
간단한 솔루션으로,  Jetpack SDK를 사용하여
'출입 시 얼굴 인증 및 체온 측정', '리테일 매장 내 방문자 체류 분석'
이 두 가지 기능의 프로그램을 개발.

Jetson Nano + Jetpack SDK 4.3+ Deep stream
Dlibの顔認証 face_recognition

gstreamer로 카메라에서 받은 실시간 영상 처리
OpenCV (+Haar Cascades) 로 비디오 캡쳐 및 얼굴 인식 

#### 1-2. 소매 상점 내 고객 트렉킹
2020년 동시 진행 플젝
매장 내 방문자 체류 분석 서브시스템 프로토타입
Jetson Nano +USB camera +  Jetpack SDK 4.3 + Deep stream
Microsoft Azure IoT Hub と MQTT연계로 데이터 분석

방문자를 개별적으로 식별, 입점부터 퇴점까지의 위치 정보를 시계열로 추적.
특정 위치에 일정 시간 이상 체류할 경우, 다른 단말기에 경고 메시지를 전송(예: 매장 내 관리 단말기, 점원 스마트폰 등)


#### 2. AI사람 감지 센서, 스마트 조명 시스템
- 2021년초 플젝
- 애자일 방식으로 개발됨. ４名から８名で２週間から１か月間程度のバックログ

소규모 사무실에서 사용하기 좋은,
 사람이 없으면 불을 꺼주는 등의 스마트 조명 시스템

 통행인을 검출해서 그 진행방향과 속도까지 측정
 혹은 앉아잇는 사람을 검출해서 바라보는 방향을 검출

사용 하드웨어 엣지디바이스
 **NVIDIA Jetson Nano** <--  Deepstream 을 위해서는 필수.

**사용 모델, 데이터셋, 프레임워크**
NVIDIA Deepstream SDK안에서 
트래킹을 통한 동선 분석 및 속도 추정 (e.g. PeopleNet, YOLO4 + SORT) + COCO dataset
자세 추정을 통한 착석 시 신체 방향 추정 (e.g. OpenPose, PoseFlow) + ITOP dataset 

각 모델들은 Deep stream 안에서 쓸 수 있도록 ==TensorRT 호환 포맷으로 변환==.


- ITOP data set (taken by Depth camera)
	인체 자세 추정을 위해 특별히 설계된 데이터셋 중 하나로, 깊이 카메라(depth camera)를 사용하여 수집된 데이터를 기반으로 합니다.


#### 3.C의대 실습 고객이 DICOM뷰어를 마우스 없이 비접촉으로 조작

2022년 10월~ 프로젝트
[[MediaPipe ]]사용
하드웨어는 **Intel NUC PC、RealSense D435を使用** 사용.
Object detection - Landmark detection - Gesture detection



#### 공장 내 인물 감지 및 위험구역에 침입감지
2021년 8월~10월 프로젝트

NVIDIA Jetson TX2 + Optical 카메라 사용.
DeepStream 프레임 워크를 사용.  <- NVIDIA 제품 없으면 불가능

모델은 [[Model Zoo & Hugging Face#Model Zoo]] 에서 사전 학습된 모델을 찾아서 사용.

NVIDIA DeepStream SDK는 실시간 비디오 분석을 위한 프레임워크로, 
그 중 `gst-nvinfer`와 `gst-nvtracker`플러그인을 사용.

비스듬히 카메라 촬영-->  인물의 위치를 평면상에 변환-->
차나 사람이 위험 지역에 들어가면 알림이 가게 함.

MQTT 프로토콜 사용.
모바일 앱에서 카메라 화면을 확인할 수 있게 함.

약 3개월 플젝

-------------

한국 연구 사례
[[YOLO＋ DeepSORT를 활용한 School Safety Monitoring System Development]]
한국 학교 스마트 카메라 
2022년말 프로젝트

Deep sort - 실시간으로 다중 객체 추적을 할 수 있는 SORT의 확장 모델
Jetson Xavier AGX 사용 

------------
중간정리: 
人体姿勢推定のためにOpenPose, PoseFlowのようなモデルを使用する場合、そしてJetson NanoのようなNvideaデバイスに使用するためには、TensorRT互換フォーマットに変換してDeepstreamフレームワーク上でビデオ分析を行うことができます。
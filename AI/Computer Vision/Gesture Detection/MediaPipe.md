-  Google이 개발한 오픈 소스 프레임워크
-  머신 러닝을 활용한 멀티모달(예: 비디오, 오디오, 시간적 데이터 포인트 등) 인터랙션을 위해 설계됨.
- 이 프레임워크는 주로 ==실시간 컴퓨터 비전 애플리케이션==에 사용됨.
- 다양한 사전 훈련된 모델과 사용자 정의 모델을 통합하여 비디오, 이미지, 오디오 분석 등을 수행할 수 있음.

MediaPipe의 주요 특징은 다음과 같습니다:

1. **실시간 성능**: 최적화된 파이프라인을 통해 실시간으로 데이터를 처리하고 분석할 수 있습니다.
2. **크로스 플랫폼 지원**: Android, iOS, 웹, 데스크탑 등 다양한 플랫폼에서 사용할 수 있습니다.
3. **모듈화 및 확장성**: 사용자는 필요에 따라 모듈을 추가하거나 제거하여 애플리케이션을 맞춤 설정할 수 있습니다.
4. **다양한 API 지원**: MediaPipe는 카메라, 손동작 인식, 얼굴 감지, 얼굴 랜드마크 인식 등 다양한 컴퓨터 비전 관련 기능을 제공합니다.

이 프레임워크는 학계, 연구, 상업적 애플리케이션에서 널리 사용되며, 특히 AR 경험, 감정 분석, 가상 시도 등에 유용하게 사용됩니다. MediaPipe의 유연성과 다양한 기능으로 인해 개발자와 연구자 사이에서 인기가 높습니다.


Hand Gesture Recognition + Mouse Input 선례
3개월 프로젝트.

 손을 감지해서 이미지 크롭 해서 손 랜드마크(트래킹 Mediapipe 사용)
Media pipe로 
- Frame Real Time Flow Limiter Block
- Hand Detection Block
- Detection to Rectangle Block
- Image Cropping Block
- Hand Landmark Block
이후 static handgesture, Dynamic Hand Gesture을 Detect
그로부터 Pynput 라이브러리로 마우스 입력 이벤트를 발생시킴.


사용된 카메라: #RealSenseD435  - 깊이를 인식 가능한 카메라.

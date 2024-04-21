## Comparative Analysis of CV Models for Face and Age Recognition

  

| Model Type                                                            | Resource Requirements                 | Accuracy | Raspberry Pi Suitability | Main Use Cases                                   | Specialized in Face Recognition | Potential in Age and Face Recognition                                         |
| --------------------------------------------------------------------- | ------------------------------------- | -------- | ------------------------ | ------------------------------------------------ | ------------------------------- | ----------------------------------------------------------------------------- |
| Latest Transformer Models (e.g., Improved Swin Transformer, SwinFace) | Very High                             | Highest  | ✖️                       | Advanced applications requiring high accuracy    | High                            | Excellent performance in various face recognition tasks                       |
| CNN-based Models (e.g., VGGFace, AgeNet, GenderNet, Inception)        | Low                                   | High     | ⭕️                       | Real-time processing with high accuracy required | Very High                       | Potential to specialize in age recognition                                    |
| YOLO Models (e.g., YOLOv5, YOLOv8)                                    | Low (especially lightweight versions) | Medium   | ⭕️                       | Fast processing with sufficient general accuracy | Medium                          | Suitable for general face recognition but less specialized in age recognition |
  

| 모델 타입                                                | 리소스 요구사항      | 정확도 | 라즈베리파이 적합성 | 주요 사용 예                     | 얼굴 인식 특화 | 연령 인식 및 얼굴 인식 잠재력              |
| ---------------------------------------------------- | ------------- | --- | ---------- | --------------------------- | -------- | ------------------------------ |
| 최신 트랜스포머 모델 (Improved Swin Transformer, SwinFace)    | 매우 높음         | 최고  | ✖️         | 고급 애플리케이션에서 높은 정확도가 필요할 때   | 높음       | 다양한 얼굴 인식 작업에서 우수한 성능 가능       |
| CNN 기반 모델 (예: VGGFace, AgeNet, GenderNet, Inception) | 낮음            | 높음  | ⭕️         | 실시간 처리가 필요하고 높은 정확도가 요구될 때  | 매우 높음    | 연령 인식에 특화될 가능성이 있음             |
| YOLO 모델 (예: YOLOv5, YOLOv8)                          | 낮음 (특히 경량 버전) | 중   | ⭕️         | 고속 처리가 필요하고 일반적인 정확도가 충분할 때 | 중        | 일반적인 얼굴 인식에 적합하나 연령 인식에는 덜 특화됨 |

트랜스포머를 사용하려면 [[Transformer with Raspberry-pi#^07a3d9 |외부처리]]
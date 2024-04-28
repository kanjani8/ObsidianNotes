NVIDIA Jetson Nano, Jetson AGX Xavier, 그리고 Raspberry Pi Compute Module 4 (CM4)를 비교. 
### 1. 성능 및 하드웨어 사양
- **Jetson Nano**: 
	- ==GPU: 128-core Maxwell== 
	- CPU: Quad-core ARM Cortex-A57 
	- 메모리: 4GB LPDDR4 
	- 파워: 5-10W 
	- 소형 및 에너지 효율적. 가볍고 간단한 AI 작업에 적합합니다. 
	
- **Jetson AGX Xavier**: 
	- ==GPU: 512-core Volta GPU with 64 Tensor Cores==
	- CPU: 8-core NVIDIA Carmel ARMv8.2 
	- 메모리: 16-32GB LPDDR4x - 파워: 10-30W 
	- 고성능 AI 애플리케이션을 위해 설계되어 복잡하고 요구 사항이 높은 작업을 수행할 수 있습니다. 
	
- **Raspberry Pi Compute Module 4**: 
	- CPU: Broadcom BCM2711, Quad-core Cortex-A72 (ARM v8) 64-bit SoC 
	- 메모리: 1-8GB LPDDR4 
	- 파워: 상대적으로 낮은 전력 소비 
	- 일반적인 컴퓨팅 작업 및 학습용 프로젝트, 저비용 IoT 디바이스에 적합합니다.
	- GPU: Broadcom BCM2711 SoC가 내장된 VideoCore VI 그래픽 처리기를 사용합니다. 이는 일반적인 비디오 출력과 간단한 그래픽 작업을 지원하기 충분하지만, NVIDIA Jetson 시리즈처럼 고급 AI 및 딥러닝 작업을 위한 전용 GPU만큼의 성능은 제공하지 않습니다.
### 2. 비용 
- **Jetson Nano**는 저렴한 가격으로 AI 개발을 시작하고자 하는 개발자에게 적합합니다. 2만엔대 후반. 
- **Jetson AGX Xavier**는 고성능이 요구되는 프로젝트를 위해 더 높은 비용을 지불해야 하는 대신, 뛰어난 처리 능력을 제공합니다. 20만엔 
- **Raspberry Pi CM4**는 매우 경제적인 옵션으로, 광범위한 어플리케이션에 유연하게 사용될 수 있습니다. 1.5만엔~ 2만엔 
### 3. 사용 용도 및 커뮤니티 지원 
- **Jetson 시리즈**는 전문적인 AI 및 로봇공학 프로젝트, 실시간 이미지 처리 및 복잡한 컴퓨터 비전 태스크에 특히 강력한 지원을 제공합니다. NVIDIA의 강력한 생태계와 커뮤니티 지원을 통해 개발자는 다양한 리소스와 도구에 접근할 수 있습니다. 
- **Raspberry Pi CM4**는 교육, DIY 프로젝트, 소형 상업 제품 개발에 이상적입니다. 라즈베리 파이의 대규모 커뮤니티와 광범위한 문서는 시작하기에 좋은 환경을 제공합니다. 

### 결론 
Jetson 시리즈는 고성능 AI 컴퓨팅에, Raspberry Pi는 비용 효율적인 일반 컴퓨팅 및 기본적인 이미지 처리 작업에 적합합니다. 프로젝트의 목표에 따라 각각의 장점을 활용하는 것이 중요합니다.


#Raspberry-pi
#Jetson 
#Edge-device
#ComputerVision
#AI

### 1. **Terraform이란?**

- Terraform은 **인프라 코드(IaC, Infrastructure as Code)** 도구로, 클라우드 리소스를 선언적으로 정의하고 관리할 수 있게 해줍니다.
- **HashiCorp**에서 개발한 오픈 소스 도구이며, AWS뿐만 아니라 Google Cloud, Azure, Kubernetes, On-Premise 등 다양한 플랫폼과 통합할 수 있습니다.
- Terraform을 사용하면 코드(주로 `.tf` 파일)를 통해 클라우드 리소스를 생성, 변경, 삭제하는 작업을 자동화할 수 있습니다.

#### Terraform의 특징

- **클라우드 중립적**: AWS, Azure, Google Cloud 등 여러 클라우드 플랫폼에서 사용할 수 있음.
- **선언적 방식**: 리소스의 "최종 상태"를 정의하면, Terraform이 해당 상태에 도달하기 위한 작업을 알아서 수행.
- **계획 기능 (`terraform plan`)**: 실제 적용 전에 변경 내용을 미리 확인 가능.
- **상태 관리**: Terraform이 리소스의 현재 상태를 저장하여 변경 사항을 추적.
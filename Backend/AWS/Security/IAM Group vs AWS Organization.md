

### 주요 차이점 요약

|**특징**|**IAM 그룹**|**AWS Organizations**|
|---|---|---|
|**적용 범위**|단일 계정 내 사용자 관리|여러 AWS 계정의 중앙 관리|
|**관리 대상**|IAM 사용자|AWS 계정|
|**정책 적용 단위**|IAM 그룹 (사용자 그룹)|조직(Organization) 또는 OU(조직 단위)|
|**주요 기능**|권한 할당, 사용자 관리|계정 간 SCP 적용, 청구 통합, 계정 거버넌스|
|**사용 사례**|팀별 사용자 권한 관리|대규모 조직의 여러 계정 관리|


---

### IAM 그룹 (Identity and Access Management Group)

- **목적**: AWS 리소스에 대한 **사용자 수준**의 접근 제어를 효율적으로 관리하기 위해 사용.
- **적용 대상**: 개별 사용자 계정 (IAM User).
- **기능**:
    - IAM 사용자를 그룹화하여 동일한 권한을 할당 가능.
    - IAM 정책을 그룹에 적용하면, 그룹에 속한 모든 사용자가 동일한 권한을 상속받음.
    - 예: 개발자 그룹, 운영 그룹, 관리자 그룹 등으로 나눠 각각 다른 권한 부여.
- **주요 특징**:
    - **단일 계정 내**에서만 작동.
    - 계정 간 권한 관리 기능이 없음.
    - AWS 계정을 초과하는 범위에서 사용할 수 없음.

---

### AWS Organizations

- **목적**: ==여러 AWS 계정==을 **조직 수준**에서 관리하고 비용, 보안, 거버넌스를 중앙에서 통제하기 위해 사용.
- **적용 대상**: AWS 계정 전체.
- **기능**:
    - 여러 AWS 계정을 하나의 조직(Organization)으로 묶어서 중앙에서 관리 가능.
    - **서비스 제어 정책(SCP)**을 사용하여 조직 내 계정 또는 OU(조직 단위)에 대한 허용/제한 정책을 설정 가능.
    - 예: 프로덕션 계정 그룹에 엄격한 정책 적용, 테스트 계정 그룹에 유연한 정책 적용.
    - 청구 관리(Consolidated Billing)를 통해 모든 계정의 비용을 통합 관리 가능.
- **주요 특징**:
    - **다중 계정 관리**에 최적화.
    - 계정을 조직 단위로 나눠 세부적으로 제어 가능 (OU 구조).
    - 단일 계정 내에서의 사용자 관리보다는 **계정 관리 및 거버넌스**가 초점.


---

### 사용 예시

1. **IAM 그룹**:
    
    - "개발자 팀"을 위한 IAM 그룹을 생성하고, EC2, S3에 대한 읽기/쓰기 권한을 부여.
    - "운영 팀"에는 Lambda와 CloudWatch 접근 권한만 부여.
2. **AWS Organizations**:
    
    - "프로덕션 계정" OU에는 보안 강화를 위한 SCP를 적용하여 S3 버킷 삭제를 금지.
    - "개발 계정" OU는 모든 리소스를 자유롭게 생성할 수 있도록 허용.



필요에 따라 두 기능을 조합해 사용하는 것이 일반적입니다. 😊
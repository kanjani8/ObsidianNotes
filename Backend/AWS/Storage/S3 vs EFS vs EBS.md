


---

### **S3, EFS, EBS 비교표**

| **특징**           | **Amazon S3**            | **Amazon EFS**              | **Amazon EBS**          |
| ---------------- | ------------------------ | --------------------------- | ----------------------- |
| **스토리지 유형**      | 객체 스토리지 (Object Storage) | 네트워크 파일 스토리지 (File Storage) | 블록 스토리지 (Block Storage) |
| **데이터 접근 방식**    | 키-값 쌍으로 데이터 접근           | 파일 시스템 (POSIX 호환)           | 블록 단위로 데이터 접근           |
| **데이터 공유 가능 여부** | 글로벌 데이터 공유 가능            | 여러 EC2 인스턴스에서 동시에 접근 가능     | 단일 EC2 인스턴스 전용          |
| **데이터 구조**       | 비정형 데이터 (JSON, 이미지 등)    | 파일 및 디렉토리 구조                | 로컬 디스크처럼 사용             |
| **자동 확장 지원**     | ✔ 자동 확장                  | ✔ 자동 확장                     | ✘ 수동 확장 필요              |
| **사용 사례**        | 백업, 로그 저장, 대용량 데이터 분석    | 다중 인스턴스 데이터 공유, 파일 저장       | 데이터베이스, 고성능 애플리케이션      |
| **성능**           | 대규모 데이터 처리에 최적화          | 다중 인스턴스에서 읽기/쓰기 가능          | 고성능 및 저지연 작업            |
| **비용 (GB당)**     | 매우 저렴 ($0.023/GB)        | 중간 ($0.30/GB)               | 중간 ($0.05~$0.08/GB)     |

---

### **세 서비스의 주요 차이점**

#### **1. Amazon S3 (객체 스토리지)**

- **특징**:
    
    - 데이터를 **객체 단위**로 저장하며, 각 객체는 고유한 키(Key)로 식별됨.
    - **비정형 데이터**(이미지, 동영상, 로그, JSON 파일 등)를 저장하는 데 적합.
    - 서버리스 서비스로 글로벌 데이터 접근 가능.
- **사용 사례**:
    
    1. **백업 및 로그 저장**:
        - 장기적으로 데이터를 저장하고, 비정기적으로 접근하는 경우.
        - 예: 애플리케이션 로그, 데이터베이스 백업.
    2. **정적 웹사이트 호스팅**:
        - HTML, CSS, 이미지 등 정적 파일 저장.
        - 예: Amazon CloudFront와 통합하여 글로벌 콘텐츠 제공.
    3. **대규모 데이터 분석**:
        - 머신러닝/데이터 분석에서 대량의 비정형 데이터를 저장.
        - 예: IoT 센서 데이터.

---

#### **2. Amazon EFS (네트워크 파일 스토리지)**

- **특징**:
    
    - 데이터를 **파일 시스템 형식(POSIX 호환)**으로 저장.
    - 여러 EC2 인스턴스에서 **동시에 접근** 가능.
    - 데이터 크기가 자동으로 확장되고 축소됨.
- **사용 사례**:
    
    1. **파일 공유**:
        - 여러 애플리케이션에서 데이터를 동시에 읽고 써야 할 때.
        - 예: 웹 서버 클러스터가 공통의 파일(이미지, HTML 등)을 공유.
    2. **컨테이너 기반 애플리케이션**:
        - Amazon ECS/EKS와 함께 파일 데이터를 공유.
        - 예: 로그 파일 저장, 컨테이너 간 데이터 공유.
    3. **병렬 데이터 처리**:
        - 대규모 병렬 작업에서 데이터를 공유 및 분석.
        - 예: 빅데이터, 머신러닝 워크로드.

---

#### **3. Amazon EBS (블록 스토리지)**

- **특징**:
    
    - 데이터를 **블록 단위**로 저장하며, EC2 인스턴스에 연결해서 로컬 디스크처럼 사용.
    - 고성능, 저지연 데이터 읽기/쓰기에 적합.
- **사용 사례**:
    
    1. **데이터베이스 스토리지**:
        - MySQL, PostgreSQL 등 고성능 데이터베이스에서 사용.
        - 예: OLTP(Online Transaction Processing) 워크로드.
    2. **운영 체제 디스크**:
        - EC2 인스턴스의 루트 디스크로 사용.
        - 예: 애플리케이션 실행 디스크.
    3. **고성능 워크로드**:
        - 밀리초 단위의 응답 속도가 필요한 경우.
        - 예: 실시간 로그 처리, 금융 애플리케이션.

---

### **어떤 상황에서 어떤 스토리지를 선택할까?**

|**조건**|**Amazon S3**|**Amazon EFS**|**Amazon EBS**|
|---|---|---|---|
|**대규모 데이터 분석**|✔|✘|✘|
|**여러 EC2 인스턴스에서 데이터 공유**|✘|✔|✘|
|**고성능, 저지연 작업**|✘|✘|✔|
|**비정형 데이터 (이미지, JSON 등)**|✔|✘|✘|
|**단일 EC2 인스턴스 전용 디스크**|✘|✘|✔|
|**파일 시스템 (POSIX 호환)**|✘|✔|✘|
|**장기 보관 및 백업**|✔|✘|✘|

---

### **예제 시나리오**

#### **1. 웹 서버 클러스터**

- **사용 스토리지**: **Amazon EFS**
    - 여러 EC2 인스턴스가 이미지와 HTML 파일을 공유해야 하므로 EFS가 적합.

#### **2. 머신러닝 데이터 저장 및 분석**

- **사용 스토리지**: **Amazon S3**
    - 대규모 데이터(IoT 센서 데이터)를 저장하고 분석할 때는 S3가 적합.

#### **3. 고성능 데이터베이스**

- **사용 스토리지**: **Amazon EBS**
    - EC2 인스턴스에서 실행되는 MySQL 데이터베이스는 고성능이 필요하므로 EBS가 적합.

#### **4. 데이터 백업 및 복구**

- **사용 스토리지**: **Amazon S3**
    - 장기 보관이 필요하고, 데이터 접근 빈도가 낮으므로 S3가 적합.

---

### **결론**

- **Amazon S3**: **비정형 데이터**, **백업/아카이브**, **대규모 데이터 분석**.
- **Amazon EFS**: **여러 인스턴스 간 데이터 공유**, **파일 시스템 기반 애플리케이션**.
- **Amazon EBS**: **고성능, 저지연 데이터 처리**, **단일 인스턴스 전용**.
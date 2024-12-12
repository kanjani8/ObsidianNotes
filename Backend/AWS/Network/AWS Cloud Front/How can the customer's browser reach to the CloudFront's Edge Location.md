- **고객이 웹사이트 요청**
    - 고객 브라우저: `www.anycompany.com` 요청
    - DNS (Route 53): CloudFront 배포 도메인(`d12345abcdefg.cloudfront.net`)에 해당하는 IP 주소(192.0.2.123) 반환
- **고객 브라우저 -> CloudFront 엣지 로케이션**
    - 고객 브라우저는 반환된 IP 주소(192.0.2.123)를 사용하여 가장 가까운 CloudFront 엣지 로케이션에 연결
    - 캐싱된 데이터가 있다면 여기서 바로 제공

- **CloudFront 엣지 로케이션 -> 원본 서버**
    - 엣지 로케이션에 캐싱된 데이터가 없거나 최신 데이터가 필요하면, CloudFront가 원본 서버로 요청 전송
    - 원본 서버는 Application Load Balancer 또는 EC2 인스턴스

- **결과 전달**
    - 데이터를 CloudFront 엣지 로케이션에서 다시 고객 브라우저로 전달

---

## Detail ver
### 1. **DNS 설정 (Route 53)**

고객이 웹사이트(예: `www.anycompany.com`)를 요청하면, 브라우저는 먼저 도메인 이름(`www.anycompany.com`)에 해당하는 **IP 주소**를 찾습니다. 이 과정은 다음 단계로 이루어집니다:

1. **도메인 이름 설정**  
    `www.anycompany.com`이 **CloudFront 배포의 도메인 이름**(예: `d12345abcdefg.cloudfront.net`)과 연결되어 있습니다.  
    이 설정은 Route 53 또는 다른 DNS 서비스에서 이루어집니다.  
    예:
    `CNAME 레코드: www.anycompany.com -> d12345abcdefg.cloudfront.net`
    
2. **DNS 조회**  
    고객의 브라우저는 `www.anycompany.com`을 DNS 서버에 물어보고, CloudFront 배포에 해당하는 IP 주소를 받습니다.  
    예:
    `www.anycompany.com -> 192.0.2.123 (CloudFront 엣지 로케이션의 IP)`
    

---

### 2. **고객 브라우저 -> CloudFront 엣지 로케이션**

1. **IP 주소 연결**  
    DNS가 반환한 IP 주소(192.0.2.123)는 실제로 **CloudFront 엣지 로케이션**의 IP입니다.  
    고객의 브라우저는 이 IP 주소를 사용하여 **가장 가까운 CloudFront 엣지 로케이션**에 연결합니다.
    
2. **엣지 로케이션에서 콘텐츠 제공**  
    CloudFront는 엣지 로케이션에 콘텐츠를 **캐싱**해 두기 때문에, 캐싱된 콘텐츠가 있다면 엣지 로케이션에서 바로 데이터를 제공합니다.  
    이 과정은 빠르고 효율적입니다.
    

---

### 3. **CloudFront 엣지 로케이션 -> 원본 서버**

엣지 로케이션에 캐싱된 데이터가 없거나 최신 데이터가 필요하면, CloudFront는 **원본 서버**(Origin)로 요청을 보냅니다.  
원본 서버는 보통 다음 중 하나로 설정됩니다:

- Application Load Balancer (ALB)  
    예: `my-alb-123456.us-east-1.elb.amazonaws.com`
- EC2 인스턴스  
    퍼블릭 IP 주소로 직접 연결 가능

CloudFront는 원본 서버에서 데이터를 받아 엣지 로케이션으로 저장하고, 이를 고객에게 전달합니다.
![[Pasted image 20241208150757.png]]

Reference; https://www.youtube.com/watch?v=-t148tYgnJU



### **1. 세이빙 플랜 (Savings Plans)**

- **유연성**:
    - 특정 인스턴스 유형에 고정되지 않고, 다양한 인스턴스 패밀리, 크기, OS, 리전에 걸쳐 적용 가능.
    - AWS Lambda와 Fargate 사용량에도 할인 적용 가능.
- **할인 방식**:
    - 시간당 사용량(USD 단위)을 약정하여 할인.
    - Compute Savings Plans: 모든 인스턴스에 유연하게 적용.
    - Instance Savings Plans: 특정 EC2 인스턴스 유형에 더 높은 할인율.
- **적용 범위**:
    - 인스턴스의 속성이 변경되거나 리전이 이동해도 할인이 유지됨.
- **할인율**:
    - 최대 66%~72%까지 할인.

---

### **2. 예약 인스턴스 (Reserved Instances)**

- **고정성**:
    - 특정 인스턴스 유형, OS, 테넌시, 리전에 고정됨.
    - 약정된 구성에만 할인 적용.
- **할인 방식**:
    - 1년 또는 3년 기간 약정.
    - 표준(Standard) RI: 변경 불가, 더 높은 할인율.
    - 컨버터블(Convertible) RI: 변경 가능, 낮은 할인율.
- **용량 예약**:
    - 특정 가용 영역에 용량 예약 가능.
    - 용량이 부족한 상황에서도 인스턴스를 실행할 수 있는 보장 제공.
- **할인율**:
    - 최대 72% 할인.

---

### **차이 요약**

|**특징**|**세이빙 플랜**|**예약 인스턴스**|
|---|---|---|
|**유연성**|인스턴스 구성과 리전에 구애받지 않음|특정 속성에 고정|
|**적용 서비스**|EC2, Fargate, Lambda|EC2에 한정|
|**기간**|1년 또는 3년|1년 또는 3년|
|**용량 예약**|지원하지 않음|특정 가용 영역에서 지원|

**결론**:

- ==유연성과 다양한 서비스 적용을 원한다면 **세이빙 플랜**.==
- ==특정 구성에 대한 고정 할인과 용량 예약이 필요하다면 **예약 인스턴스**를 선택.== 

---

<h2>1. Savings Plans</h2>
<ul>
	<li><strong>Flexibility:</strong> 
		Applies across various instance families, sizes, operating systems, and regions. 
		Can also be used with AWS Lambda and AWS Fargate.
	</li>
	<li><strong>Discount Mechanism:</strong> 
		Discounts are applied based on an hourly commitment (USD). 
		- Compute Savings Plans: Flexible across instances.
		- Instance Savings Plans: Higher discount rates for specific instances.
	</li>
	<li><strong>Discount Rate:</strong> Up to 66%-72% off on-demand prices.</li>
</ul>

<h2>2. Reserved Instances</h2>
<ul>
	<li><strong>Fixed Configurations:</strong> 
		Tied to specific instance types, operating systems, tenancy, and regions.
	</li>
	<li><strong>Discount Mechanism:</strong> 
		Requires a 1-year or 3-year term commitment.
		- Standard RI: Fixed configuration, higher discounts.
		- Convertible RI: Allows changes, lower discounts.
	</li>
	<li><strong>Capacity Reservation:</strong> 
		Can reserve capacity in specific availability zones.
	</li>
	<li><strong>Discount Rate:</strong> Up to 72% off on-demand prices.</li>
</ul>

<h2>Summary</h2>
<table border="1">
	<thead>
		<tr>
			<th>Feature</th>
			<th>Savings Plans</th>
			<th>Reserved Instances</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><strong>Flexibility</strong></td>
			<td>Applies to various configurations and services</td>
			<td>Tied to specific configurations</td>
		</tr>
		<tr>
			<td><strong>Applicable Services</strong></td>
			<td>EC2, Fargate, Lambda</td>
			<td>EC2 only</td>
		</tr>
		<tr>
			<td><strong>Term</strong></td>
			<td>1 year or 3 years</td>
			<td>1 year or 3 years</td>
		</tr>
		<tr>
			<td><strong>Capacity Reservation</strong></td>
			<td>Not available</td>
			<td>Available</td>
		</tr>
	</tbody>
</table>
<p><strong>Conclusion:</strong> Choose Savings Plans for flexibility and broad service coverage. Opt for Reserved Instances for specific configurations and capacity reservation.</p>


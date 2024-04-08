## SBOM (Software Bill of Materials)
### 1. SBOM의 정의
**SBOM(Software Bill of Materials)**

- 소프트웨어 자재 명세서
- 해당 소프트웨어 제품이 어떤 컴포넌트, 소프트웨어, 버전으로 구성되었는지 나타냄
- SBOM을 통해 제품의 구성 목록 식별 및 관리, 라이선스 점검, 보안 취약점 검증 수행 가능
- SBOM의 대표적 포맷
    - SPDX(Software Package Data Exchange)
    - SWID 태그(Software Identification Tags)
    - 사이클론DX(CycloneDX)

### 2. SBOM 배경

- 2021년, 미국 정부가 SW공급망 강화를 위해 행정명령([EO 14028](https://www.nist.gov/itl/executive-order-14028-improving-nations-cybersecurity))을 발표하고, SBOM을 제출하도록 함
- 소프트웨어의 재사용률 및 복잡도가 높아지면서 SW공급망을 통한 위협 사례가 증가하는 추세
    - 2021년 7월, 미국 SW기업 Kaseya의 원격 모니터링, 관리 도구 업데이트 채널을 통해 랜섬웨어가 침투되어 약 1,500개에 이르는 최종 고객사에 피해 발생
    - 2021년 12월, 자바 시스템 로깅 오픈소스 Log4j에서 취약점이 발견되어 이를 악용하는 사레가 기업 네트워크 48% 이상에서 감지
- 이러한 위협에 빠른 대응이 가능하도록 SW공급망의 투명성을 높이기 위해 SBOM 도입 권고

### 3. SBOM의 최소 요소

미국 전기통신 및 정보청(NTIA)에서 정의한 SBOM 최소요소

<b>3.1. 데이터 필드 (Data Fields)</b>
- 필수적으로 추적해야 할 각 구성요소와 기준 정보 문서화
    - 구성요소의 공급자, 이름, 버전, 식별자, 의존관계
    - SBOM 작성자, 작성일시

<b>3.2. 자동화 지원 (Automation Support)</b>
- SW 생태계 상에서의 적용을 위한 자동 생성 및 기계가독성 등을 포함한 자동화 지원
- SBOM 생성 및 소비를 위한 데이터 포맷으로 SPDX, CycloneDX, SWID tags 포함


<b>3.3. 지침 및 절차 (Practices and Processes)</b>
- SBOM  요청, 생성, 사용에 대한 운영 정의: 생성 빈도 수, SW구성요소 깊이, 알려진 무지(know unknow), 배포 및 전달, 접근 제어, 오류에 대한 양해
<br><br>

**(+) 데이터 필드의 최소 구성요소 7가지**

- 공급자 이름 : 구성요소를 만들고 정의하고 식별하는 주체의 이름
- 구성요소 이름 : 최초 공급자에 의해 정의된 소프트웨어 단위의 명칭
- 구성요소 버전 : 공급자가 이전에 식별된 소프트웨어 버전으로부터의 변경을 명시하기 위해 사용하는 식별자
- 기타 고유 식별자 : 구성요소를 식별하는 데 사용되거나 관련 데이터베이스를 위한 조회 키 역할을 하는 기타 식별자. 예를 들어 NIST의 CPE 사전의 식별자일 수 있다.
- 종속성 관계 : 업스트림 구성요소 X가 소프트웨어 Y에 포함된다는 관계의 명시. 오픈소스 프로젝트에서 특히 중요하다.
- SBOM 데이터 작성자 : 이 구성요소에 대한 SBOM 데이터를 만든 주체의 이름
- 타임스탬프 : SBOM 데이터 어셈블리의 날짜 및 시간 기록

**참고**

- [미국 SBOM(Software Bill of Materials) 정책 분석 및 시사점](https://www.globalict.kr/sbom/sbom.do?menuCode=040600&viewMode=view&boardno=40&datano=1)
- [소프트웨어 세계의 자재 명세서, SBOM이 필요한 이유](https://www.itworld.co.kr/news/246094)
- [The Minimum Elements For a Software Bill of Materials (SBOM) - NTIA](https://www.ntia.doc.gov/files/ntia/publications/sbom_minimum_elements_report.pdf)
- [Framing Software Component Transparency: Establishing a Common Software Bill of Material (SBOM)](https://www.ntia.gov/files/ntia/publications/framingsbom_20191112.pdf)
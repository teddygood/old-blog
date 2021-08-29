---  
title: "[Study] Data Engineering with Python 스터디 2주차"  
categories: Study  
tag:
  - datacamp
  - Data Engineering
  - PseudoLab
  - Python
  - SQL
date: 2021-08-28
---  

PseudoLab Data Science Fellowship 1기

---

# Inrtroduction to Data Engineering

## Introduction to Data Engineering

최악의 상황
- 데이터는 흩어져있음
- 분석에 최적화되어 있지 않음
- 레거시코드 때문에 데이터가 손상되어 있음

data engineer는 data scientist 삶을 편하게 함
- 여러 소스에서 데이터를 extract하고 single DB에 load
- 분석을 위하여 DB를 최적화하여 쿼리 속도를 빠르게 만듬
- 손상된 데이터도 제거
- 확장을 원하는 데이터 중심(data-driven) 회사에서 가장 가치있는 사람

데이터 엔지니어 정의
- DB와 large-scale processing system 같은 architecture를 개발, 구성, 테스트, 유지 관리하는 엔지니어
- 많은 양의 데이터를 처리
- 컴퓨팅을 수행하는 machine cluster를 사용 및 설정 -> virtual machine의 cluster
  - cluster: 고성능 컴퓨팅을 위해 여러 단말의 컴퓨터로 구성된 컴퓨터 집합

Data Engineer vs Data Scientist
- Data Engineer
  - 확장가능한 데이터 아키텍처 개발
  - 데이터 수집 간소화
  - 데이터를 가져오는 프로세스 설정
  - 손상된 데이터를 정리하여 데이터 보호
  - 클라우드 기술에 잘 알아야 함
- Data Scientist
  - 데이터 패턴을 찾기 위해 하는 데이터 마이닝
  - 대규모 데이터셋에 통계 모델 적용
  - 머신러닝으로 예측 모델 구축
  - 비즈니스 프로세스를 모니터링하는 도구 개발
  - cleaning 작업으로 이상치(outlier) 제거
  - 비즈니스에 대한 깊은 이해를 가짐

Database
- 간략하게 말하면 DB는 많은 양의 데이터를 보유하는 컴퓨터 시스템
- 애플리케이션은 특정 기능을 제공하기 위헤 DB에 의존

Processing
- clean, aggregate, join하기 위해 데이터 처리
- 엄청난 양의 데이터 처리
  - 병렬 처리
  - 한 컴퓨터에서 데이터 처리 -> virtual machine cluster를 사용하여 분산하여 데이터 처리
    - 이런 툴은 기본 아키텍처 추상화, 간단한 API 제공
    - e.g.
      ```python
      df = spark.read.parquet("users.parquet")
      outliers = df.filter(df["age"] > 100)
      print(outliers.count())
      ```

Scheduling
- 데이터가 특정 간격에 따라 적절한 시간에 한 장소에서 다른 장소로 이동하는지 확인
- 경우에 따라 처리 작업이 올바르게 작동하려면 특정 순서로 실행되어야 함
  - 시간에 맞게 실행되도록 하고 올바른 순서로 실행되도록 만듬
- 작업의 종속성이 올바르게 해결되어야 함

Existing tools
- Databases: MySQL, PostgreSQL
- Processing: Apache Spark, Apache Hive
- Scheduling: Apache Airflow, Oozie, cron

Data Pipeline
- DB와 연결하여 모든 데이터 Extract, Transform
- Spark 같은 cluster computing framework를 사용하여 analytical DB에 Load
- Airflow와 같은 scheduling framework를 통해 특정 순서로 실행되도록 scheduling
- source가 외부 API 또는 기타 파일 형식일 수도 있음

Data processing in the cloud
- 과거에는 자체 데이터 센터를 설립하여 서버 랙을 사용
  - 전기 요금, 유지관리 비용
  - 피크 타임에 충분한 처리 능력 필요 -> 사용이 없을 때는 처리 능력이 그대로 남아있음 -> 리소스 낭비
  - 재난을 대비해 데이터를 다른 지리적 위치에 복제 필요
- 클라우드
  - 리소스를 필요할 때 사용
  - 비용 최적화
  - DB 안정성 -> 재난 같은 최악의 상황에 대비

AWS, Azure, GCP
- 2017 AWS 중단 발생
- 2018 기준 점유율: AWS > Azure > GCP

Storage
- 모든 유형 파일 클라우드에 업로드
- 일반적으로 매우 저렴
- 파일 안정적으로 저장
- AWS S3, Azure Blob Storage, Google Cloud Storage

Computation
- 클라우드에서 계산 수행
- 가상머신을 원하는대로 사용 -> 필요에 따라 유연하게 시작, 중지
  - e.g. 웹 서버 호스팅
- AWS EC2, Azure Virtual Machines, Google Compute Engine
  
Database
- DB 호스팅
- AWS RDS, Azure SQL Database, Google Cloud SQL
  
## Data engineering toolbox

Database 정의
- 데이터 보유
- 데이터 구성
- DBMS를 통해 되찾아오거나 검색하는 데 도움이 됨 

DB와 File system 차이
- DB
  - 매우 조직화되어 있음
  - 검색, 복제 등과 같은 복잡한 작업들을 추상화
- File system
  - 덜 조직화되어 있음
  - 위와 같은 기능들이 간단하거나 덜함

Structured and unstructured data
- Structured: database schema
  - RDBMS의 테이블 형식 데이터
- Semi-structured
  - JSON
- Unstructured: shemaless, 파일과 더 비슷함
  - 비디오, 사진

SQL and NoSQL
- SQL
  - Tables
  - Database schema: 테이블 간의 관계, 속성 정의
  - RDBMS(Relational DataBase Management System)
  - Mysql, PostgreSQL
- NoSQL
  - Non-relational database
  - NoSQL DB에는 여러가지 유형이 있음
    - unstructured data만 연결되는 것이 아님 -> structured data도 연결
  - Key-value 저장(e.g. caching, 분산 구조)
  - Document DB(e.g. JSON object -> structured or unstructured object)
  - Redis, MongoDB

database schema
- DB의 구조와 관계 설명 
- e.g. 스키마 테이블 생성
  ```sql
  -- Create Customer Table
  CREATE TABLE "customer" (
    "id" SERIAL NOT NULL,
    "first_name" varchar,
    "last_name" varchar,
    PRIMARY KEY ("id")
  );

  -- Create Order Table
  CREATE TABLE "Order" (
    "id" SERIAL NOT NULL,
    "customer_id" integer REFERENCES "Customer",
    "product_name" varchar,
    "product_price" integer,
    PRIMARY KEY ("id")
  );
  ```
  - customer_id로 주문을 고객과 연결 -> foreign key
  - JOIN 문을 사용하여 테이블을 조인하여 외래 키 활용
## Extract, Transform and Load (ETL)

## Case Study: DataCamp
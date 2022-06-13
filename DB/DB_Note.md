# DataBase 정리



## INDEX			목차

### 1. 데이터베이스 개요

### 2. SQL

### 3. JDBC : Java + DB

### 4. 데이터 모델링



---

### 1. 데이터베이스 개요

- #### **데이터베이스 기본 개념**

  - **데이터와 정보**
  - **데이터 구조**
  - **DBMS**
  - **데이터베이스 언어**
  - **데이터베이스 발전 (DBMS의 종류)**
  - **관계형 데이터 모델**
  - **관계 데이터 제약**

  

---

#### 1) 데이터와 정보

- **데이터(Data)**

  - 관찰이나 측정을 통해 수집된 **사실(facts)**이나 **값(value)**

  - 정량적 또는 정성적인 **실제 값**

    


- **정보(Information)**

  - 의사결정에 도움이 되도록 데이터를 의미있는 패턴으로 정리한 것

  - 데이터에 **의미를 부여**한 것

  

---

#### 2) 데이터의 구조

- **논리적 구조(logical organization)**
  - **사용자의 관점**에서 본 데이터의 **개념적** 구조
  - 데이터의 **논리적 배치**
  - 논리적 레코드



- **물리적 구조(physical organization)**
  - **저장 관점**에서 본 데이터의 **물리적** 배치
  - 저장장치에 저장된 데이터의 **실제 구조**
  - 물리적 레코드



---

#### 3) DBMS

- **데이터베이스**
  - **데이터의 집합체**
  - 조직에 필요한 정보를 얻기 위해 **논리적으로 연관된 데이터**를 모아 **구조적으로 통합**해 놓은 것
  - **여러 사용자나 응용프로그램이 공유**
  - **동시 접근** 가능



- **데이터베이스 관리 시스템(DataBase Management System)**

  - 데이터베이스를 관리해주는 소프트웨어 시스템

    ex) Oracle, MS SQL Server, MySQL 등..



- **데이터베이스 시스템**
  - **통합된 데이터를 관리, 처리 및 사용자에게 서비스**하기 위한 전체 시스템
    - 데이터베이스(DB)
    - 데이터베이스 관리 시스템(DBMS)
    - 데이터 언어(Data Language)
    - 사용자(User)
    - 데이터베이스 관리자(DBA)
    - 데이터베이스 컴퓨터(Database Computer)
    - 시스템



---

#### 4) 데이터베이스 / DBMS 특징

- 데이터 공유

  - 필요한 자료를 한 번만 데이터베이스에 저장

  - 모든 응용프로그램(사용자)가 공유

  - 데이터의 중복 방지, 최신 데이터 유지, **일관성 보장**

  - 이전 File System에서는 여러 응용프로그램에서 데이터를 중복하여 저장 및 관리 

    -> 많은 문제 발생



- **데이터 중복의 최소화**
  - 동일한 데이터가 여러 개 중복되어 저장되는 것 방지



- **데이터의 독립성**
  - 데이터베이스의 크기를 변경하거나 데이터 파일의 저장소 변경 시 기존에 작성된 응용 프로그램에는 영향을 미치지 않도록 데이터의 **독립성 보장**
  - **프로그램과 데이터 분리**



- **데이터의 안정성 향상**
  - 대부분의 DBMS가 제공하는 백업-복원 기능 이용
  - 데이터가 손상되는 문제가 발생할 경우 원상으로 복원, 복구하는 방법이 명확해짐



- **데이터의 무결성(Integrity)**

  - 데이터베이스 안의 데이터는 **오류가 없어야 함**

  - 데이터베이스에 저장된 **데이터 값**과 표현하는 현실 세계의 **실제 값이 일치**해야 함

  - **데이터 상호간의 모순성이 없어야** 하며, 현실세계에 **모순되지 않도록 데이터 유지**

  - 데이터베이스 시스템에서는 이러한 오류를 방지하기 위해 **외래키를 사용하여 데이터(테이블) 간의 모순성 배제**

  - **무결성 제약 조건**

    - 무결성을 보장하기 위해 정확하지 않은 **데이터가 데이터베이스 내에 저장되는 것을 방지**하기 위한 제약 조건

      

- 보안

  - 데이터베이스의 테이블에 따라 접근 권한을 다르게 하여 데이터베이스의 비밀 유지와 조작 방지



- 데이터 추상화
  - 데이터베이스에서는 사용자에게 **저장구조의 복잡성을 숨김**
  - 테이블 개념만으로 DB를 생성 및 관리할 수 있도록 지원



- 다양한 뷰 제공
  - **다양한 형태(뷰)**로 **사용자에게 필요한 DBMS 데이터 세트 제공**
  - 수 천 가지의 뷰 정의 가능
  - 사용자 편의성 제공
  - 보안 및 권한 관리



- 데이터베이스 관리 시스템의 기능

|              기능               |                             내용                             |
| :-----------------------------: | :----------------------------------------------------------: |
|  데이터 정의<br />(Definition)  | 데이터의 **구조**를 정의하고, 데이터 구조에 대한 **삭제 및 변경** 기능 수행 |
| 데이터 조작<br />(Manipulation) | 데이터를 조작하는 소프트웨어(응용 프로그램)가 요청하는 **데이터의 검색, 삽입, 수정, 삭제** 등의 작업 지원 |
|   데이터 제어<br />(Control)    | 데이터베이스 사용자를 생성하고 모니터링하며 접근을 제어<br />**무결성, 보안 및 권한 검사, 백업과 회복, 동시성 제어** 등의 기능 지원 |



---

#### 5) 데이터베이스 언어

- 데이터 언어(Data Language)
  - 데이터베이스를 구축하고 이용하기 위한 **데이터베이스 관리시스템과의 통신 수단**
  - **데이터 정의어** (DDL : Data **Definition** Language)
  - **데이터 조작어** (DML : Data **Manipulation** Language)
  - **데이터 제어어** (DCL : Data **Control** Language)



- **데이터 정의어** (DDL : Data **Definition** Language)

  - **데이터베이스 구조 정의를 위한 언어**

  - 데이터베이스의 구조, 데이터 형식, 접근 방식 등 데이터베이스 구축 및 변경

  - 데이터베이스의 논리적, 물리적 **구조 정의 및 변경**

  - 스키마(Schema)에 사용되는 제약 조건 정의

    - 스키마 : **데이터베이스의 전체 구조 명시**

  - 데이터의 물리적 순서 규정

  - **CREATE / ALTER / DROP**

    

- **데이터 조작어** (DML : Data **Manipulation** Language)

  - **데이터 처리**를 위해 응용프로그램과 데이터베이스 관리 시스템 간의 인터페이스를 위한 언어

  - 데이터 처리 연산 기능

    - 검색, 삽입, 삭제, 갱신, 연산 등

  - **INSERT / DELETE / UPDATE / SELECT**

  - **CRUD**

    - **Create / Read / Update / Delete**

    

- **데이터 제어어** (DCL : Data **Control** Language)

  - **보안 및 권한 제어, 데이터 무결성, 복구, 병행 제어 등**을 위한 언어
  - 데이터 보안 : 권한이 없는 접근으로 부터 보호
  - 데이터 무결성 : 데이터의 정확성, 안전성 보장
  - 데이터 복구(회복) : 시스템 오류 등으로 부터 회복
  - 병행 제어 : 다수 사용자가 공유
  - **GRANT / REVOKE / COMMIT / ROLLBACK**



---

#### 6) 데이터베이스의 발전

- 오프라인 관리
  - 종이에 연필로 기록해 장부로 관리



- 파일 시스템 사용
  - 컴퓨터 파일에 기록 / 저장 → 메모장, 엑셀 활용
  - 컴퓨터에 저장된 파일의 내용은 읽고, 쓰기가 편한 약속된 형태의 구조 사용
  - 데이터 중복으로 인한 불일치 문제



- 데이터베이스 관리시스템(DBMS)

  - 파일시스템의 단점 보완

  - 대량의 데이터를 보다 효율적으로 관리하고 운영

  - 중복제거 등..

    > 참고 : 



---

#### 7) DBMS 종류

- 계층형 DBMS
  - 처음으로 나온 DBMS 개념 - 1690년대 시작
  - 레코드들을 계층 구조로 표현한 데이터 모델 사용
  - **검색이 빠르지만 구조의 변경이 어렵고 데이터 중복 문제 발생**



- 네트워크형 DBMS 
  - 레코드 타입과 링크(Pointer들의 집합)로 구성
  - 복잡한 내부 포인터 사용
  - 프로그래머가 이 모든 구조를 이해해야하만 프로그램의 작성 가능



- **관계형 DBMS**
  - **논리적 구조가 2차원 Table**인 형태
  - 속성값 사용
  - Oracle, DB2, Informix, Sybase, MS SQL Server, MySQL



- NoSQL 데이터베이스(Not Only SQL)
  - SQL을 사용하지 않는다는 의미
  - 필요가 없다는 의미가 아닌 개선 / 보완의 의미
  - 관계형 데이터베이스보다 덜 제한적인 일관성 모델을 이용
  - 키(Key)와 값(Value)의 형태로 저장
  - 키를 사용해 데이터 관리 및 접근
  - MongoDB



---

#### 8) 관계형 데이터베이스

- 관계형 데이터 모델
  - 데이터를 **2차원 테이블 형태인 릴레이션 구조로 표현**하는 **논리적 데이터 모델**



- 릴레이션(Relation)
  - **관계형 데이터 구조**
  - 데이터를 **원자값(Atomic Value)**으로 갖는 2차원 테이블로 표현
  - 논리적 구조이므로 **다양한 정렬 기준을 통하여 릴레이션 표현** 가능



- 릴레이션(테이블) 스키마 - 구조
  - 릴레이션에 데이터를 넣을 수 있도록 하는 릴레이션 틀
  - 릴레이션 이름, 속성 이름, 속성 값의 도메인 정의
    - 릴레이션(Relation) : 테이블(Table)
    - 속성(Attribute): 필드(Field), 열(Row), 칼럼(Columm)
    - 튜플(Tuple) : 행(Record, Row)



- **속성(Attribute)** 

  - 데이터베이스를 구성하는 가장 작은 논리적 단위

  - 개체의 특성, 상태 등 기술

  - 파일 구조의 데이터 필드에 해당

    > 예) 학번, 이름, 학과, 학년 등..



- **도메인(Domain)**

  - 릴레이션에서 하나의 속성이 취할 수 있는 같은 타입의 원자값들의 집합

    > 예) [학년] 속성의 경우 도메인은 1 ~ 4

  - 실제 속성값이 나타날 때 속성값의 적법 여부를 검사하는데 이용

    > 예) [성별] 속성의 경우 도메인은 '남자', '여자'



- 릴레이션의 스키마 표현

  - 릴레이션의 이름(속성1, 속성2, 속성3, ...)

    > 예) 학생(학번, 이름, 학과, 학년, ...)



- 릴레이션 인스턴스
  - 어느 시점의 릴레이션에 들어 있는 튜플(행)들의 집합
  - 동적 성질(삽입, 삭제, 갱신으로 시간에 따라 변함)



- **튜플(Tuple)**
  - 릴레이션의 행(Row) : 데이터 행
  - 릴레이션 내의 모든 튜플은 **서로 중복되어서는 안 됨**



- **릴레이션의 특징**

  - **속성(열)은 단일 값을 가짐**

    - 각 속성의 값은 도메인에 정의된 값만 가짐
    - 각 속성값은 모두 단일 값

  - **속성은 서로 다른 이름을 가짐**

    - 속성은 한 릴레이션에서 서로 다른 이름을 가져야만 함
    - 동일한 이름의 속성명이 존재해서는 안 됨

  - 한 속성의 값은 모두 같은 도메인 값을 가짐

    - 한 속성에 속한 열은 모두 그 속성에서 정의한 도메인 값만 가질 수 있음

  - 속성과 튜플의 순서는 상관없음

    > **속성)**
    >
    > - 속성의 순서가 달라도 릴레이션 스키마는 같음
    >
    > - 열의 순서를 변경하더라도 이 관계의 내용은 전혀 변하지 않음
    >
    >   예) 릴레이션 스키마에서 (이름, 학과) 순으로 속성을 표시하거나 (학과, 이름) 순으로 표시해도 상관없음

    > **튜플)**
    >
    > - 행의 순서가 달라도 같은 릴레이션임
    > - 관계 데이터 모델의 행은 실제적인 값을 가지고 있음
    > - 이 값은 시간이 지남에 따라 데이터의 삭제, 수정, 삽입에 따라 순서가 바뀔 수 있음

  - 릴레이션 내의 **중복된 튜플은 허용하지 않음**
    - 하나의 릴레이션 인스턴스 내에서는 서로 중복된 값을 가질 수 없음
    - **모든 튜플은 서로 값이 달라야 함**
    - 각 튜플을 **서로 다르게 구별** 짓는 속성 - **기본키(Primary Key)**



---

#### 9) 관계 데이터 제약

- **제약(Constraints)**
  - 데이터베이스에 저장되는 **데이터에 대한 규칙**
  - 데이터베이스의 기본 구조 유지
  - 현실세계에서 데이터가 갖는 의미를 보다 정확하게 표현
  - 데이터의 **오류를 방지**하기 위한 중요한 수단



- **관계 데이터 제약**

  - 키
  - 무결성 제약 조건

  

- **키(Key)** 		

  - **릴레이션을 구성하는 각 튜플(행)을 속성(열)값에 의해 유일하게 식별할 수 있게 해주는 속성 또는 속성의 집합**
  - 릴레이션은 중복된 튜플을 허용하지 않기 때문에 각 튜플에 포함된 속성들 중 어느 하나(혹은 그 이상)는 값이 달라야 함

  

- **키의 종류**

  - **기본키**
  - **외래키**
  - 후보키
  - 대체키
  - 복합키



- **기본키(주 키, Primary Key, PK)**

  - **한 테이블에서 모든 행을 유일하게 구별할 수 있는 열(속성)** > 데이터를 구분하는 기본적 기준

  - **NULL 값은 허용하지 않음**

  - **키 값의 변동이 일어나지 않아야 함**

    > 예1) 학생(학번, 성명, 학과, 학년) → 기본키 : 학번
    >
    > 예2) 대한민국 국민(주민번호, 성명, ...) → 기본키 : 주민번호
    >
    > 예3) 상품(상품번호, 상품명, 가격, 제조사, ...) → 기본키 : 상품번호

  

- **외래키(Foreign Key, FK)**

  - **다른 테이블의 기본키를 참조**하는 속성

  - **테이블 간의 관계(Relationship) 표현** 사용

  - 참조하고(외래키) 참조되는(기본키) 양쪽 릴레이션의 도메인은 서로 동일

  - 참조되는(기본키) 값이 변경되면 참조하는 값(외래키)도 변경

  - NULL 값과 중복값 허용

    > 예)
    >
    > - 학과(<u>학과코드</u>, 학과명) : 학과코드(기본키)
    > - 학생(<u>학번</u>, 성명, 학과코드(FK))
    >   - 학번 : 기본키
    >   - 학과코드 : 외래키




- **복합키**
  - 여러 개의 속성을 묶어서 기본키로 사용하는 키



---

### 2. SQL(Structured Query Language)

- localhost(127.0.0.1)
  - 현재 사용 중인 컴퓨터(로컬)를 가리킴



- 포트 : 3306
  - 컴퓨터의 가상의 연결 통로 개념
  - 0 ~ 65535번 까지 사용 가능
  - 일반적으로 0 ~ 1023 까지는 운영체제 등에 의해 할당
  - 이후 응용프로그램 별로 자신의 포트 사용
  - MySQL : 3306
  - Oracle : 1521
  - MS SQL Server : 1433



- 사용자 : root



- 인스턴스
  - MySQL 프로그램이 컴퓨터에서 활성화 되어 있는 서비스
  - MySQL 서버, MySQL 서비스, MySQL 인스턴스 모두 MySQL 자체로 보면 됨



---

#### 1) 데이터베이스 / 테이블 생성

- 데이터베이스(스키마) 생성
  - MySQL에서는 데이터베이스와 스키마가 동일한 의미로 사용
  - root 권한으로 생성
  - Schemas 탭에서 우클릭 / Create Schema...
  - **Name : shopdb** (소문자로 지정 > 대문자로 하면 소문자로 바꾼다는 알림)



- **Charset / Collation : utf8 / Default Collation**
  - Collation : 해당 문자셋을 어떻게 정렬할지 결정하는 방법
  - ORDER BY, LIKE, Primary Key 등 SQL 연산에 영향



- **Apply**



#### 2) 데이터베이스 삭제

- **Drop Schema / Drop Now**



#### 3) 테이블 생성

- shopdb / Tables 우클릭 Create Table
  - 아직 SQL문 안하고 워크벤치에 GUI로 테이블 작성
  - 데이터 입력



#### 4) 데이터베이스 표준 질의어 SQL

1. SQL 개요

2. 데이터 정의어(DDL)

3. 데이터 조작어(DML)

4. 데이터 제어어(DCL)

   

#### 5) SQL 개요

- 데이터베이스 질의어
  - 데이터베이스를 구축하기 위한 도구로서
  - 현대 정보시스템에서 매우 중요한 역할 담당
  - 질의어(Query Language)는 검색 언어라는 의미지만
  - 데이터를 검색하는 역할 외에 데이터의 입력, 수정, 삭제, 제어, 병행 제어, 복구 등
  - 다양한 기능을 제공하는 종합적인 언어



- SQL(Structured Query Language)
  - 관계형 데이터베이스 관리 시스템(DBMS)의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어
  - '에스큐엘' 또는 '시퀄'로 읽음
  - 1970년대 말 밀국 IBM사의 한 연구소에서 데이터베이스 유형에 관계 없이 사용자들이 편리하게 사용하게 사용할 수 있는 질의어를 만들기 위해 개발
  - 초기에는 SEQUEL(Structured English Query Language, 구조 영어 질의어)이라는 이름으로 시작
  - 많은 수의 데이터베이스 관련 프로그램들이 SQL을 표준으로 채택하면서
  - 자신의 제품에 특화 시킨 SQL 사용



#### 6) 데이터 정의어(DDL)

- 데이터베이스 / 테이블이나 관계의 구조를 생성하는데 사용

- CREATE / ALTER / DROP 문

  | SQL문  | 설명                                         |
  | :----: | :------------------------------------------- |
  | CREATE | **데이터베이스** 및 **객체 생성**            |
  | ALTER  | 기존에 존재하는 데이터베이스의 **객체 변경** |
  |  DROP  | 데이터베이스 및 **객체 삭제**                |

- CREATE 문

  - 테이블, 도메인, 뷰, 인덱스, 스키마 구조 정의

  - **CREATE TABLE**

    - 테이블 구성

    - 속성(열)과 속성(열)에 관한 제약 정의

    - 기본키 : PRIMARY KEY

    - 외래키 : FOREIGN KEY

    - 기본 형식 : **CREATE TABLE** 테이블명 (열이름 데이터타입 [,..제약조건]);

      ​					**CREATE TABLE** 테이블명 (열이름 데이터타입 [NUO NULL] [UNIQUE] [DEFAULT...] [PRIMARY KEY 열이름] [FOREIGN KEY 열이름 REFERENCES 테이블(기본키)] [CONSTRAINT 명] ... );

      | 표기 형식                  | 설명                                         |
      | -------------------------- | -------------------------------------------- |
      | NOT NULL                   | 빈 값 허용하지 않음                          |
      | DEFAULT                    | **기본값**으로 설정                          |
      | PRIMARY KEY                | **기본키** 설정                              |
      | FOREIGN KEY                | **외래키** 설정                              |
      | REFERENCES                 | **외래키가 참조할 테이블**(부모 테이블) 설정 |
      | UNIQUE                     | **중복값이 없도록** 설정(대체키 설정 의미)   |
      | CHECK                      | 특정 내용의 **제약 조건 설정**               |
      | ON DELETE / ON UPDATE 옵션 | 참조되는 테이블의 행 **삭제/갱신 시 옵션**   |

      

  - **CREATE SCHEMA**

  - CREATE DOMAIN

  - CREATE INDEX

  - CREATE VIEW

- CREATE TABLE

  - 테이블 생성 후 데이터 입력 시 주의
    - publisher의 pubNo에 먼저 값을 입력해야
    - book의 pubNo 입력할 때 오류 없음

#### 7) 데이터 조작어(DML)

- 테이블의 데이터를 검색, 삽입, 수정, 삭제 하는데 사용
- SELECT / INSERT / DELETE / UPDAET 문
- CRUD

| SQL문  | 설명                                                   |
| :----: | ------------------------------------------------------ |
| INSERT | 데이터베이스 객체에 **데이터 입력**                    |
| DELETE | 데이터베이스 객체에서 **데이터 삭제**                  |
| UPDATE | 기존에 존재하는 데이터베이스 객체 내의 **데이터 수정** |
| SELECT | 데이터베이스 객체로부터 **데이터 검색**                |



#### 8) 데이터 제어어(DCL)

- 데이터의 사용 권한을 관리하는 데 사용
- GRANT / REVOKE / COMMIT / ROLLBACK 문

| SQL문  | 설명                                          |
| :----: | --------------------------------------------- |
| GRANT  | 데이터베이스 객체에 **권한 부여**             |
| REVOKE | 이미 부여된 데이터베이스 객체의 **권한 취소** |



#### 9) 자동 증가

- AUTO_INCREMENT
  - 속성 값을 자동으로 증가

- AUTO_INCREMENT = 100
  - 기본값 100부터 증가



- SET @@AUTO_INCREMENT_INCREMENT = 3
  - 3씩 증가



- 자동 증가 수정
  - SET @COUNT = 0;
  - UPDATE board SET boardNo = @COUNT:=@COUNT + 1;



#### 10) ALTER 문 : 테이블 수정

- 테이블에 대한 **정의 변경**
- 새료운 열 추가, 특정 열의 디폴트 값 변경, 특정 열 삭제 등 수행



#### 11) ALTER 문의 기본 형식

- **ALTER TABLE**
  - **ADD** : 열 추가
  - **RENAME COLUMN** : 열의 이름 변경
  - **MODIFY** : 열의 데이터 형식 변경
  - **CHANGE** : 열의 이름과 데이터 형식 변경
  - **DROP** : 여러 개의 열 삭제
  - **DROP COLUMN** : 열 삭제
  - **DROP PRIMARY KEY** : 기본키 삭제
  - **DROP CONSTRAINT** : 제약조건 삭제



#### 12) Safe Updates 모드 해제

- 메뉴 Edit / Preferences
- SQL Editor
  - Safe Update (rejects ...) 체크 해제
  - OK
  - Workbench 종료했다가 다시 시작



#### 13) 제약조건 삭제

- 기본키 / 외래키 제약조건 삭제
- 기본키 / 외래키 제약조건 추가
- ON DELETE CASCADE
- CHECK 제약조건 추가 / 삭제
- DEFAULT 제약조건 추가 / 삭제



#### 14) 기본키 / 외래키 제약조건 삭제

```sql
-- 기본키 / 외래키 삭제

-- 기본키 삭제
--  1) department 테이블의 기본키 삭제 
-- 	student 테이블에서 외래키 제약조건이 설정되어 있으므로
--  department의 기본키 삭제 시 오류 발생!!
-- 	2) ->> 먼저 외래키 제약조건을 삭제하고 기본키 삭제
-- 	department의 dptNo를 외래키로 사용하고 있는 테이블 : student와 professor

-- 1) department 테이블의 기본키 삭제
alter table department drop primary key;
-- 외래키 제약조건에 위배되어 기본키 삭제 안 됨

-- 2) -> 먼저 외래키 제약조건을 삭제하고
-- student 테이블에서 외래키 제약조건 삭제
alter table student
	drop constraint FK_student_department;
-- 외래키 제약조건이 있을 경우 먼저 외래키 제약조건을 삭제 후 기본키 삭제 가능

-- professor2 테이블에서 외래키 제약조건 삭제
alter table professor2
	drop constraint FK_professor2_department2;
    
-- 3) 이제 department2 테이블의 기본키 삭제됨
alter table department2 drop primary key;
```



#### 15) 기본키 / 외래키 제약조건 추가

```sql
-- department 테이블
alter table department
	add constraint PK_department_depNo primary key(depNo);
    
-- 테이블에 설정된 제약조건 확인
select * from information_schema.table_constraints
where table_schema="sqldb";

select * from information_schema.table_constraints
where table_schema="sqldb" and table_name="department";

-- 외래키 제약조건 추가 : student와 professor 테이블
alter table student
	add constraint FK_student_department
    foreign key (depNo) references department (depNo);
    
-- professor 테이블에 외래키 추가
alter table professor2
	add constraint FK_professor2_department2
    foreign key (depNo) references department2(depNo);
    
select * from information_schema.table_constraints
where table_schema="sqldb" and table_name="professor2";

-- book3 테이블 생성 : 이름 없이 외래키 설정

create table book3_1(
	bookNo 	char(10) not null primary key,
    bookName	varchar(30) not null,
    bookPrice int default 10000 check(bookPrice>1000),
    bookDate date,
    pubNo	char(10) not null,
    foreign key(pubNo) references publisher(pubNo)
    -- 참조하는 외래키 생성(이름 지정 x)
);

-- 제약조건 확인
select * from information_schema.table_constraints
where table_schema="sqldb" and table_name="book3_1";
```





#### 16) ON DELETE CASCADE

- 기준 테이블(기본키를 갖고 있는 테이블)의 데이터가 삭제되었을 때
- 이 값을 사용하고 있는 테이블의 외래키 데이터도 자동으로 삭제되도록 설정

```sql
-- ON DELETE CASCADE
-- ON DELETE CASCADE 제약조건으로 외래키 제약조건을 설정해야 하므로
-- 기존 외래키 제약조건 먼저 삭제 후 다시 설정
alter table student
	add constraint FK_student_department 
    foreign key(depNo) references department(depNo)
    on delete cascade;
```





#### 17) CHECK / DEFAULT 제약조건 추가 / 삭제

- CHECK 제약조건

  - 삭제 시 제약조건 이름 필요

  - 제약조건 확인

    ```sql
    -- 제약조건 확인
    select * from information_schemaa.table_constraints
    where table_schema="sqldb" and table_name="book";
    ```

    

#### 데이터 조작어

 - 데이터 입력 / 수정 / 삭제 / 검색
 - INSERT 문
 - UPDATE 문
 - DELETE 문
 - SELECT 문



---

### INSERT 문

- 테이블에 새로운 행을 삽입하는 명령어



#### INSERT 문 기본 형식

- INSERT INTO 테이블명 (열이름 리스트) VALUES (값리스트);
- INSERT INTO 테이블명 VALUES (값리스트);
  - 모든 열에 값 저장
- 예) student 테이블에 행 삽입
  - INSERT INTO student (stdNo, stdName, stdYear, dptNo) VALUES ('2022001', '홍길동', 4, '1');



#### 스키마 생성 : sqldb2

- publisher / book 테이블 생성



#### 데이터 임포트

- CSV 파일을 읽어서 테이블 생성 및 데이터 입력
- dbworkspace/0603/product.csv
- 파일 import 시 제약조건 없어짐
  - prdNo를 VARCHAR(10) NOT NULL로 변경 후
  - 기본키 제약조건 추가 : PK_product_prdNo



---

### UPDATE 문

- 특정 열의 값을 수정하는 명령어
- 조건에 맞는 행을 찾아서 열의 값 수정



#### UPDATE 문 기본 형식

- **UPDATE** 테이블명 **SET** 열=값 WHERE 조건;
- 예) 상품번호가 5인 행의 상품명을 'UHD TV'로 수정
- **UPDATE** product **SET** **prdName='UHD TV'** **WHERE** prdNo='5';



---

### DELETE 문

- 테이블에 있는 기존 행을 삭제하는 명령어



#### DELETE 문 기본 형식

- **DELETE FROM** 테이블명 **WHERE** 조건;
- 예) 상품명이 '그늘막 텐트'인 행 삭제
  - **DELETE FROM** product WHERE prdName='그늘막 텐트';
- 테이블의 모든 행 삭제
  - **DELETE FROM** product;



---

### SELECT 문

- 테이블에서 조건에 맞는 행 검색



#### SELECT 문 기본 형식

- **SELECT** **열이름 리스트** **FROM** **테이블명** WHERE 검색 조건 / GROUP BY 열이름 / HAVING 검색 조건 / ORDER BY 열이름 ;

| 기능            | 설명                                                         |
| --------------- | ------------------------------------------------------------ |
| SELECT 열이름   | 검색할 **열** 기술                                           |
| FROM 테이블명   | 데이터를 검색할 **테이블명** 기술                            |
| WHERE 조건      | 질의 결과에 포함될 행들이 만족해야 할 **조건** 기술          |
| ORDER BY 열이름 | 특정 **열**의 값을 기준으로 질의 결과 **정렬**<br />**ASC** : 오름차순<br />**DESC** : 내림차순 |
| GROUP BY 열이름 | **그룹** 질의를 기술할 때 사용<br />특정 **열**로 그룹화한 후 각 그룹에 대해 한 행씩 질의 결과 생성 |
| HAVING 조건     | **GROUP BY 절에 의해 구성된 그룹들에 대해** 적용할 **조건** 기술 |





#### 중복 제거

- *: 모든 열 출력
- **DISTINCT**
  - 속성값이 중복되는 것이 있으면 한 번만 출력
  - 예) 주문 테이블에서 '홍길동'이 여러 번 주문한 경우
  - 한 번이라도 주문한 적이 있는 고객명 리스트 출력 시 DISTINCT 사용하면 '홍길동' 한 번만 출력



#### 스키마 생성 : sqldb3

- CSV 파일의 데이터를 읽어서 테이블 생성

  - publisher

  - book

  - client

  - bookSale

- 데이터 타입 변경 : text -> VARCHAR()
  - 모든 NO는 문자 타입
  - 날짜는 DATE 타입
- 기본키 / 외래키 설정



---


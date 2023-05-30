# SQL & DB 공부

## 1. 데이터베이스의 종류

### Key-value Database

- JavaScript의 객체 프로퍼티처럼 Key: Value 형태로 저장하는 형태의 데이터베이스
- 실용성이 없음(때문에 서브용 DB로 많이 사용)

종류: redis

특징:

- 조금 특수한 형태의 Key-value Database
- 많이 씀
- 기본적으로 Hard Disk가 아닌 RAM에 저장하므로 속도가 뛰어나다.

활용:

- main DB 같은 것을 하나 두고 자주 필요한 데이터는 여기에 저장한 뒤 데이터가 필요하면 main DB가 아닌 redis에서 꺼내 쓴다.
- 자주쓰는 데이터 캐싱
- 채팅을 위한 pub/sub
- 영상 스트리밍
- 로그인 기록 저장

redis로 모든 것을 다 할 수 있는 redis 업그레이드 버전이 있으나, 아무도 안 씀

### Relational Database

특징:

- 테이블(행과 열로 이루어진 표)을 하나 만들고 하나의 행(columns)마다 데이터를 저장할 수 있다.
  ex:

```
상품명 | 가격 | 색상
셔츠    6000   Red
바지    7000   Blue
양말    8000   Green
```

- SQL(Structured Query Language)이라는 쿼리 언어 사용
- 그냥 엑셀을 연상하면 됨
- 보통 데이터를 정규화해서 저장
  - 정규화: 데이터가 중복되면 다른 테이블로 다 쪼개버리는 짓거리
- ACID Transaction 기능 지원
- 정확도가 매우 중요한 서비스(결제 등)라면 사용

종류(점유율 순서):

- PostgreSQL
- MySQL
- SQLite
- Microsoft SQL Server
- ORACLE
- MariaDB
- Google Cloud Spanner
- IBM DB2

### Graph Database

특징:

- Graph Query Language 사용
- Relational Database의 '관계'는 데이터 간의 관계가 아니라 행렬에서의 수학적 관계를 말함
- 데이터 간의 관계를 주로 DB에 저장하고 싶으면 Graph Database 사용
- node라는 것을 생성해서, node끼리 어떤 관계에 있는지까지도 기록해 둘 수 있음

종류:

- neo4j(가장 유명함)
- Sparsity
- OrientDB
- ArangoDB

활용:

- 비행기 노선
- SNS 친구관계
- 코로나전염맵
- 추천 서비스

### Document Database

특징:

- Relational Database보다 더 자유로움
- collection을 만들어서 안에 document라는 데이터들을 JSON 형태로 저장
- 정규화 안함
- 구조 바뀌어도 에러 발생 X
- 대부분 분산처리 매우 잘해줌

단점:

- DB간의 정확도가 떨어질 수 있음

종류:

- MongoDB
- CouchDB
- Cloud Firestore

활용:

- SNS
- 실시간 채팅
- 게시판
- 온라인게임

### Column-family Database

특징:

- 테이블을 만들고, row를 만들고 row 안에 자유롭게 기입해서 데이터를 저장
- 행마다 column이 달라도 상관없음
- 데이터 입출력에 자기들이 만든 언어 써야함
- 정규화 없음
- 데이터 입출력 문법이 쉬움
- 데이터 복제 분산 잘함
- 물론 이러면 데이터 일관성이 부족

종류:

- cassandra
- APACHE HBASE
- Google Cloud Bigtable

### Search engine

특징:

- index 보관에 특화
- 기존 DB에서 뽑아서 입력하면 index 생성하고 보관함
- 검색요청이 들어오면 index를 이용해서 자료를 쉽게 검색할 수 있도록 도와줌
- 검색의 오타 요청, 실시간, 추천 검색어 등의 부가 기능 사용

종류:

- elastic
- Amazon CloudSearch
- Google Cloud Search

## 2. MySQL & DBeaver 설치

DBMS(Database Management System) 설치 필요

- 데이터입출력 쉬워짐
- DB접속 계정발급 가능
- 백업 쉬움

### MySQL 설치

Windows 버전

- DBMS마다 저장하는 데이터타입이 다르고 SQL 문법도 살짝 다름

1. 아래 링크에서 MySQL 설치 (가입하라는건 무시)
   https://dev.mysql.com/downloads/installer/

설치된 파일 실행

2. 'Choosing a Setup Type'에서 'Custom' 체크 후 Next> (아니면 불필요한 파일까지 다 다운받게 됨)

3. 설치 설정 과정

- MySQL Servers
  - MySQL Server
    - MySQL Server 8.0(제일 최신버전 선택)
- Applications
  - MySQL Workbench
    - MySQL Workbench 8.0(제일 최신버전 선택)

다 골랐으면 Next> 클릭

4. Type and Networking에서 Next> 클릭

5. 'Accounts and Roles'에서 패스워드 설정 후 Next> (패스워드는 기억해놓기)

6. 이후 계속 Next> 하면서 설치

7. workbench 실행 (안보이면 검색창에서 검색)

8. 'MySQL Connections'에 등록된 서버 클릭해야 MySQL 서버를 띄울 수 있다.

9. 등록된 서버 클릭해서 로그인

10. DBeaver를 사용하면 GUI로 쉽고 편하게 작업할 수 있다.

11. DBeaver 설치: https://dbeaver.io/download/

12. 상단의 '데이터베이스(D)' => '새 데이터베이스 연결' => 비밀번호 입력 후 완료 누른 뒤 설치하라는거 설치

# 데이터베이스

---
## DBMS

- 데이터베이스 내 데이터에 접근하도록 도와주는 시스템

- 크게 질의처리기와 저장시스템으로 이루어짐

---
## 트랜잭션 특징 ACID

- 데이터베이스의 무결성과 일관성을 위해 ACID를 만족해야함

  - 원자성 : 한 트랜잭션 내 실행 작업은 모두 반영하거나 모두 반영하지 않아야 한다.

  - 일관성 : 작업 처리 결과는 항상 일관적이어야 한다.

  - 독립성 : 동시에 실행되는 트랜잭션은 서로에게 영향을 끼치지 않아야 한다.

  - 지속성 : 트랜잭션 완료시 결과가 영구적으로 반영

---
## NOSQL(Not Only SQL)

- SQL을 보완한다는 의미를 가짐

- 스키마가 없어서 데이터를 조회하고 삽입하는 속도가 빠름

- 대량의 분산 데이터를 저장하는데 특화됨

---
## 파티셔닝

- 테이블을 컬럼 단위로 나누는 기법

- update나 insert 같은 작업이 분산되어서 성능이 향상

- 테이블간 join 비용 증가

- index를 별도로 파티셔닝할 수 없음

---
## 샤딩(Horizontal 파티셔닝)

- 테이블을 row 단위로 분산해서 저장하는 방법

- 샤드 키를 정하는 방법에 따라서 샤드 종류가 결정

- 크게 해시 샤딩(해시키 이용)과 동적 샤딩(로케이터 서비스 이용)이 있음

---
## 데이터 베이스 정규화, 비정규화

- 정규화

  - 테이블을 분할하여 중복 데이터를 제거함으로써 데이터 무결성을 유지하는 행위
  
  - 1정규화(1NF) : 도메인이 원자값   
      
    <img src="https://user-images.githubusercontent.com/101415950/195033077-8eaaa90a-ceaa-4f0f-a1ee-f1fa0fa1d39b.png" width="60%" height="60%">

  - 2정규화(2NF) : 부분적 함수 종속 제거   
      
    <img src="https://user-images.githubusercontent.com/101415950/195034681-dda3722c-2923-47e0-8d04-7abdd2ce7c99.png" width="80%" height="80%">

  - 3정규화(3NF) : 이행적 함수 종속 제거   
      
    <img src="https://user-images.githubusercontent.com/101415950/195034701-18d90abe-850f-46d4-b371-403ccf8dd04b.png" width="80%" height="80%">

  - BCNF(보이스코드 정규화) : 결정자이면서 후보키가 아닌 것을 제거   
  
    - 교수는 과목을 결정 짓는 결정자

    - 교수는 학번을 결정 지을 수 없으므로 후보키가 아님, 제거 대상
  
    <img src="https://user-images.githubusercontent.com/101415950/195036347-bf205642-ec79-4cd4-af2c-8971f863b81d.png" width="80%" height="80%">

  - 4정규화(4NF) : 다치(다중) 종속 제거
    
    - 다치종속 : 두개의 독립된 애트리뷰트가 1:N 관계로 대응하는 관계
  
    ![image](https://user-images.githubusercontent.com/101415950/195234161-eab7d116-a95f-4bce-9e65-a921affdb232.png)
  
  - 5정규화(5NF) : 조인 종속 제거
    
    - Join 종속 : 하나의 릴레이션을 무손실, 비부가적 분해하고 나서 다시 합쳤을 때 원래의 릴레이션으로 복원 가능한 관계

    ![image](https://user-images.githubusercontent.com/101415950/195247702-96354a74-6d70-4ec9-87c9-6f61759f6780.png)

- 비정규화

  - 데이터베이스 성능 향상 등을 위해 중복, 통합, 분리 등을 수행하여
    의도적으로 정규형을 위배한 데이터 구조로 만드는 행위
    

---
## DBMS 기능

- 데이터 정의어(DDL, Data Definition Language)

  - 테이블과 컬럼을 정의하는 명령어로 생성, 수정, 삭제 등의 데이터 전체 골격을 결정하는 언어

  - ex. CREATE, ALTER, DROP, RENAME, TRUNCATE

- 데이터 조작어(DML, Data Manipulation Language)

  - 데이터베이스의 내부 데이터를 관리하기 위한 언어로 데이터를 조회, 추가, 변경, 삭제 등의 작업을 수행

  - SELECT, INSERT, UPDATE, DELETE

- 데이터 제어어(DCL, Data Control Language)

  - 데이터베이스에 접근하고 객체들을 사용하도록 권한을 주고 회수하는 명령

  - GRANT, REVOKE

- 트랜잭션 제어어(DDL, Transaction Control Language)

  - 데이터를 제어하는 언어가 아닌 DML에 의해 조작된 결과를 논리적인 작업 단위로 묶어 트랜잭션 별로 제어
  
  - COMMIT, ROLLBACK, SAVEPOINT

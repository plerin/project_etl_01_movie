# project_etl_01_movie


## Keyword

### Github

- Github에 프로젝트 올리기

### Docker

- Docker를 통해 로컬 개발 환경 구성하기

### ETL

- Data_Pipeline 구성하기
- Airflow 활용하기

---

## GOAL

1. Github
    1. Github / Git 에 익숙해지기
    2. 프로젝트를 기록하기
2. Docker
    1. Container 기반 환경 구축에 익숙해지기
    2. 구성하며 기록하여 정리하기(개념/명령어/trouble_shooting)
3. ETL
    1. API를 통해 제공되는 데이터를 수집하여 적재하는 데이터 파이프라인 만들기
    2. Airflow를 통한 구동

---

## TECH_STACK

### Version_Control

- git
    - create repo in github
    - clone repo in local develop
    - build code to github

### ENV

- docker
    - compose image
    - use resource with container
    - connect network with another container

### DB

- postgres(OLTP)
    - store of extract and transform data
    - create summary table

### Workflow

- Airflow
    - create dag for etl
    - setting config(airflow.cfg)

---

## Subject

### 영화 뭐보지? 일단 순위보고 결정해!

<aside>
💡 일별 박스오피스 데이터 수집 ETL 만들기

</aside>

영화 뭐보지 고민중인 당신! 

그렇다면 대세를 따르면 평타는 치잖아요 그러니 일단 데이터를 보고 사람들이 많이 보는 것 중 골라보는건 어떨까요??

### 데이터 정보

- 수집 데이터 : KOBIS 일별 박스오피스
- 생성 주기 : 1일
- 응답 형식 : JSON / XML
- 예시 : [http://kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=f5eef3421c602c6cb7ea224104795888&targetDt=20120101](http://kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=f5eef3421c602c6cb7ea224104795888&targetDt=20120101)

### 환경(by Docker)

- Language : Python
- DB : Postgres
- Scheduler : Airflow

### ETL

- Extract
    - API로부터 데이터 수집
- Transfrom
    - 필요한 필드만 추출
- Load
    - DB(Postgres)에 적재

---

## Process

### Setting_env

**GIT**

- [x]  Make repo in github
- [x]  clone repo in local
    - add .gitignore
    - make the branch _ testor / refactor / main

**DOCKER**

Construct AIRFLOW 

- [x]  find image for airflow
- [x]  acquire properties meaning
- [x]  run image

Construct DB(Postgres)

- [x]  Find image for postgres
    - ID/PW : root / 1234
    - contianerID = pg_container
- [x]  acquire properties meaning
    - comment in docker-compose.yaml
- [x]  run image
- [x]  test connection with airflow
    - register connection in Airflow WEB UI & test done

### ETL

Coding DAG

1. issue the API KEY
    1. official ref : [http://kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.**json**?key=f5eef3421c602c6cb7ea224104795888&targetDt=20120101](http://kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=f5eef3421c602c6cb7ea224104795888&targetDt=20120101)
2. select field for parse
    - rank(int) : 관객수
    - movieCd(varchar(8)) : 영화대표코드
    - salesAmt(bigint) : 해당일 매출액
    - autiCnt(int) : 해당일 관객수
    - scrnCnt(int) : 해당일 스크린수
    - showCnt(int) : 해당일 상영수
    - updated_date(date) : 데이터 수집 일자
3. extract part
4. transform part
5. load part
6. 

---

### TROUBLE_SHOOTING

---

### THOUGHTS

### Github의 작지만 위대한 시작

항상 말로만 Github에 프로젝트를 올려야지 생각했고 회사에서 일을 할 때나 개인적으로 무언가를 만들어볼 때 사용하지 않았다. 프로젝트를 올린다는 것이 부담스러운 일이기도 했고 손이 많이 가는 작업이라 생각했기 때문이다. 그러나 개발이ㄹ

### 컨테이너 기반 개발환경 구축

---

## DURING

postges 컨테이너 접속

```bash
docker exec -it [postgres container id] /bin/bash

# psql 접속 _ 기본 사용자 = root
psql [db_name]
ex) psql postgres // psql dev_db
```

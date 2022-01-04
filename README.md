# project_etl_01_movie



## GOAL

1. container를 활용한 환경 구성
    1. Cloud native env을 사용하기 전(비용 필요) container(docker/k8s)에 익숙해 지기 위함
    2. 과정들을 정리하여 기록하기(개념/명령어/trouble_shooting)
2. 실제 데이터 대상으로 ETL 수행
    1. 예제 샘플이 아니라 실제 API로 제공되는 데이터를 정하고 ETL과정을 통해 수집
    2. 데이터는 일정 기준을 갖고 SUMMARY TABLE 만들기
    
    → 실 데이터를 사용함으로써 ETL 작업의 감을 익히기
    
3. ETL 결과 데이터를 활용한 시각화
    1. 간단한 그래프형태라도 SUMMARY TABLE의 데이터를 시각화 하기

### summary_goal

앞으로 포트폴리오 프로젝트의 시작이 되는 것으로 과정을 기록하고 github에 잘 정리하여 올려보자

-> readme.md 에 해당 프로젝트에 대한 기록 남기기

→ git에 branch를 만들어가며 진행

- testor : 기능 추가시 사용
- refactor : 추가 기능 정리 시 사용
- main : 기능 완성 때마다 사용

순서 : testor → refactor → main

---

## TECH_STACK

### Docker & Docker-compose

### GIT

### AIRFLOW

### SUPERSET

---

## PROCESS

### subject

- 일별 박스오피스 데이터 수집
    - API REF : [https://www.kobis.or.kr/kobisopenapi/homepg/apiservice/searchServiceInfo.do](https://www.kobis.or.kr/kobisopenapi/homepg/apiservice/searchServiceInfo.do)
    - EXAMPLE : [http://kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=f5eef3421c602c6cb7ea224104795888&targetDt=20120101](http://kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=f5eef3421c602c6cb7ea224104795888&targetDt=20120101)
    - ETL :
        1.  매일 영화 데이터(박스 오피스 10위)를 받아 수집 후 특정 필드만 파싱하여 DB에 저장
        2.  SUMMARY TABLE 만들기 
- 시각화
    - SUMMARY TABLE 을 활용한 SUPERSET 시각화
    

### ETL

**일별 박스오피스 수집**

1. KEY 발급
2. API 제공 인터페이스 확인
3. 사용할 필드 선택
4. MOVIE INFO COLLECTING DAG CODING
5. 결과 확인

**CREATE SUMMARY TABLE** 

1. SUMMARY TABLE 대상 필드 및 시나리오 수립
2. SUMMARY TABLE DAG CODING
3. CEHCK RESULT DATA

### anaytsis

**VIEW CHART USING PRESET.IO**

1. CHECK CONNECTION WITH POSTGRES IN DOCKER
2. MAKE CHART
3. COMPOSE DASHBOARD
4. DONE

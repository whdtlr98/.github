
# DE

<details>
  <summary><h2>🔎 Process Preview</h2></summary>
  <img src="https://github.com/user-attachments/assets/acc2c65a-06f3-4ebc-86ff-090874f7dc86"/>
</details>

<details>
  <summary><h2>🏗️ Data Engineering Flow Architecture</h2></summary>
  <img src="https://github.com/user-attachments/assets/055f0fa3-803c-417a-8290-38e11c8258bc"/>
</details>


<details>
  <summary><h2>🛠️ Tech Stack</h2></summary>
  
  ![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
  ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
  ![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-017CEE?style=for-the-badge&logo=Apache%20Airflow&logoColor=white)
  ![Apache Airflow](https://img.shields.io/badge/PySpark-FDEE21?style=for-the-badge&logo=apachespark&logoColor=white)
  
</details>


<details>
  <summary><h2>🆕 데이터 업데이트 자동화</h2></summary>

### <mark>🎯 목적</mark>
**시의성 반영 정보 제공**
> SeoulPOT은 사용자에게 공간에 대한 대시보드를 제공하여 빠르게 공간을 파악할 수 있도록 지원하며, 이를 위해 최신 데이터로 시의성 있는 정보가 필요함
> 
> 주간 단위로 리뷰를 최신화하여, 시의성을 반영한 공간 대시보드를 제공함으로써 사용자가 변화하는 공간 평가를 반영하여 확인할 수 있도록 함
<br/>

### <mark>🗃️ 과정</mark>

1st, 2nd agile에서 수행한 내용들을 기반으로, 업데이트에 필요한 각 과정들을 하나의 태스크로 묶어 순차적으로 실행되도록 함

<br/>

**① 리뷰 수집 / 클리닝 (구별 수행)**

> 1) DB에서 Place 정보 추출
>
> 2) GraphQL을 활용하여 추출한 공간에 업데이트된 리뷰 데이터 수집
> 
> 3) json 형식에서 알맞은 DataFrame 형식으로 클리닝

<br/>

**② 리뷰 감정 분석 (구별 수행)**

> 전이학습된 KoELECTRA 기반 감정 분석 수행

<br/>

**③ 리뷰 광고성 분석 (구별 수행)**

> Transformer 기반 광고성 분석 수행

<br/>

**④ 구별 리뷰 데이터 병합** 

> 구별 기존 데이터와 업데이트된 데이터 병합

<br/>

**⑤ 데이터 집계 (분산처리)**

> 1) 장소별 총 리뷰 수,  긍정 리뷰 수, 부정 리뷰 수, 광고성 리뷰 수 집계

> 2) 장소별 최신순 상위 10개, 긍정순 상위 10개, 부정순 상위 10개 리뷰 데이터 추출

<br/>

**⑥ 리뷰 번역 (구별 수행)**

> GoogleTranslate 기반 번역 수행

<br/>

**⑦ 데이터 업데이트**

> 1) 장소별 집계 결과 업데이트 (DB.place_tb)

> 2) 추출된 리뷰 업데이트 (DB.review_tb)

<br/><br/>

### <mark>📋 결과</mark>

※ 리뷰 약 27000개 기준 (실제 2024.10.28 ~ 2024.11.03 수집 결과)

<br/>

**리뷰 수집 / 클리닝 (**⛔ 약 75% 단축**)**

> 전체 소요 시간 약 8시간
>
> 4개의 Worker를 통해 병렬로 수행한 시간 약 2시간
>
> 약 8시간 → 약 2시간

<br/>

**리뷰 감정 분석 (**⛔ 약 80% 단축**)**

> 전체 소요 시간 약 2시간
>
> 4개의 Worker를 통해 병렬로 수행한 시간 약 25분
> 
> 약 2시간 → 약 25분 

<br/>

**리뷰 광고성 분석 (**⛔ 약 80% 단축**)**

> 전체 소요 시간 약 4시간 30분
> 
> 4개의 Worker를 통해 병렬로 수행한 시간 약 1시간
> 
> 약 4시간 30분 → 약 1시간

<br/>

**데이터 집계 (**⛔ 약 75% 단축**)**

> 전체 소요 시간 약 6분
> 
> Pyspark를 활용한 분산처리 수행한 시간 1분 30초
> 
> 약 6분 → 약 1분 30초

<br/>

**리뷰 번역 (**⛔ 약 70% 단축**)**

> 전체 소요 시간 약 117시간 30분
> 
> 4개의 Worker를 통해 병렬로 수행한 시간 약 35시간
>
> 약 117시간 30분 → 약 35시간

<br/>

**⏱️ 최종 전체 실행 시간 (**⛔ 약 70% 단축**)** 

> 약 132시간 → 약 38시간

</details>

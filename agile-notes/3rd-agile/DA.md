
# DE

<details>
  <summary><h2>🔎 Processes Preview</h2></summary>
  <img src="https://github.com/user-attachments/assets/acc2c65a-06f3-4ebc-86ff-090874f7dc86"/>
</details>

<details>
  <summary><h2>🏗️ Data Engineering Architecture</h2></summary>
  <img src="https://github.com/user-attachments/assets/14ee2191-13b8-45a9-9ada-2ad6edfa8a58"/>
</details>

<details>
  <summary><h2>🆕 최신 리뷰 업데이트</h2></summary>

### <mark>🎯 목적</mark>

**시의성 반영 공간 정보 제공**

> SeoulPOT은 사용자에게 공간에 대한 대시보드를 제공하여 빠르게 공간을 파악할 수 있도록 지원하며, 이를 위해 최신 데이터로 시의성 있는 정보가 필요함
> 
> 주간 단위로 리뷰를 최신화하여, 시의성을 반영한 공간 대시보드를 제공함으로써 사용자가 변화하는 공간 평가를 반영하여 확인할 수 있도록 함

<br/>

### <mark>💾 데이터</mark>
**약 13,000개의 공간 데이터**

**기존 수집한 약 2,000,000개의 공간 리뷰 데이터**

<br/>

### <mark>📃 과정</mark>

**① 리뷰 데이터 준비**

> 20자 이상, SENTIMENT_PARAM(0.5) 이상 데이터 준비 (Unlabeled)

**② 공간별 이상치 리뷰 추출**

> 이전 30일간의 일일 리뷰 수 평균 / 표준편차 계산
> 
> [평균 + OUTLIER_PARAM(2)* 표준편차]
> 
> 위 threshold를 기반으로 이 이상의 일일 리뷰 개수가 나올 경우 이상치 리뷰로 선정

**③ 공간별 이상치 리뷰들간의 유사 리뷰 추출**

> 가게+주소 조합당 tf-idf 벡터의 cosine유사도 계산
> 
> SIMILARITY_PARAM(0.5) 이상의 cosine 유사도를 가진 리뷰들 추출 (Labeling)

<br/>

### <mark>❓ 파라미터 선정 이유</mark>

**SENTIMENT_PARAM(0.5)** : 광고와 걸맞지 않은 가게의 공통된 단점을 걸러냄

**OUTLIER_PARAM(2)** : 기본 이상치 연산시 사용되는 가중치

**SIMILARITY_PARAM(0.5)** : 어순이 바뀌어도 맥락이 비슷한 리뷰를 찾기 위한 값

<br/>

### <mark>⚠️ 문제점</mark>

데이터 약 2,000,000개 중 약 1,400개 추출됨 (0.0007%) → 추가 판단 및 보완 필요

다른 요인으로 인해 리뷰가 많아진 경우도 검토 필요

</details>

<details>
  <summary><h2>📊 장소별 리뷰 수 집계 업데이트</summary>

### <mark>🎯 목적</mark>

**공간 평판 파악**

> 리뷰의 총 개수, 긍정적 및 부정적 피드백 수, 광고성 리뷰 수는 공간에 대한 평판을 직접적으로 반영함
> 
> 시간적 변화를 반영하여 최신 리뷰 데이터를 업데이트함으로써, 더욱 신뢰성 있는 공간 평판을 제공하고자 함

<br/>

### <mark>💾 데이터</mark>
**기존 수집한 약 2,400,000개의 사용자 공간 리뷰 데이터**
**매주 수집되는 약 50,000개의 사용자 공간 리뷰 데이터**

<br/>

### <mark>📃 과정</mark>

**① 평가용 데이터셋 구축**

> 평가용 데이터셋 구축 (Human Eval 데이터 라벨링) 
> 
> 리뷰수 3000개 이상 보유 가게 20개 추출 (각기 다른 태그의 가게)
> 
> 리뷰 길이별 개수 비율에 맞추어 가게당 약 200개 랜덤샘플링 (Unlabeled)
> 
> Human Eval 데이터 라벨링 (긍정/부정)
> 
> 라벨링된 데이터들 중 리뷰 길이별 개수 비율에 맞추어 긍정 100개, 부정 100개 리샘플링

**② 학습 데이터 라벨링**

> Mistral-7B-Instruct-v0.1-GGUF (LLM Eval) 데이터 라벨링 수행
> 
> 리뷰수 3000개 이상 보유 가게 20개 추출 (Unlabeled)
> 
> 리뷰 길이별 개수 비율에 맞추어 여러 가게에 걸쳐 약 4300개 데이터 라벨링

**③ 사전학습모델 전이학습**

> labed dataset을 활용하여 전이학습 수행 (약 3500개)
> 
> KoELECTRA 모델에 대해 수행

**④ Labeling**

> 전이학습된 KoElectra를 활용하여 200,000,000개 데이터(Unlabeled) 라벨링 수행
> 
> POS_PARAM(0.9) 이상 긍정, NEG_PARAM(0.1) 이하 부정으로 판단

<br/>

</details>

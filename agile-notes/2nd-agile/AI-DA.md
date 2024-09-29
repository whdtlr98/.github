# AI-DA
<details>
  <summary><h2>📜 광고성 리뷰 추출 & 제거</h2></summary>

### <mark>🎯 목적</mark>

**신뢰할 수 있는 정보 제공**

> SeoulPOT은 실제 방문자들이 작성한 리뷰를 통해 각 가게에 대한 진정한 평판을 반영하고자 함
> 
> 이를 통해 사용자는 보다 신뢰할 수 있는 정보에 기반하여 공간을 선택할 수 있음


<br/>

### <mark>📃 과정</mark>

**① 리뷰 데이터 준비**

> 20자 이상, SENTIMENT_PARAM(0.5) 이상 데이터 준비 (Unlabeled)

**② 이상치 리뷰들 추출**

> 이전 30일간의 일일 리뷰 수 평균 / 표준편차 계산
> 
> [평균 + OUTLIER_PARAM(2)* 표준편차]
> 
> 위 threshold를 기반으로 이 이상의 일일 리뷰 개수가 나올 경우 이상치 리뷰로 선정

**③ 이상치 리뷰들의 유사 리뷰 추출**

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

데이터 약 200,000,000개 중 약 1,400개 추출됨 (0.0007%) → 추가 판단 및 보완 필요

다른 요인으로 인해 리뷰가 많아진 경우도 검토 필요

</details>
<details>
  <summary><h2>🎭 사용자 리뷰 감정분석</summary>

### <mark>🎯 목적</mark>

**공간 평판 파악**

> 리뷰에 담긴 긍정적 및 부정적 피드백은 사용자 선호도를 직접적으로 반영하므로, 분석을 통해 공간의 평판을 파악할 수 있음

**방문 결정 지원**

> 명확한 긍정/부정 평가 시스템을 통해 공간 선택에 대한 자신감을 얻고, 만족도 높은 방문 경험을 할 수 있도록 도움

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

**④ 모델 평가 및 inference**

> 전이학습된 KoElectra를 활용하여 200,000,000개 데이터(Unlabeled) 라벨링 수행
> 
> POS_PARAM(0.9) 이상 긍정, NEG_PARAM(0.1) 이하 부정으로 판단

<br/>

### <mark>❓ 파라미터 선정 이유</mark>
<details>
    <summary>왜 Mistral-7B-Instruct-v0.1-GGUF으로 모든 데이터를 라벨링하지 않을까?</summary>

    다양한 Sentiment Analysis Pre-trained Model:
    - 평균 AUC: 0.7
    - inference 시간: 1초 이내

    LLM을 활용한 Sentiment Analysis:
    - AUC: 0.99
    - inference 시간: 약 120초 (200,000,000개 데이터 셋에 부적합)

    ➡️ LLM을 통해 학습용 데이터 라벨링을 수행한 후 해당 데이터로 사전학습 모델에 전이학습함으로써 모델의 무게와 소요 시간을 줄이자
</details>

<details>
    <summary>왜 KoELECTRA로 모델을 선택했을까?</summary>

    KoBERT:
    - AUC: 0.49 → 0.95
    - inference 시간: 약 0.5초

    KoELECTRA:
    - AUC: 0.50 → 0.98
    - inference 시간: 약 0.2초

    ➡️ 성능이 좋고 시간이 2배 이상 차이 나는 KoELECTRA를 활용하자
</details>


**POS_PARAM(0.9)** : NEG와 대칭으로 맞춤

**NEG_PARAM(0.1)** : FP의 경우 해당 결과로 인해 해당 장소의 평판을 낮출 수 있음 → 주의하여 확실한 부정 리뷰만을 라벨링

<br/>

### <mark>⚠️ 문제점</mark>

POS_PARAM, NEG_PARAM의 타당성 검토 필요 

</details>

<details>
  <summary><h2>📚 공간 테마 분류</summary>


### <mark>🎯 목적</mark>

테마에 맞는 키워드를 정의하고, 리뷰에 쓰인 키워드 빈도수에 따라 테마를 지정하자

<br/>

### <mark>📃 과정</mark>

**① 리뷰 데이터 준비**

> 20자 이상, SENTIMENT_PARAM(0.5) 이상 데이터 준비

**② 이상치 리뷰들 추출**

> 이전 30일간의 일일 리뷰 수 평균 / 표준편차 계산
> 
> [평균 + OUTLIER_PARAM(2)* 표준편차]
> 
> 위 threshold를 기반으로 이 이상의 일일 리뷰 개수가 나올 경우 이상치 리뷰로 선정

**③ 이상치 리뷰들의 유사 리뷰 추출**

> 가게+주소 조합당 tf-idf 벡터의 cosine유사도 계산
> 
> SIMILARITY_PARAM(0.5) 이상의 cosine 유사도를 가진 리뷰들 추출

<br/>

### <mark>❓ 파라미터 선정 이유</mark>

**SENTIMENT_PARAM(0.5)** : 광고와 걸맞지 않은 가게의 공통된 단점을 걸러냄

**OUTLIER_PARAM(2)** : 기본 이상치 연산시 사용되는 가중치

**SIMILARITY_PARAM(0.5)** : 어순이 바뀌어도 맥락이 비슷한 리뷰를 찾기 위한 값

<br/>

### <mark>⚠️ 문제점</mark>

데이터 약 200,000,000개 중 약 1,400개 추출됨 (0.0007%) → 추가 판단 및 보완 필요

다른 요인으로 인해 리뷰가 많아진 경우도 검토 필요

</details>

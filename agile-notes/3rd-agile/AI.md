# 광고성 리뷰 탐지 및 감정 분석을 통한 리뷰 데이터 정제

## 초록 (Abstract)

온라인 플랫폼에서 사용자 리뷰는 제품 및 서비스의 품질을 판단하는 핵심 지표로 활용된다. 그러나 광고성 리뷰나 스팸 리뷰는 사용자들에게 잘못된 정보를 제공하고 플랫폼의 신뢰도를 저하시킨다. 본 연구에서는 한국어 리뷰 데이터를 대상으로 광고성 리뷰를 효과적으로 탐지하고 감정 분석을 수행하여 리뷰 데이터의 품질을 향상시키는 방법을 제안한다. 이를 위해 Transformer 기반의 분류 모델, KcBERT를 활용한 감정 분석, 코사인 유사도 기반의 그래프 구축 및 약한 감독 학습, 그리고 SDOC 알고리즘을 적용하였다. 제안된 방법은 데이터 불균형 문제를 해결하고 다양한 기법을 통합하여 광고성 리뷰 탐지의 정확도를 향상시켰다.


## 서론 (Introduction)

### 연구 배경 및 필요성

인터넷과 모바일 기술의 발전으로 온라인 리뷰는 소비자들이 제품과 서비스를 선택하는 데 중요한 역할을 한다 [1]. 그러나 광고성 리뷰나 스팸 리뷰는 소비자들에게 왜곡된 정보를 제공하고 기업의 신뢰성을 저하시킬 수 있다[2]. 이러한 문제를 해결하기 위해 광고성 리뷰를 효과적으로 탐지하고 제거하는 기술의 개발이 필요하다.

### 연구 목적

본 연구의 목적은 한국어 리뷰 데이터를 대상으로 광고성 리뷰를 탐지하고 감정 분석을 통해 리뷰 데이터의 신뢰성을 높이는 것이다. 이를 위해 최신 자연어 처리 기법과 머신러닝 알고리즘을 적용하여 광고성 리뷰를 식별하고, 감정 분석을 통해 리뷰의 질을 평가한다.

## 관련 연구 (Related Work)

광고성 리뷰 탐지는 자연어 처리 분야에서 중요한 연구 주제이며, 다양한 접근법이 제안되었다[3][4]. 특히 Transformer 모델은 자연어 처리에서 우수한 성능을 보이며, 광고성 리뷰 탐지에도 활용되고 있다[5]. 또한, 감정 분석을 통해 리뷰의 긍정적 또는 부정적 경향을 파악하여 스팸 여부를 판단하는 연구도 진행되고 있다[6]. 최근에는 한국어에 특화된 사전 학습 언어 모델인 KcBERT를 활용한 감정 분석 연구가 활발히 이루어지고 있다[8].

## 연구 방법 (Methodology)

### 1. 데이터 준비 및 전처리

	•	데이터 로딩: CSV 및 Parquet 형식의 리뷰 데이터를 불러왔다.
	•	결측치 처리: 리뷰 본문(‘body’)의 결측치를 빈 문자열로 대체하였다.
	•	날짜 처리: 리뷰 작성 날짜와 방문 날짜를 표준 형식으로 변환하였다.
	•	리뷰 길이 통계: 리뷰의 평균 길이와 표준편차를 계산하였다.
	•	짧은 리뷰 카운트: 일정 길이 이하의 짧은 리뷰 빈도를 계산하였다.
	•	리뷰 빈도 분석: 시간 간격에 따른 리뷰 작성 빈도를 파악하였다.

리뷰의 길이 및 빈도는 광고성 리뷰를 탐지하는 데 중요한 특징으로 활용된다. 이전 연구에 따르면, 광고성 리뷰는 일반적인 리뷰보다 텍스트 길이가 짧거나 특정 패턴을 보일 가능성이 높다[12][13]. 또한, 특정 시간대에 리뷰가 집중되는 패턴은 스팸 활동의 지표가 될 수 있다[14].

### 2. 광고성 리뷰 탐지

	•	키워드 기반 탐지: 도메인 전문가가 선정한 특정 키워드 목록과 TF-IDF 점수를 활용하여 광고성 리뷰를 식별하였다.
	•	TF-IDF 계산: scikit-learn의 TfidfVectorizer를 사용하여 리뷰 텍스트에서 키워드의 중요도를 산출하였다.
	•	리뷰 전처리: 특수 문자, URL, 해시태그 등의 패턴을 감지하고 제거하였다.

#### 3. 데이터 증강 및 모델 준비

	•	SMOTE 기법 사용: imbalanced-learn의 SMOTE를 활용하여 불균형한 데이터셋에서 소수 클래스를 증강하여 모델의 학습 성능을 향상시켰다[7].

### 4. Transformer 모델 구축 및 학습

	•	TransformerClassifier 구현: PyTorch를 사용하여 다층의 Transformer를 기반으로 하는 분류 모델을 구축하였다. 모델의 구조는 입력층, 선형 변환, 다층의 Transformer 인코더, 출력층으로 구성된다. 입력 데이터는 리뷰 텍스트로부터 추출된 특징 벡터이며, 이를 선형 변환하여 Transformer 인코더의 입력으로 사용한다. Transformer 인코더는 Self-Attention 메커니즘을 활용하여 입력의 패턴을 학습하며, 최종적으로 출력층에서 이진 분류를 수행한다.

[그림 1] TransformerClassifier 모델 구조
![image](https://github.com/user-attachments/assets/36eb7929-734c-42a2-b182-e94ff53dd758)


	•	모델 학습: 이진 크로스엔트로피 손실 함수와 Adam 옵티마이저를 사용하여 모델을 최적화하였다. 학습 과정에서 체크포인트를 저장하여 모델의 재사용성을 높였다.
	•	모델 평가: 테스트 데이터를 통해 모델의 성능을 평가하고 ROC 커브를 시각화하였다.

### 5. KcBERT를 통한 감정 분석

	•	모델 및 토크나이저 로드: beomi/KcBERT-base 모델과 토크나이저를 사용하여 한국어 리뷰의 감정 분석을 수행하였다[8]
 ].
	•	모델 미세 조정: 감정 분석 성능 향상을 위해 사용자 정의 데이터로 모델을 파인튜닝하였다.
	•	감정 점수 계산: 각 리뷰에 대한 긍정/부정 감정 점수를 산출하였다.
	•	속성 기반 감정 분석(ABSA): ‘서비스’, ‘품질’, ‘가격’ 등의 특정 속성에 대한 감정 점수를 계산하였다[9].

### 6. 코사인 유사도 기반 그래프 및 약한 감독 학습

	•	그래프 구축: 리뷰 간 코사인 유사도를 계산하여 NetworkX를 사용해 그래프 형태로 표현하였다.
	•	약한 감독 학습: 라벨이 없는 리뷰에 대해 이웃 리뷰의 라벨을 참고하여 예측하였다[10].
	•	컷 엣지 로직 적용: 유사도가 높은 리뷰들의 라벨을 반영하여 라벨을 수정하였다.

[그림 2] 코사인 유사도 기반 그래프 구조
![image](https://github.com/user-attachments/assets/2d7908f8-69df-4992-b49c-1c4b47f5af7c)


### 7. SDOC 알고리즘 적용

	•	SDOC 알고리즘 사용: 리뷰의 감정 변동성과 폴라리티를 기반으로 광고성 리뷰를 판단하였다[11][15].

### 8. 최종 분류 및 성능 평가

	•	최종 라벨 결정: 다양한 방법의 결과를 종합하여 광고성 리뷰 여부를 최종 판단하였다. 구체적으로 다음과 같은 기준을 적용하였다:


\text{final\_label} =
\begin{cases}
1, & \text{if } (\text{is\_spam\_keyword} = 1) \text{ or } (\text{short\_review\_count} \geq 3) \\
& \text{or } (\text{sdoc\_label} = 1) \text{ or } (\text{final\_classification\_binary} = 1) \\
0, & \text{otherwise}
\end{cases}


	•	성능 평가: 정확도, 정밀도, 재현율, F1 스코어 등의 지표를 사용하여 모델을 평가하였다.
	•	시각화: Confusion Matrix, ROC 커브 등을 통해 결과를 시각적으로 표현하였다.


## 실험 결과 (Experiments and Results)
[그림 3] roc curve

![roc_curve](https://github.com/user-attachments/assets/58b3b3c6-7c53-428f-8be6-67b029f967f2)


### 데이터 불균형 문제 해결

	•	이전 문제점: 전체 2,000,000개의 데이터 중 광고성 리뷰는 약 1,400개로, 비율이 0.0007%에 불과하였다.
	•	개선 사항: SMOTE 기법을 통해 광고성 리뷰 데이터를 증강하여 데이터 불균형 문제를 해결하였다.

### 모델 성능 향상

	•	다양한 모델 적용: Transformer, KcBERT, SDOC 알고리즘 등 여러 모델을 사용하여 광고성 리뷰 탐지의 정확도를 높였다.
	•	성능 지표 개선: 정밀도와 재현율이 이전보다 향상되었으며, F1 스코어도 증가하였다.
	•	체크포인트 저장: 학습 과정에서 모델의 체크포인트를 저장하여 학습 중단 시에도 재학습이 가능하도록 구현하였다.

### 약한 감독 학습의 효과

	•	라벨 부족 문제 완화: 약한 감독 학습을 통해 라벨이 없는 데이터에 대한 예측 정확도를 높였다.
	•	그래프 기반 관계 활용: 리뷰 간의 유사도를 활용하여 라벨 예측의 신뢰성을 향상시켰다.

## 논의 (Discussion)

### 문제점 및 한계

	•	리뷰 수 급증 요인 미검토: 특정 요인으로 인해 리뷰 수가 급증한 경우에 대한 고려가 부족하였다.
	•	실시간 처리 한계: 대용량 데이터를 처리하는 데 시간이 소요되어 실시간 처리에 제약이 있다.

### 향후 연구 방향

	•	모델의 지속적인 개선: 추가 데이터 수집 및 모델 튜닝을 통해 성능을 향상시킬 수 있다.
	•	실시간 모니터링 시스템 구축: 광고성 리뷰를 실시간으로 탐지하고 대응할 수 있는 시스템을 개발이 가능하다.
	•	사용자 피드백 반영: 실제 사용자들의 피드백을 수집하여 모델의 적용성을 높일 수 있다.

## 결론 (Conclusion)

본 연구에서는 한국어 리뷰 데이터를 대상으로 광고성 리뷰 탐지 및 감정 분석을 수행하여 리뷰 데이터의 품질을 향상시키는 방법을 제안하였다. 데이터 불균형 문제를 해결하고, Transformer 모델과 KcBERT, SDOC 알고리즘 등을 통합하여 모델의 성능을 향상시켰다. 실험 결과, 제안된 방법은 광고성 리뷰를 효과적으로 탐지하였으며, 감정 분석을 통해 리뷰의 질을 평가할 수 있었다. 이를 통해 사용자들에게 보다 신뢰성 있는 리뷰 정보를 제공할 수 있을 것으로 기대된다.

## 참고 문헌 (References)

<ol>
  <li>Hu, N., Pavlou, P. A., & Zhang, J. (2006). Can online reviews reveal a product’s true quality? <i>Proceedings of the 7th ACM conference on Electronic commerce</i>.</li>
  <li>Yoo, K. H., & Gretzel, U. (2009). Comparison of deceptive and truthful travel reviews. <i>Information and communication technologies in tourism 2009</i>.</li>
  <li>Jindal, N., & Liu, B. (2008). Opinion spam and analysis. <i>Proceedings of the 2008 international conference on web search and data mining</i>.</li>
  <li>Mukherjee, A., Venkataraman, V., Liu, B., & Glance, N. (2013). Fake review detection: Classification and analysis of real and pseudo reviews. <i>UAI</i>.</li>
  <li>Vaswani, A., et al. (2017). Attention is all you need. <i>Advances in neural information processing systems</i>.</li>
  <li>Pang, B., & Lee, L. (2008). Opinion mining and sentiment analysis. <i>Foundations and Trends® in Information Retrieval</i>.</li>
  <li>Chawla, N. V., et al. (2002). SMOTE: synthetic minority over-sampling technique. <i>Journal of Artificial Intelligence Research</i>.</li>
  <li>Lee, J., et al. (2020). KR-BERT: A small-scale Korean-specific language model. <i>arXiv preprint arXiv:2008.03979</i>.</li>
  <li>Pontiki, M., et al. (2016). SemEval-2016 task 5: Aspect based sentiment analysis. <i>Proceedings of the 10th international workshop on semantic evaluation (SemEval-2016)</i>.</li>
  <li>Zhu, X., & Goldberg, A. B. (2009). Introduction to semi-supervised learning. <i>Synthesis lectures on artificial intelligence and machine learning</i>.</li>
  <li>Li, F., et al. (2011). Spam detection by content and structure analysis. <i>ICDE</i>.</li>
  <li>Ott, M., Choi, Y., Cardie, C., & Hancock, J. T. (2011). Finding deceptive opinion spam by any stretch of the imagination. <i>Proceedings of the 49th Annual Meeting of the Association for Computational Linguistics: Human Language Technologies</i>.</li>
  <li>Li, J., & Hovy, E. (2014). Sentiment analysis on the people’s daily. <i>Proceedings of the 52nd Annual Meeting of the Association for Computational Linguistics</i>.</li>
  <li>Fei, G., Mukherjee, A., Liu, B., Hsu, M., Castellanos, M., & Ghosh, R. (2013). Exploiting burstiness in reviews for review spammer detection. <i>Proceedings of ICWSM</i>.</li>
  <li>Li, J., Yang, L., & Zhang, P. (2023). Shooting review spam with a weakly supervised approach and a sentiment-distribution-oriented method. <i>Applied Intelligence, 53</i>(9), 10789-10799.</li>
</ol>

## 실험 환경 (Experimental Setup)

- **하드웨어**: NVIDIA GPU를 사용하여 모델 학습 및 추론을 수행하였다.
- **소프트웨어**: Python 3.8, PyTorch, Transformers 라이브러리 등을 사용하였다.

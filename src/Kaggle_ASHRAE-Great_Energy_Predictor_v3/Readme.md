# ASHRAE - Great Energy Predictor III
---
### 주소: https://www.kaggle.com/c/ashrae-energy-prediction 

### 일정: 2019년 12월 20일 마감

### 평가방식: RMSE

### 결과 : 동메달 획득, Top 10%(333 / 3614)

### 근황일지(12월 18일 최종 수정)
 - [Leak Validation - Constrained Heuristic Search](https://www.kaggle.com/kulkarnivishwanath/ashrae-great-energy-predictor-iii-eda-model/comments)
	- Leak Validation  커널**(0.97)** 제출 완료

 - [ASHRAE- KFold LightGBM - without leak (1.08)](https://www.kaggle.com/aitude/ashrae-kfold-lightgbm-without-leak-1-08)
	-  LGBM 모델을 통한 데이터 학습 후 예측부분에서 메모리 부족으로 인해 커널이 끊기는 것으로 보임
	- fold의 개수를 **증가**시킬 경우 예측부분에서 상당한 메모리가 사용됨(캐글에서 지원하는 메모리는 16GB, 메모리가 터짐...)

 - Leak Validation + 3-Fold 2560 leaves + Highway route4 + 
		- Public score 0.95 달성(TOP 3%)

 - LGBM 파라미터 및 fold 값 조정결과: 
	1. **num_leaves**의 수 증가: **1.09**로 하락
	2. **fold**의 수를 증가: **1.09**로 하락
	3. **fold** + **num_leaves**의 수 증가: **1.09**로 하락	
	4. **outlier** 데이터 포함 후 모델 트레이닝: **1.12**로 하락

 - 추후 계획:
	1. 모델 트레이닝에 들어가는 feature 특성 조정 후 모델링 예정(+ Leak data) 
		- outlier 데이터 항목을 제외하고 트레이닝, 1.08
			- outlier 데이터에 대해서만 따로 트레이닝 하고 합칠 수 있는 방법?

### 스터디 내용
---
#### 1. 11월 11일 ~ 15일
 - 목표:
	- 데이터 예측을 위해 캐글 컴피티션에 게시된 커널 따라 해보기
	- 커널에 작성되어있는 코드를 따라 작성 후 제출하여 score 얻기

 - 분석한 커널:
	- [eda-for-ashrae](https://github.com/madfalc0n/kaggle_project/blob/master/great_energy_predict/notebook/20191114/EDA_or_Model%20apply.ipynb)
	- [simple-linear-regression-benchmark](https://github.com/madfalc0n/kaggle_project/blob/master/great_energy_predict/notebook/20191112/Simple%20Linear%20Regression%20Benchmark.ipynb)

 - 달성한 내용:
	- 커널에 작성되어 있는 코드를 따라 적어보며 전반적인 데이터 분석을 위한 EDA 과정과 모델(simple linear regression) 사용하는 방법에 대한 습득
	- Public score 1.88 달성

#### 2. 11월 18일 ~ 29일
 - 목표:
	- 데이터 예측을 위해 캐글 컴피티션에 게시된 커널 따라 해보기
	- 커널에 작성되어있는 코드를 따라 작성 후 제출하여 score 얻기

 - 분석한 커널:
	- [ashrae-great-energy-predictor-iii-eda-model](https://github.com/madfalc0n/kaggle_project/blob/master/great_energy_predict/notebook/20191120/ASHRAE%20-%20Great%20Energy%20Predictor%20III-%20EDA%26Model_2.ipynb)
	- [ASHRAE_energy predict_Half and Half_score 1.11](https://github.com/madfalc0n/kaggle_project/blob/master/great_energy_predict/notebook/20191209/ASHRAE_energy%20predict_Half%20and%20Half_score%201.11.ipynb)

 - 달성한 내용:
	- 커널에 작성되어 있는 코드를 따라 적어보며 전반적인 데이터 분석을 위한 EDA 과정과 모델(LightGBM) 사용하는 방법에 대한 습득
	- Public score 1.11 달성

#### 3. 12월 02일 ~ 13일
 - 목표:
	- Leak Validation 커널 분석
	- LGBM 모델 파라미터 튜닝을 통해 스코어(0.97 이하) 낮추기

 - 분석한 커널:
	- [ashrae-leak-validation-heuristic-search-madfalcon](https://github.com/madfalc0n/kaggle_project/blob/master/great_energy_predict/notebook/20191213/ashrae-leak-validation-heuristic-search-madfalcon.ipynb)
	- [ashrae-kfold-lightgbm-1-09-madfalcon](https://github.com/madfalc0n/kaggle_project/blob/master/great_energy_predict/notebook/20191213/ashrae-kfold-lightgbm-1-09-madfalcon.ipynb)

 - 달성한 내용:
	- KFold 제출 후 public score 1.09 달성
	- Leak Validation 제출 후 public score 0.97 달성

 - 직면한 문제:
	- KFold + LGBM 모델을 통한 데이터 train 후 predict 부분에서 메모리 부족으로 인해 커널이 끊기는 것으로 보임, fold의 수와 예측정확도를 올리기위한 모델(LGBM) 파라미터 조정 시, 예측부분에서 메모리 사용량이 많이 증가됨에 따라 커널이 끊기는 것으로 보임
		- fold의 개수를 증가시킬 경우 예측부분에서 상당한 메모리가 사용됨(캐글에서 지원하는 메모리는 16GB, 메모리가 터짐...)
		- 또한 fold의 개수를 늘린다고 하더라도 항상 성능이 좋아지지는 않음(기존 커널 1.08에서 1.09로 올라버림...)



#### 4. 12월 13일 ~ 19일

- 분석한 커널:
   
- [Leak Validation - Constrained Heuristic Search](https://www.kaggle.com/kulkarnivishwanath/ashrae-great-energy-predictor-iii-eda-model/comments)
   
 - 달성한 내용

    - Leak 된 Data 와 LGBM 을 통해 얻어낸 예측값(Leak Validation + 3-Fold 2560 leaves + Highway route4)을 통해 결과 제출
   - Public score **0.951** 달성(TOP 10%, Bronze medal)

- 개인소감

  참가자들의 공개된 커널을 통해 데이터의 전반적인 흐름을 분석하고 Leak 된 Data를 통해(약간의 하이퍼파라미터조절) 운이좋게도 동메달을 딴것 같다. 다음 대회에서는 참가자들의 비중이아닌 내가 직접 코드를 작성해보고 나의 비중을 늘려가봐야 겠다.
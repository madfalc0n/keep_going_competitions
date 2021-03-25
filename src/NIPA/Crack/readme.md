# 태영세라믹 - 타일 이미지 내 미세 Crack 검출

참고 : 해당 폴더에는 데이터가 존재하지 않음

0. 모델 대략 설명

## 1. 데이터 전처리

1. (64,64,3) 이미지를 (156,156,3) 사이즈로 resize 후 normalize 진행



## 2. 모델링 및 예측

1. Efficientnet(B5~7), Resnet50 등의 CNN 모델을 사용하여 학습진행
2. 학습된 모델들을 통해 ensemble 진행 후 예측
3. F-1 score 기준 94% 정확률 달성



## 3. Etc

- 모델 학습
  - Step2_model_train.ipynb 파일을 이용하여 학습 진행

- 데이터 예측
  - Step3_model_predict.ipynb 파일을 이용하여 예측 진행
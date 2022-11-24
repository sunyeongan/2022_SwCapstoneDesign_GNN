# 태풍 경로 예측 딥러닝 모델 개발 
 태풍 정보 데이터를 학습 후 일정 시간 이후의 태풍을 예측하는 Seq2Seq with Attention 모델 개발

## 프로젝트 선정이유 
2022년에 발생한 초강력 태풍 "힌남노"로 인한 인명, 재산 피해가 발생했다. 지구 온난화의 영향으로 기상이변의 피해를 최소화 하기 위해
기상이변의 출현과 진행을 빠르게 예측하고 대비해야한다. 우리나라 기상청이 태풍이나 날씨를 예측할 때 사용하는 "수치예보모델"은 하루에 
1번 구동시에 많은 컴퓨팅 비용이 발생해서 2번 정도 구동이 된다. 이는 시시각각 변하는 태풍에 빠르게 대응하기 어렵다는 단점이있다.
우리팀은 적은 컴퓨팅 파워를 요구하는 태풍 경로 예측 딥러닝 모델을 개발해서 자주 예측을 수행하는 모델을 만들었다.


## Notion
[프로젝트 진행상황](https://atom-swordtail-48b.notion.site/AAMMCC-edf4dd5d83cf416d9ff3a9bcac2f0589)

## 팀원 

|이름|학과|개발|
|---|------|---|
|[박상현](https://github.com/CAKE31115)|빅데이터전공|AI|
|[전진완](https://github.com/JeonJinw)|빅데이터전공|AI|
|[안선영](https://github.com/sunyeongan)|빅데이터전공|AI|

## Deep Learning
### DataSet 수집 및 전처리
기상청자료개방포털에서 2001년부터 2022년 10월까지 한반도에 영향을 준 태풍 정보 csv파일을 526개 수집. 
윈도우 슬라이딩 방식을 이용해 데이터셋 정의.

![image](https://user-images.githubusercontent.com/44018024/203675869-df7a5ac6-5409-4e4a-942b-b521b61bc5a1.png)
![image](https://user-images.githubusercontent.com/44018024/203675916-a6fd912f-fe4b-4fb1-99ea-2c92e36197aa.png)

### 모델 구조 
![image](https://user-images.githubusercontent.com/44018024/203678209-188949ed-37ce-468d-a7d0-05d714a715d3.png)

### 학습
Batch size : 256

input window size : 3

output winodw size : 1

Hidden size : 4, 5, 6

Optimizer : Adam (learning rate : 0.0008)

Scheduler : CosineAnnealingLR

Loss : L1Loss

-> 4, 5, 6 의 히든 스테이트로 학습 시킨 Seq2Seq with Attetion모델 총 5개를 앙상블한 모델 이용 

### 결과
- 태풍 힌남노 

![힌남노](https://user-images.githubusercontent.com/44018024/203676148-9ffd3238-150e-4269-9c8a-e1b2793b92b1.gif)

- 태풍 난마돌
![난마돌](https://user-images.githubusercontent.com/44018024/203676425-0bb61b6b-cd18-4d31-9842-c61b47b2c758.gif)
- 태풍 매미
![매미2](https://user-images.githubusercontent.com/44018024/203676403-208b88d3-f622-4cea-ac58-20d950a998fc.gif)


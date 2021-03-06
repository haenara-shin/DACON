# 주제
- 제시된 지역의 기상 데이터와 과거 발전량 데이터를 활용하여, 시간대별 태양광 발전량을 예측
# 기대효과 
- 시간대별 소비자 그룹의 전력소비량 예측 데이터와 결합하여 가장 효율적인 시간대별 태양광 발전과 국가 전력망을 조합 가능.
- 각 소비자 그룹에 최적화된 공급계획 수립 가능.  
# 배경
- 신재생 에너지 태양광 발전량 예측을 위한 시계열 데이터 분석기법 발굴  
- 신재생 에너지 관리 솔루션 개발 활용 및 에너지 서비스 산업 발전 촉진   

# 대회 설명
- 취지: 태양광 발전은 매일의 기상 상황과 계절에 따른 일사량의 영향을 받음. 이에 대한 예측이 가능하다면 보다 원활하게 전력 수급 계획을 세울 수 있음.
- 목표: 신재생에너지의 생산 효율성을 극대화하고, 사용자들에게 저렴한 전력을 공급할 수 있도록 인공지능 기반 태양광 발전량 예측 모델을 만듦.  
- 모델은 7일(Day 0~ Day6) 동안의 데이터를 input으로 활용하여, 향후 2일(Day7 ~ Day8) 동안의 30분 간격의 발전량(TARGET)을 prediction 해야함. (1일당 48개씩 총 96개 타임스텝에 대한 예측)
# 주최 / 주관
- 주최: 연구개발특구진흥재단 / 한국원자력연구원(KAERI)
- 주관: [데이콘](https://dacon.io/competitions/official/235680/overview/description)
- 후원: (주)에넨에스

# data
- `train.csv` : 훈련용 데이터 (1개 파일)
  - 3년(Day 0~ Day1094) 동안의 기상 데이터, 발전량(TARGET) 데이터  
- `test.csv` : 정답용 데이터 (81개 파일)
  - 2년 동안의 기상 데이터, 발전량(TARGET) 데이터 제공 
- 각 파일(*.csv)은 7일(Day 0~ Day6) 동안의 기상 데이터, 발전량(TARGET) 데이터로 구성
- 파일명 예시: 0.csv, 1.csv, 2.csv, …, 79.csv, 80.csv (순서는 랜덤이므로, 시계열 순서와 무관)
- 각 파일의 7일(Day 0~ Day6) 동안의 데이터 전체 혹은 일부를 인풋으로 사용하여, 향후 2일(Day7 ~ Day8) 동안의 30분 간격의 발전량(TARGET)을 예측 (1일당 48개씩 총 96개 타임스텝에 대한 예측)

- `sample_submission.csv` : 정답제출 파일
  - test 폴더의 각 파일에 대하여, 시간대별 발전량을 9개의 Quantile(0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9)에 맞춰 예측
  - “파일명_날짜_시간” 형식(예시: 0.csv_Day7_0h00m ⇒ 0.csv 파일의 7일차 0시00분 예측 값)에 유의
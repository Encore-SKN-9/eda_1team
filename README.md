## 목차

1. 데이터셋 소개

2. 데이터 클리닝

3. 데이터 시각화

4. 관계분석

5. 결론

6. 향후 분석 방향


---

# 1. 데이터셋 소개

## **데이터 명:**
**Effects of Alcohol on Student Performance**
(알코올이 학생 성과에 미치는 영향)

## **데이터 출처:**
[https://www.kaggle.com/datasets/joshuanaude/effects-of-alcohol-on-student-performance]

## **데이터 개요:**
이 데이터는 학생들의 음주 습관과 학업 성취 간의 상관관계를 탐구하고, 음주가 학습 성과에 미치는 잠재적 영향을 파악할 목적으로 수집된 데이터이다.  
2024년에 진행된 설문조사의 응답들로 구성되어 있으며, 2023년의 학생 정보를 담고 있다.

## **데이터 속성:**
| **Column**                                         | **번역 (한글)**                         | **의미**                                | **데이터 타입** | **응답**                                                                                                                                                                   | **비고**                                    |
|---------------------------------------------------|-----------------------------------------|-----------------------------------------|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------|
| Timestamp                                         | 타임스탬프                              | 설문 제출 시간                          | object          |                                                                                                                                                                          |                                            |
| Your Sex?                                         | 당신의 성별은?                          | 성별                                    | object          | 'Female', 'Male'                                                                                                                                                         |                                            |
| Your Matric (grade 12) Average/ GPA (in %)       | 고등학교(12학년) 평균/학점(%)           | 고등학교 성적                          | float64         | (0~100)                                                                                                                                                                 |                                            |
| What year were you in last year (2023) ?         | 작년(2023년)에는 몇 학년에 재학 중이었나요? | 2023년 재학 학년                        | object          | '1st Year', '2nd Year', '3rd Year', '4th Year', 'Postgraduate'                                                                                                          |                                            |
| What faculty does your degree fall under?        | 전공 학부는 무엇인가요?                 | 전공 학부                               | object          | 'Arts & Social Sciences', 'Economic & Management Sciences', 'AgriSciences', 'Engineering', 'Science', 'Medicine and Health Services', 'Law', 'Education'              |                                            |
| Your 2023 academic year average/GPA in %         | 2023년 학업 평균/GPA                    | 2023년 성적                             | float64         | (0~100)                                                                                                                                                                 | (2024년 신입생은 해당 없음)               |
| Your Accommodation Status Last Year (2023)       | 작년(2023년)의 거주 상태는?             | 거주지                                  | object          | 'Private accommodation/ stay with family/friends', 'Non-private accommodation i.e., Res'                                                                               |                                            |
| Monthly Allowance in 2023                        | 2023년 월간 용돈은?                     | 월간 용돈 수준                          | object          | 'R 4001- R 5000', 'R 7001 - R 8000', 'R 6001 - R 7000', 'R 5001 - R 6000', 'R 8000+'                                                                                     | 단위: 남아프리카공화국 (랜드) <br> 1 랜드: 77.79 원 |
| Were you on scholarship/bursary in 2023?         | 2023년에 장학금을 받았나요?             | 장학금 수령 여부                        | object          | 'No', 'Yes (NSFAS, etc...)'                                                                                                                                            |                                            |
| Additional amount of studying (in hrs) per week  | 주당 추가 공부 시간(시간 기준)          | 주당 공부 시간                          | object          | '0', '1-3', '3-5', '5-8', '8+'                                                                                                                                          |                                            |
| How often do you go out partying/socialising...  | 주중에 파티나 사교 활동을 얼마나 자주 하나요? | 파티, 사교모임 빈도                     | object          | 'Only weekends', '0', '1', '2', '3', '4+'                                                                                                                              |                                            |
| On a night out, how many alcoholic drinks...     | 외출 시 술을 몇 잔이나 마시나요?        | 외출 시 음주량                          | object          | '0', '1-3', '3-5', '5-8', '8+'                                                                                                                                          |                                            |
| How many classes do you miss per week due to...  | 술로 인해 주당 몇 수업을 결석하나요?     | 주당 음주로 인한 결석 수                 | object          | '0', '1', '2', '3', '4+'                                                                                                                                                |                                            |
| How many modules have you failed thus far...     | 지금까지 몇 개의 과목에서 낙제했나요?   | 낙제 과목 수                            | object          | '0', '1', '2', '3', '4+'                                                                                                                                                |                                            |
| Are you currently in a romantic relationship?    | 현재 연애 중인가요?                     | 연애여부                                | object          | 'Yes', 'No'                                                                                                                                                             |                                            |
| Do your parents approve alcohol consumption?     | 부모님은 음주를 허용하시나요?           | 부모 음주 허용 여부                     | object          | 'Yes', 'No'                                                                                                                                                             |                                            |
| How strong is your relationship with your...     | 부모님과의 관계는 얼마나 가까운가요?    | 부모 친밀도                             | object          | 'Very close', 'Fair', 'Close', 'Distant'                                                                                                                                |                                            |




### 데이터 구조:
**총 데이터 수:**  407개  
**총 컬럼 수:** 17개

**범주형 데이터 (object) :** 15개  
**숫자형 데이터(float64) :** 2개 


### 데이터 기초통계:



---

# 2. 데이터 클리닝

수치형 데이터

히스토그램을 확인해본 결과 극단값이 존재함. 이는 잘못된 값은 아니지만 분석에서 이 값으로 인해 극단값에 영향을 받아 평균값이 달라지므로 제거함



범주형 데이터

데이터의 분포를 확인
학과의 경우 성적과 음주의 영향이 없을 것이라고 판단했고, 학과의 편향이 심하다고 생각하여 '학과'열 삭제



결측치 처리

전부 NaN인 값을 확인하고 삭제



수치형 데이터의 경우 평균값으로 대체함

범주형 데이터는 가장 많은 최빈값으로 대체

NaN이 많은 속성들의 공통점은 과거 음주로 인한 영향을 알 수 없으므로 데이터를 모두 삭제함
현재 최근성적을 알수 있는 데이터만 남김





---

# 3. 분석

## 3-1) 음주 습관

시각화 이미지(주요설명)


## 3-2) 음주와 학업의 관계

시각화 이미지(주요설명)


## 3-3) 음주에 영향을 미치는 요인

시각화 이미지(주요설명)


---


# 4. 결론


## 주요 내용:


~~ 증가할수록 ~~ 도 증가
~~ 이 감소하면 ~~~ 이 증가
~~ 이 성적에 중요 요인이 됨


## 한계점:


---

# 6. 향후 분석 방향


추가 변수 고려: 스트레스, 수면 시간, 운동 습관 등 학업 성적에 영향을 미칠 수 있는 요인을 분석에 포함.
세분화된 분석: 전공 또는 학년에 따른 음주 습관과 학업 성적의 차이를 탐구.

음주량이 증가할수록 학업 성적이 하락하는 경향이 있다는 점은 학생들의 음주 습관 관리가 성적 향상에 중요한 요소.
음주로 인해 학습 시간이 줄어들거나 학업에 지장이 생기는 경우가 있음.
학생들이 학업 스트레스를 다른 방식으로 해소하도록 지원(운동, 상담 등).

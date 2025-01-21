## 목차

0. 팀 소개

1. 데이터셋 소개

2. 데이터 클리닝

3. 데이터 특징

4. 결론



---


# 0.팀 소개

### 팀명 : 밸런스(Balance)

학업과 음주의 균형을 맞추자는 의미를 가짐




<table align=center>
<tbody>
<tr>
<td align=center><b>김도연</b></td>
<td align=center><b>박주은</b></td>
<td align=center><b>서예찬</b></td>

</tr>

<tr>
<td><a href="https://github.com/youngseo98"><div align=center>@doyeon158</div></a></td>
<td><a href="https://github.com/yujitaeng"><div align=center>@pprain1999</div></a></td>

<td><a href="https://github.com/Hack012"><div align=center>@syc9811</div></a></td>

</tr>
</tbody>
</table>

<br><br><br>

# 1. 데이터셋 소개

## **데이터 명:**
**Effects of Alcohol on Student Performance**
(알코올이 학생 성과에 미치는 영향)

## **데이터 출처:**
[https://www.kaggle.com/datasets/joshuanaude/effects-of-alcohol-on-student-performance]

## **데이터 선정이유:**
건강한 음주생활과 학습에 관련된 영향을 파악하기 위해서 선정했다.

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
![220320](https://github.com/user-attachments/assets/47b9a163-e8b7-42d7-b264-c5516091919f)


**총 데이터 수:**  407개  
**총 컬럼 수:** 17개

**범주형 데이터 (object) :** 15개  
**숫자형 데이터(float64) :** 2개 


### 데이터 기초통계:
![df describe](https://github.com/user-attachments/assets/547bd57a-f98f-4fc1-b49b-2bcaefbf5c18)

![df describe(2)](https://github.com/user-attachments/assets/74262deb-109f-4b6c-b8ec-5edb0b95ced5)


---

# 2. 데이터 클리닝

## 2-1) 데이터 컬럼 확인

- 시간, 학과 열 삭제

 - 시간 : 응답제출 시간은 주제에 관련 없으므로 삭제
 - 학과 : '경제학과'에 대부분을 차지하고 있어 편향적이며, 음주와 관련성이 없다고 보고 삭제
![220516](https://github.com/user-attachments/assets/be9394b5-ea21-4640-a3be-e805f7d429b8)



## 2-2) 결측치 처리

- 전체 결측치 확인


![220528](https://github.com/user-attachments/assets/69363f5a-f643-4a24-b491-c7fda3848368)



- 전체 결측치인 값 (224,232)을 제거


![220538](https://github.com/user-attachments/assets/f0e19112-8c1b-4630-9263-3966f32f2d05)



- 학년, 최근성적이 없는 값을 제외


![225655](https://github.com/user-attachments/assets/adc27dbf-a0aa-4b57-adb7-626ffd583310)

NaN이 많은 속성들의 공통점은 과거 음주로 인한 영향을 알 수 없으므로 데이터를 모두 삭제함.

현재 최근성적을 알수 있는 데이터만 남김


- 수치형 데이터 확인


![output1](https://github.com/user-attachments/assets/827bc4fd-0d52-4574-a3ef-7d8601726475)
![output](https://github.com/user-attachments/assets/20684b9e-3d3b-4b41-831b-d36ca45b507b)


수치형의 데이터는 정규분포를 따르고 있고, 0~100점 이내로 존재하기 때문에 이상치를 유지하기로 함.




- 나머지 결측치 데이터를 최빈값/평균값으로 대체

![225924](https://github.com/user-attachments/assets/9341e1a1-bbf7-4d8a-a394-9e9c47510021)
![225938](https://github.com/user-attachments/assets/e7ea6fb2-0682-4617-9aa2-aa2d9a4077c1)


삭제할 경우 데이터 손실이 크다고 생각하여 대체함.



## 2-3) 결측치 처리 완료

 - 결측치 0개

![225950](https://github.com/user-attachments/assets/8a8d99a9-034b-4383-8d7e-63f5539a9a9f)

 - 최종 데이터 (상위 5개만)

![스크린샷 2025-01-21 090042](https://github.com/user-attachments/assets/22a1d2ed-7d8f-4b73-a797-93668d605e79)

총 334개 , 15개의 컬럼 데이터

---

# 3. 데이터 특징

## 3-1) 특성별 음주 습관 (음주량에 영향을 미치는 요인)
 

### **외출시 음주량에 따른 비율**  
![output](https://github.com/user-attachments/assets/799bbe2f-8272-478f-b0a7-064809a245b3)  
전체 학생의 외출시 음주량을 전체 100%로 수치화해서 데이터로 시각화 했을때 8잔이상이 21%,5-8잔사이가 28%,전체의 절반정도인 49%가 과음을 하는 경향을 보여주고 있다.


### **성별별 외출시 음주량**  
![output1](https://github.com/user-attachments/assets/a6c8c1a1-bbed-4148-8036-12699a40d99b)  
남성과 여성으로 분류했을때 남성은 5잔이상 마시는 사람의 비율이 65.9%,여성은 5잔 이상 마시는 사람의 비율이 31%로 남성이 과음을 하는 비율이 더높은것으로 나타났다.


### **파티활동빈도별 외출 시 음주량 비율**  
![output5](https://github.com/user-attachments/assets/97469e07-e736-4e82-b763-1e9210792a43)  
파티활동의 빈도에 따른 외출시 음주량을 기준으로 시각화한 데이터의 경우 파티 활동의 빈도가 없는사람의 경우 5잔이상의 과음을 하는경우가 28.5퍼센트 주에 1회 참가하는경우 55%,주에 2회 참가하는경우 51.4%,3회이상참가 60%,4회이상은 84.6% 주말에만 파티활동을 하는 사람의경우 34.1%로 파티활동참여의 빈도가 많을수록 과음을 하는경향이 나타났다


### **용돈수준별 외출시음주량 비율**  
![output6](https://github.com/user-attachments/assets/4bc6e19d-3818-47ce-89df-14a62d0022b9)  
용돈의양에 따른 외출시음주량기준으로는 4001~ 5000 남아공 랜드화를 받는 사람이 8잔이상의 음주량인 경우가 18.2% 5001~ 6000랜드화 17.8%, 6001~ 7000랜드화 37%,7001~ 8000랜드화 19.2%,8000랜드화 이상이 20.8%로 받았으며 이의 평균을 구했을때 상대적으로 적은용돈의 범위인 4001~ 5000,5001~6000 랜드화가 평균인 18퍼센트인데 반해 6000랜드화 이상의 평균인 25.6퍼센트의 수치가 나타났다. 

### **용돈수준별 파티활동빈도 비율**  
![output7](https://github.com/user-attachments/assets/50d8892e-9358-4704-b9e0-2b798929415f)  

음주에 영향을 미치는 요인으로 용돈에 따른 파티활동의 빈도를 기준으로 볼때 3회이상 파티활동을 참여하는비율이 4001-5000 남아공 랜드화를 받는 사람의 경우 14.2%,5001-6000랜드화 14.4%, 6001-7000랜드화 28.3%,7001-8000랜드화24%, 8000랜드화 이상이 41.7%로 증가하는 추세를 보였다.


## 3-2) 성적에 영향을 미치는 요인

### **부모의 음주 허용 여부별 최근 성적 평균**
- **부모의 음주 허용 여부에 따른 부모 관계 친밀도**


![output](https://github.com/user-attachments/assets/2ed09fb7-d3c4-4eed-b7d1-6dddf2e08d45)  
부모가 음주를 허용한 경우, 그렇지 않은 경우보다 최근 성적의 평균이 더 높은 것으로 나타났다.  

![output_2](https://github.com/user-attachments/assets/bf1a1f70-38b8-4923-b841-a14bfa2b2473)

부모의 음주 허용 여부에 따른 부모 관계 친밀도를 확인해본 결과, 부모님이 음주를 허용한다고 응답했을수록 부모와의 관계도 친밀한 것으로 나타났다.  
부모와의 관계 친밀도가 최근 성적에 영향을 미쳤을 가능성이 있는 것처럼 보인다.

### **학습 시간별 최근 성적의 평균**  
![output_3](https://github.com/user-attachments/assets/c976c9a3-ae16-4951-98e2-e68aaef0fb26)  
3~5 시간 공부한다고 응답한 학생들의 최근성적평균이 가장 낮은 결과를 보인다.  
또한 0시간 공부한다고 응답한 학생들의 최근성적평균이 가장 높은 것으로 보아 학습시간과 최근성적이 서로 큰 연관이 없을 가능성이 있다.


### **파티활동빈도별 최근 성적 평균**
![output_4](https://github.com/user-attachments/assets/86fe90c8-f86f-472f-8d0e-74dea4c22fe2)  

일주일에 파티, 사교 활동에 4회 이상 참여한다고 응답한 학생들의 최근 성적 평균이 가장 낮은 것으로 나타났다.  
하지만 3회라고 응답한 학생들의 성적이 가장 높은 것으로 보아, 파티, 사교 활동이 성적에 직접적인 영향을 주지는 않을 가능성이 있는 것을 보인다.


## 3-3) 음주와 학업의 관계(음주량이 학업에 미치는 영향)

### **외출시 음주량별 낙제 횟수 비율**  
![output3](https://github.com/user-attachments/assets/e105d112-6d6c-4d18-8dec-43382071341c)  
음주와 학업의 관계에서 외출시 음주량에 따른 낙제횟수에따른  2과목이상 낙제비율이 음주를 하지않는 사람이 13.6%, 1-3 잔은 20.8 %, 3-5잔 21% ,5-8잔 29.8% 8잔이상이 28.6 %로 음주량이 많은 경우 낙제하는 과목수의 비율도 높아졌다.




### **낙제횟수별 최근 성적 평균**
- **1학년 대상 - 낙제횟수별 고교 성적 대비 최근 성적 하락 비율**  
![output_5](https://github.com/user-attachments/assets/0fc7eede-961b-4637-8340-f6540ff35482)

낙제횟수가 많을 수록, 최근 성적의 평균도 낮아지는 결과를 보였다.  

![output_6](https://github.com/user-attachments/assets/7d2cf84b-30e1-4753-98fc-39e0901d9a73)  

고등학교를 가장 최근에 졸업한 1학년을 대상으로 분석해보았을 때, 낙제 횟수가 많을 수록 고교 성적 대비 최근 성적 하락 비율도 큰 것으로 나타났다.


### **외출시 음주량별 음주로 인한 결석수 비율**
![output4](https://github.com/user-attachments/assets/a0a46e3a-a946-4263-a4f4-4446e9206f67)  
외출시 음주량에 따른 결석수의 비율은 결석수가 0인 비율이 음주하지않는사람 90.9%, 1-3잔 77.8%, 3-5잔 50% ,5-8잔 40.4%, 8잔이상은 25.7%로 점점 줄어들었고,  
3회이상 결석하는 비율은 음주를 하지않는사람과 1-3잔 마시던 사람이 5% 미만에 머물렀던것과 다르게  
3-5잔이 10.6% 5-8잔이 14.9%,8잔이상이 24.3%로  결석하는 비율이 더높은것으로 나타났다.

### **음주로인한결석수별 최근 성적 평균**
-  **1학년 대상- 음주로인한결석수별 고교 성적 대비 최근 성적 하락 비율**   
![output_7](https://github.com/user-attachments/assets/b263efbc-e144-4505-8b5e-e5cdc1e907b9)

음주로인한 결석 횟수가 많을 수록, 최근 성적의 평균도 낮아지는 결과를 보였다.  
![output_8](https://github.com/user-attachments/assets/b80be0c3-8b26-4c87-bd78-0b02eb3cf1ee)  

고등학교를 가장 최근에 졸업한 1학년을 대상으로 분석해보았을 때,  
음주로인한 결석 횟수가 많을 수록 고교 성적 대비 최근 성적 하락 비율도 큰 것으로 나타났다.

---


# 4. 결론


## 주요 내용:

### **음주량과 학업의 관계**

일주일간 파티및외출 빈도가 높거나 외출시 술을 많이 마시는 학생들은 음주로 인한 결석 횟수와 낙제 횟수가 증가하는 경향이 있었다.
또한 음주로 인한 결석횟수와 낙제횟수가 많을수록 최근 성적 평균이 낮아지는 결과가 나타났다.

**그러나**, 파티및외출빈도가 높거나, 외출시 술을 많이 마실수록 학생들의 최근 성적 평균이 직접적으로 낮아지는 결과는 확인되지 않았다. 오히려 적당한 빈도의 경우 성적에 부정적인 영향을 미치지 않는 것으로 나타났다.

학습 시간과 최근 성적 간의 관계에서도, 학습 시간이 적은 학생들의 평균성적이 높게 나타나기도 했는데, 이는 마찬가지로 학습 효율성이나 개인의 학업 역량 등 다른 요인이 성적에 더 큰 영향을 미칠 가능성이 있다는 것을 보여준다. 

음주량이나 학습 시간 외의 다른 요인이 학생의 성적에 영향을 미치는 예시로 부모음주허용여부와 최근 성적 평균의 관계의 경우, 부모가 음주를 허용한다고 응답한 학생의 최근 성적 평균이 더 높은 것으로 나타났다. 
이에 부모의 음주 허용 여부와 부모-자녀 관계를 분석한 결과, 음주를 허용한 부모와 자녀 간의 관계가 더 친밀한 경향이 있었고, 부모, 자녀간의 화목한 관계가 성적에도 긍정적인 영향을 미쳤을 가능성이 있다는 것을 보여준다.

**결론적으로**, 파티및외출의 빈도나 음주량이 성적에 직접적인 영향을 미치지 않는다고 볼 수 있으며, 낙제와 결석을 통해 간접적으로 학업 성과에 영향을 미친다고 볼 수 있다. 


## 한계점:
- 현재 데이터로는 낙제의 원인이 음주 외에 다른 요인일 가능성도 배제할 수 없다. 
- 또한 결론에서 언급한 것처럼, 학습 성과에 음주, 학습 시간이 아닌 다른 요인들이 영향을 미칠 수 있지만, 데이터 세트에 존재하는 것 외에 다른 요인들을 고려할 수 없다.
- 자기보고식 데이터(주관적인 데이터)가 다수 존재하므로, 응답이 왜곡되었을 가능성이 존재한다.
  
---


## 한 줄 회고:
**김도연**
: 데이터 전처리과정에서 수치데이터에 이상치가 나와도 이 값이 다른 값에 영향을 미치는걸 생각해서 삭제할지 또는 스케일링, 또는 이대로 유지하는 방식을 고민했고 주제에 맞게 의사결정을 해야한다는걸 느꼈습니다.


**박주은**
: 1학년들의 최근 성적과 학년 결측치를 전처리하면서, 전처리를 위해 컬럼에 대한 충분한 이해가 필수적임을 깨닫게 되었다.
효율적이고 정확한 시각화를 위해서라도 앞으로는 컬럼별 의미와 특성을 확실히 정리한 뒤에 작업하도록 해야겠다.


**서예찬**
: 


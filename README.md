## BDA 10기 최종 과제

### 1. Overview
#### 🔸프로젝트 소개
BDA 학회원 조별활동의 운영 효과 분석 및 참여 지속성 제고를 위한 이탈 방지 개선 방안 제안 

#### 🔹프로젝트 목적

BDA (Big Data Analysis) 학회원들의 참여 지속성은  조별활동과 밀접하게 연결되어 있습니다. 따라서 본 분석은 조별활동의 효과를 검토하고 이탈을 방지할 수 있는 개선 방안을 마련하고자 합니다. 

---

### 2. 팀원 소개

| <img src="images/image1.jpg" width="100"> | <img src="images/image2.jpg" width="100"> | <img src="images/image3.jpg" width="100"> | 
|------------------------------------|------------------------------------|------------------------------------|
| 김혜원                             | 박찬우                             | 변해민                             |


---

### 3. 프로젝트 기간 및 수행 내용

| 기간 | 수행 내용 |
|------|-----------|
| 2025.07.07 ~ 2025.07.31 | - EDA <br>- 베이스라인 설계 <br>- 파생변수 생성 |
| 2025.08.01 ~ 2025.08.14 | - 추가 전처리 <br>- 모델 튜닝 및 개선 |
| 2025.08.15 ~ 2025.08.25 | - 보고서 작성 <br>- 코드 정리 |

---

### 4. 프로젝트 환경 및 구성 요소
#### Tech stack
##### 사용 프로그램

| 항목 | 내용 |
|------|------|
| Language        | ![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white) |
| Development     | ![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=Jupyter&logoColor=white) ![Colab](https://img.shields.io/badge/Colab-F9AB00?style=flat&logo=Google%20Colab&logoColor=white) |
| Collaboration   | ![GitHub](https://img.shields.io/badge/GitHub-100000?logo=github&logoColor=white) ![Discord](https://img.shields.io/badge/Discord-5865F2?logo=discord&logoColor=white) |

##### 사용 라이브러리 

| 항목 | 내용 |
|------|------|
| Python       |![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white) ![matplotlib](https://img.shields.io/badge/matplotlib-11557C?style=flat&logo=matplotlib&logoColor=white) ![seaborn](https://img.shields.io/badge/seaborn-76B7B2?style=flat&logo=seaborn&logoColor=white) ![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white) ![numpy](https://img.shields.io/badge/numpy-013243?style=flat&logo=numpy&logoColor=white) ![Logistic Regression](https://img.shields.io/badge/Logistic%20Regression-4CAF50?style=flat) ![Random Forest](https://img.shields.io/badge/Random%20Forest-2E7D32?style=flat) ![Linear Regression](https://img.shields.io/badge/Linear%20Regression-1976D2?style=flat) ![OneHotEncoder](https://img.shields.io/badge/OneHotEncoder-6A1B9A?style=flat) ![LabelEncoder](https://img.shields.io/badge/LabelEncoder-6A1B9A?style=flat) ![StandardScaler](https://img.shields.io/badge/StandardScaler-00838F?style=flat)|

#### 데이터 설명 

**member (학회원 정보 테이블)**

| 컬럼명 | 설명 | 
|--------|---------|
| member_id | 학회원 고유번호 |
| generation | 기수 |
| birthday | 생년월일 | 
| school1 | 학부 대학교 | 
| major1_1 | 제1전공 |
| major1_2 | 제2전공 |
| major1_3 | 제3전공 | 
| school2 | 석사 대학교 |
| major2 | 석사 전공 | 
| job | 현재 직무 |
| company | 현재 직장 | 
| class1 | 수강분반1 | 
| class2 | 수강분반2 | 
| class3 | 수강분반3 | 
| class4 | 수강분반4 | 
| marketing_agree | 마케팅 수신 동의 여부 |
| contents_agree | 콘텐츠 동의 여부 | 
| before_id | 이전 수강시 고유번호 |
| withdrawal | 탈퇴 여부 | 

**group_study (조별활동 정보 테이블)**

| 컬럼명 | 설명 | 
|--------|------|
| member_id | 학회원 고유 번호 |
| class_code | 분반 고유 번호 | 
| generation | 기수 | 
| group_master | 조장 여부 | 
| on_offline | 온/오프라인 참여방식 | 
| group_leave | 조 탈퇴 여부 | 
| leave_point | 탈퇴 시 차감 포인트 | 
| excellent_group | 우수 조 여부 | 
| excellent_group_master | 우수 조 조장 여부 | 

**group_point (조별활동 점수 테이블)**

| 컬럼명 | 설명 | 
|--------|------|
| generation | 기수 | 
| class_code | 분반 고유 번호 | 
| group_number | 조 번호 | 
| nth_month | 해당 점수가 부여된 월차 (n개월 차) | 
| point | 부여된 점수 | 

---

### 5. 프로젝트 내용

- 📑 [보고서](./BDA%2010기%20최종과제.pdf) 
- 💻 [코드](https://colab.research.google.com/drive/1lVqfxx5VQdpSQNZkR901v7luGHW8XSyf)

#### 🔍 분석 내용 정리

#### 1. 데이터 전처리

- 1-1. 데이터 정제 
    - 잘못된 member_id 및 leave_point 값을 통일된 표기로 일괄 치환 
    - major 컬럼의 통합하여 IT관련 전공과 Non-IT 전공으로 분류 
    - leave_point의 결측치 처리 및 nan, None 값 통일
    - 각 데이터셋에 존재하지 않는 class_code와 group_number를 비정합 그룹으로 처리 및 제거 
    - 스터디 그룹셋에는 존재하지만 member 데이터셋에는 존재하지 않은 학회원 처리 

- 1-2. 중복 참여자 처리 
    - 여러 조에 참여하여 중복된 학회원 데이터 전처리 

#### 2. 개인 특성 프로파일링
- 2-1. 전체 현황 개요 
    - 전체 인원의 IT 전공 비율 파악
    - 전체 인원의 조별활동 참여 비율 및 이탈 비율 파악
- 2-2. 전공별 참여 현황
- 2-3. 참여자 활동 특성 분석 

#### 3. 우수조 프로파일링
- 3-1. 우수조·일반조 점수 분포 파악 
- 3-2. 개인특성별 우수조·일반조·미참여 비교
- 3-3. 우수조·일반조 점수 성장 추세 비교
- 3-4. 우수조·일반조 나이 분포 비교 

#### 4. 조별활동 이탈자 프로파일링
- 4-1. 탈퇴 시점 파악 

#### 5. 통계분석 (group_leave 대상)
- 5-1. 이탈 유무와 변수들간의 상관관계 분석
- 5-2. 이탈 유무와 변수들간의 카이제곱 연관성 분석
- 5-3. 랜덤포레스트 피처 중요도 분석

#### 6. 다중 회귀분석 (leave_point 대상)

#### 7. 다양성 지수
- 7-1. 조별활동 지속 요인 다양성 분석
- 7-2. 조별 성과 향상 요인 다양성 분석

#### 8. 점수 추세 분석
- 8-1. 기수별 점수 추세 및 변화량 분석
- 8-2. 9기 특화 분석 기준 및 평가 체계
    - 4개월치 데이터가 모두 존재하는 9기 데이터를 대상으로 추세 분석을 진행

---
### 6. 한 줄 소감 

| 팀원    | 소감                                                                                                                                                                                                                       |
|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 김혜원 | 본 분석을 통해 정제되지 않은 데이터를 도메인 맥락에 맞게 전처리하는 과정이 데이터 분석 전반의 신뢰도를 좌우한다는 점을 깊이 체감했다.<br>잘못된 값의 통일, 결측치 처리, 비정합 그룹 제거 등 단순해 보이는 정제 과정 역시 EDA를 통해 확인하지 않았으면 놓치기 쉽다는 것을 깨달았으며, EDA와 전처리가 잘못될 경우 이후 모든 분석 결과가 왜곡될 수 있음을 경험했다.<br>정제된 데이터를 바탕으로 학회원의 개인 특성을 프로파일링하고, 조별활동 참여 여부와 이탈 양상을 시각화뿐만 아니라 통계 분석과 회귀 분석까지 확장해 확인할 수 있었다. 이를 통해 보다 입체적으로 이해할 수 있었으며, 단순 현황 분석을 넘어 변수 간 관계를 검증하는 분석의 중요성을 느꼈다.<br>또한 점수 추세 분석을 위해 기수별 조별활동 점수 기준표를 직접 비교하였다. 이 과정은 분석 기준의 일관성이 얼마나 중요한지를 깨닫게 해주었으며, 분석 목적에 맞는 데이터 정의를 끝까지 고민하고 설명해냈다는 점에서 큰 성취감을 느낄 수 있었다. |
| 박찬우 | 조별활동이 학회원 참여 지속성에 미치는 영향을 데이터로 구조화해 해석하는 경험을 할 수 있었습니다. 단순 이탈 여부를 넘어서 개인 특성, 조 성과, 점수 추세를 함께 보며 ‘이탈률’을 설명하는 분석의 중요성을 느꼈습니다. 분석 결과를 실제 운영 개선 아이디어로 연결하는 과정에서 데이터 분석이 의사결정으로 이어지는 흐름을 명확히 이해할 수 있었습니다. 또한 회원의 참여 지속성에 대해 분류 모델을 직접 설계하고 학회원의 잔존 가능성을 예측하는 모델링을 수행했습니다. 단순 정확도 비교가 아닌 변수 중요도를 해석하며 어떤 요인이 학회원의 지속 참여에 실제로 기여하는지를 이해할 수 있었습니다. |
| 변해민 | 이전 9기 최종과제를 통해 이탈율 감소를 위한 아이디어와 전략 제시를 했다면 이번에는 변수들을 이용해 예측 성능을 높일 수 있을지 고민하는 과정에서 비슷한 데이터로 다양한 방식을 경험해볼 수 있는 좋은 경험이었다고 생각합니다.                                                                          |

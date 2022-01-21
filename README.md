<h2 align="center">🌊2021 JOISS 해양과학 빅데이터 활용 경진대회<br><br>🌿갯끈풀 발생 영향 변수 도출 및 갯벌별 위험등급 산출</h2>

<p align = "center"><img src = "README Images/상장.png" width = "400" height = "550"></p>


<h2>🌿 1. 개요</h2>

- 공모전: 2021년 해양수산부에서 주최한 [2021 JOISS 해양과학 빅데이터 활용 경진대회](https://dacon.io/competitions/official/235793/overview/description)

- 주제: 갯끈풀 발생 영향 변수 도출 및 갯벌별 위험등급 산출

- 수행기간: `2021. 09. 01 ~ 2021.10. 24`

- 수행인원: 구병모, 구희연, 양재영

- 결과 및 성과: `한국해양학회장상(2등)`

- 담당역할: IDW 보간기법을 사용하여 데이터 생성, 갯끈풀 발생 영향 변수 EDA, PCA, SMOTE, Logistic 기법을 통한 가중치 설정

<h2>🌿 2. 분석 배경</h2>

<p align = "center"><img src = "README Images/2. 갯끈풀.jpg" width = "400" height = "400"></p>

- 세계자연보전연맹(IUCN)에서 지정한 100대 악성 위해 외래 식물

- 갯끈풀이 서식하게 되면 갯벌을 초지화시킴

- 갯벌 서식 생물뿐만 아니라 철새까지 영향을 끼침

- 생태, 경제적 손실 큼

- 무엇보다도 빠른 번식력이 문제

<img src = "README Images/3. 갯끈풀 서식.JPG" width = "1000" height = "400">

<h2>🌿 3. 분석 목표</h2>

#### 갯끈풀 서식에 영향을 주는 변수 도출

#### 갯벌별 위험도 등급 부여 (위험도: 갯끈풀이 잘 자라는 환경)

<h2>🌿 4. 분석 프로세스</h2>

<p align = "center"><img src = "README Images/4. 프로세스.JPG" width = "1000" height = "300"></p>

<h2>🌿 5. 분석 내용</h2>

### 1. 데이터셋 구성

- 해양특성평가격자(약 5km)를 세분한 후, 갯벌 공간정보와 JOIN하여 1,399개의 격자 생성

<p align = "center"><img src = "README Images/5. 격자.JPG" width = "800" height = "400"></p>

- 해양데이터 특성상 모든 격자에 변수 값이 존재하지 않기 때문에 IDW 보간기법 사용

<p align = "center"><img src = "README Images/6. IDW.JPG" width = "1000" height = "400"></p>

### 2. EDA

<img src = "README Images/7. EDA.JPG" width = "1000" height = "400">

- 20개의 변수(수온, 질소, 생체량, 규산염 등)의 히스토그램과 Box Plot을 통해 왜도, 첨도, 이상치 개수 비교

<img src = "README Images/8. EDA.JPG" width = "1000" height = "400">

- 위 과정을 통해 선정된 13개의 변수(질소, 염분, 투명도 등) 상관분석

- 상관성이 높은 6개의 변수(질소, 부유물질 농도, 규산염, 화학적산소 요구량, 투명도, 총인)로 주성분분석(PCA) 실시

<img src = "README Images/9. RF.JPG" width = "1000" height = "400">
 
- Random Forest 모델의 변수 중요도를 통한 갯끈풀 영향 변수 선택

### 3. 데이터 모델링

<img src = "README Images/10. 모델링.JPG" width = "1000" height = "400">

- Logistic Regression을 통한 각 변수의 가중치 설정 (+ 유의하지 않은 변수 제거)

<img src = "README Images/11. 군집.JPG" width = "1000" height = "400">

- 군집분석(K-Means) 수행 후, 각 군집 특성을 파악하여 위험등급 설정

<img src = "README Images/12. 군집결과.JPG" width = "1000" height = "400">

<h2>🌿 6. 분석 결과</h2>

<p align = "center"><img src = "README Images/14. 최종.gif" width = "400" height = "550"></p>

- 1등급 | 최고 위험 등급 | 86개

- 2등급 | 위험 등급      | 196개

- 3등급 | 안정 등급      | 730개

- 4등급 | 최고 안정 등급 | 387개

<p align = "center"><img src = "README Images/13. 1등급.JPG" width = "400" height = "550"></p>

- 최고 위험 등급 지역은 위와 같이 산출됨
<h2>🌿 7. 참고 문헌</h2>

- 김은규, 길지현, 주영규, 정영상.(2015).미기록 외래잡초 영국갯끈풀의 국내 분포와 식물학적 특성.Weed&Turfgrass Science,4(1),65-70.

- 김진석 (한국화학연구원). (2016). 생태계 교란식물 cordgrass (Spartina spp.)의 효과적인 관리방안 수립을 위한 고찰.

- 해양환경공단. (2020). 2020년 갯끈풀 제거 및 관리 사업.

- 해양수산부. (2018). 갯벌파괴자 '갯끈풀' 없애고 갯벌 생태계 살린다.

- 충남기후정보브리핑. (2016). 갯벌 환경을 위협하는 갯끈풀 확산 피해 현안과 충천남도의 대책.

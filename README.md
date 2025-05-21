# 의약품 처방 데이터 분석 프로젝트

## 개요

국민건강보험공단에서 제공한 2019~2021년 처방 데이터를 바탕으로  
- **성별, 연령대, 지역별 처방 패턴 분석**
- **계절성과 약물군 중심의 처방 트렌드 분석**
- **ARIMA, Prophet, LSTM 기반 시계열 예측 모델 성능 비교**
- **Power BI를 활용한 시각화**  
를 수행한 의료 데이터 분석 프로젝트입니다.

> 관련 문서 링크
> - [데이터 전처리 설명](https://chungjuwon.github.io/prescription-data-analysis/data_preprocessing.html)
> - [처방 패턴 EDA 분석](https://chungjuwon.github.io/prescription-data-analysis/EDA_Prescription_Analysis.html)
> - [시계열 예측 모델 분석](https://chungjuwon.github.io/prescription-data-analysis/timeseries_forecasting_models.html)

---

## 목표

- 3년치 처방 데이터를 기반으로 주요 약물군과 사용자 특성 분석
- 계절성 질환 약물의 처방 추이 확인
- LSTM, Prophet, ARIMA 모델을 통한 처방량 예측
- Power BI 기반 시각화를 통한 인사이트 강화

---

## 데이터 개요

- **출처**: 국민건강보험공단 처방정보 표본 데이터 (공공데이터포털)
- **기간**: 2019~2021년
- **형태**: 연도별 CSV (약 3,000만건/년)

### 전처리 주요 내용
- 연도별 컬럼 구조 정제 및 통합
- 비정상 값(투약량 0 이하, 이상 코드 등) 제거
- 연·월 단위 날짜 변환, 범주형 변수 인코딩
- 병합 데이터: `processed_prescription_2019_2021.csv`

---

## 분석 주요 결과

- **Top 처방 약물**: 레바미피드, 모사프리드, 아세트아미노펜, 록소프로펜 등
- **성별 차이**: 여성의 전체 처방 비율 55.4%, 주요 진통제와 소화제에서 더 높은 비율
- **연령대별**:
  - 0~9세: 감기약 위주
  - 50세 이상: 위장약, 진통제, 변비약 중심
- **지역별**: 전국적으로 유사한 처방 경향 (표준화된 가이드라인 반영)
- **계절성 약물군**:
  - 항히스타민제: 봄/가을 집중
  - 항진균제: 여름 집중
  - 항생제: 완만한 변동

---

## 시계열 예측 모델 비교

| 모델     | MAE     | RMSE    | 평가 |
|----------|---------|---------|------|
| ARIMA    | 0.2409  | 0.3196  | 우수 |
| Prophet  | 0.2561  | 0.3816  | 준수 |
| LSTM     | 1.1883  | 1.3069  | 미흡 |

예측 대상 성분: `이트라코나졸 (항진균제)`  
ARIMA가 가장 정밀한 성능을 보였으며, Prophet은 계절성 트렌드 해석에 유리함.  
LSTM은 데이터 양 부족으로 부정확한 결과 도출.

---

## 시각화 도구

- Python (matplotlib, seaborn)
- Power BI

> [Power BI 시각화 파일 다운로드 (.pbix)](https://github.com/ChungJuwon/prescription-data-analysis/raw/refs/heads/main/powerbi_med_data_analysis.pbix)

---

## 기술 스택

- **Language**: Python 3.x
- **Visualization**: matplotlib, seaborn, Power BI
- **ML Models**: ARIMA (statsmodels), Prophet (Facebook), LSTM (TensorFlow/Keras)
- **IDE**: Jupyter Notebook, Visual Studio Code

---

## 향후 발전 방향

- **대화형 AI 기반 분석 시스템**  
  자연어로 질의하면 자동 분석 및 리포트 생성을 수행하는 AI 시스템 구축

- **고도화된 예측 모델 도입**  
  Transformer 계열 시계열 모델 (e.g., Temporal Fusion Transformer, Informer) 등 적용

- **실시간 데이터 스트리밍 분석**  
  실시간으로 들어오는 의료 데이터에 대한 트렌드 분석 및 이상 탐지

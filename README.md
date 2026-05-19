# Korea Industrial Automation Opportunity Map  
# 국내 산업자동화 영업기회 분석 포트폴리오

## 1. Project Overview

This project analyzes regional sales opportunities for industrial automation solutions in South Korea using public manufacturing, industrial complex, and registered factory data.

The goal is to build a practical **Business Development opportunity map** that identifies which regions should be prioritized for industrial automation sales coverage.

Rather than treating South Korea as one uniform manufacturing market, this project evaluates each region through three business development questions:

1. Where is the manufacturing market largest?
2. Where is the potential need for automation and manufacturing upgrade highest?
3. Where are sales targets most accessible through factories and industrial clusters?

---

## 1-1. 프로젝트 개요

이 프로젝트는 공공 제조업 데이터, 산업단지 데이터, 등록공장 데이터를 활용해 **국내 산업자동화 솔루션의 지역별 영업기회 우선순위**를 분석한 포트폴리오입니다.

단순한 데이터 분석이 아니라, 제조업 규모, 자동화 고도화 가능성, 영업 접근성을 종합해 **Business Development 관점의 지역별 Opportunity Map**을 만드는 것이 목적입니다.

핵심 질문은 다음과 같습니다.

1. 제조업 시장 규모가 가장 큰 지역은 어디인가?
2. 자동화 및 제조 고도화 수요가 높을 가능성이 큰 지역은 어디인가?
3. 실제 영업 타깃에 접근하기 쉬운 지역은 어디인가?

---

## 2. Live Notebook

You can view the full Kaggle notebook here:

[View Kaggle Notebook](https://www.kaggle.com/code/namhunk1m/korea-industrial-automation-opportunity-map)

---

## 3. Business Objective

This project was designed as a business development and go-to-market strategy portfolio.

The analysis converts public manufacturing data into a regional prioritization framework for:

- Industrial automation sales planning
- Regional territory prioritization
- Distributor and channel strategy
- Key account targeting
- Manufacturing solution go-to-market planning

### 비즈니스 목적

이 프로젝트는 산업자동화, 제조 솔루션, B2B 영업, 전략적 파트너십 포지션에서 활용할 수 있는 **데이터 기반 BD 포트폴리오**로 설계되었습니다.

분석 결과는 다음과 같은 실무 의사결정에 활용될 수 있습니다.

- 산업자동화 영업지역 우선순위 설정
- 대리점 및 채널 전략 수립
- 핵심 계정 타깃팅
- 제조 솔루션 Go-to-Market 전략
- 지역별 세일즈 커버리지 설계

---

## 4. Data Sources / 데이터 출처

This project uses public data collected from Korean government and public-sector data portals.

본 프로젝트는 국내 공공데이터 및 국가통계 기반 데이터를 활용했습니다.

### 4-1. KOSIS Korean Statistical Information Service / 국가통계포털 KOSIS

- Source: KOSIS Korean Statistical Information Service
- URL: https://kosis.kr/
- English URL: https://kosis.kr/eng/
- Used for: Regional manufacturing statistics

The manufacturing statistics dataset includes regional indicators such as:

- Number of establishments
- Number of employees
- Shipment value
- Production value
- Value added
- Annual wages

제조업 통계 데이터는 KOSIS 국가통계포털에서 수집한 데이터를 기반으로 하며, 지역별 제조업 사업체 수, 종사자 수, 출하액, 생산액, 부가가치 등을 분석에 활용했습니다.

### 4-2. Public Data Portal / 공공데이터포털

- Source: Public Data Portal Korea
- URL: https://www.data.go.kr/
- English URL: https://www.data.go.kr/en/index.do
- Used for: Industrial complex data and registered factory data

The industrial complex and registered factory datasets were collected from Korea's Public Data Portal.

The data includes indicators such as:

- Industrial complex count
- Tenant companies
- Operating companies
- Industrial complex employment
- Cumulative production value
- Cumulative export value
- Registered factory company names
- Industrial complex names
- Product descriptions
- Factory addresses

산업단지 데이터와 등록공장 데이터는 공공데이터포털에서 수집한 데이터를 기반으로 하며, 산업단지 수, 입주업체 수, 가동업체 수, 고용, 생산액, 수출액, 등록공장 주소 및 생산품 정보를 분석에 활용했습니다.

### 4-3. FactoryOn / 한국산업단지공단 공장설립온라인지원시스템

- Related portal: https://www.factoryon.go.kr/
- Used for: Understanding registered factory and industrial complex-related public data context

Some factory and industrial complex-related public datasets are provided through or associated with Korea Industrial Complex Corporation and FactoryOn-related public data.

한국산업단지공단 및 FactoryOn 관련 공공데이터는 등록공장 현황과 산업단지 관련 정보를 이해하는 데 활용되었습니다.

### 4-4. Data Processing Note / 데이터 처리 참고

The original datasets used different regional naming formats.  
Therefore, region names were standardized into 17 Korean administrative regions before analysis.

Factory addresses and industrial complex names were used to extract regional information.  
Rows with missing regional information after correction accounted for less than 1% of the total registered factory records and were excluded from the v1 analysis.

원본 데이터는 지역명 표기 방식이 서로 달랐기 때문에, 분석 전에 17개 시도 기준으로 지역명을 표준화했습니다.

등록공장 데이터는 공장주소를 우선 사용해 지역을 추출했고, 주소가 비어 있거나 지역명이 명확하지 않은 경우 산업단지명을 보완적으로 활용했습니다. 최종적으로 지역을 식별하지 못한 데이터는 전체 등록공장 데이터의 1% 미만이었으며, v1 분석에서는 제외했습니다.

---

## 5. Methodology

The analysis follows six steps:

1. Load public manufacturing, industrial complex, and registered factory datasets
2. Standardize regional names into 17 Korean administrative regions
3. Aggregate all datasets at the regional level
4. Create business development indicators through feature engineering
5. Build a weighted opportunity scoring model
6. Translate the ranking into go-to-market recommendations

### 분석 방법론

분석은 다음 순서로 진행했습니다.

1. CSV 데이터 로딩
2. 컬럼, 데이터 타입, 지역명 확인
3. 지역명 표준화
4. 등록공장 주소 및 산업단지명을 활용한 지역 보완
5. 지역 단위 데이터 집계
6. 파생변수 생성
7. Opportunity Score 계산
8. 시각화
9. BD 전략 인사이트 도출

---

## 6. Opportunity Scoring Model

The final score is based on three dimensions:

### Market Scale Index — 40%

Measures the overall size of the regional manufacturing market using:

- Shipment value
- Production value
- Value added
- Employees
- Establishments

### Manufacturing Upgrade Potential Index — 30%

Measures the potential need and capacity for automation investment using:

- Shipment per establishment
- Production per establishment
- Value added per establishment
- Employees per establishment
- Production per operating company

### Sales Accessibility Index — 30%

Measures how reachable the market is from a sales perspective using:

- Registered factories
- Registered factories per establishment
- Tenant companies
- Operating companies
- Operating company ratio

Final formula:

```text
Opportunity Score v1 =
40% Market Scale Index
+ 30% Manufacturing Upgrade Potential Index
+ 30% Sales Accessibility Index
```

Percentile rank normalization was used to reduce distortion from outlier values.

### 점수 모델 설명

최종 Opportunity Score는 세 가지 축으로 구성했습니다.

### Market Scale Index / 시장 규모 지수

지역별 제조업 전체 규모를 측정합니다.

### Manufacturing Upgrade Potential Index / 제조 고도화 가능성 지수

사업장당 출하액, 생산액, 부가가치, 종사자 수 등을 통해 자동화 투자 여력을 추정합니다.

### Sales Accessibility Index / 영업 접근성 지수

등록공장 수, 입주업체 수, 가동업체 수, 산업단지 가동률 등을 통해 실제 영업 타깃 접근 가능성을 측정합니다.

---

## 7. Key Findings

The v1 model identifies the following top opportunity regions:

| Rank | Region | Strategic Meaning |
|---:|---|---|
| 1 | Gyeonggi | Largest addressable manufacturing market |
| 2 | Chungnam | High-value advanced manufacturing opportunity |
| 3 | Gyeongnam | Balanced manufacturing opportunity |
| 4 | Gyeongbuk | Balanced manufacturing opportunity |
| 5 | Jeonnam | High-upgrade-potential manufacturing market |

### 핵심 결과

v1 점수 모델 기준 상위 지역은 다음과 같습니다.

| 순위 | 지역 | 전략적 의미 |
|---:|---|---|
| 1 | 경기 | 가장 큰 제조업 주소지정 가능 시장 |
| 2 | 충남 | 고부가 첨단 제조업 기회 |
| 3 | 경남 | 균형 잡힌 제조업 영업기회 |
| 4 | 경북 | 균형 잡힌 제조업 영업기회 |
| 5 | 전남 | 제조 고도화 가능성이 높은 지역 |

---

## 8. Business Development Interpretation

### Gyeonggi

Gyeonggi ranks first due to its dominant manufacturing scale and high sales accessibility.

It should be treated as the primary broad sales coverage market for pipeline generation, distributor expansion, and multi-industry account targeting.

### Chungnam

Chungnam combines strong market scale with high manufacturing upgrade potential.

It may be attractive for automation opportunities related to semiconductors, displays, batteries, materials, components, and advanced manufacturing facilities.

### Gyeongnam and Gyeongbuk

Gyeongnam and Gyeongbuk show balanced profiles across market size, manufacturing base, and accessibility.

These regions may be suitable for vertical-specific sales plays in machinery, industrial equipment, automotive parts, shipbuilding, and heavy manufacturing.

### Ulsan and Jeonnam

Ulsan has the highest manufacturing upgrade potential, while Jeonnam also shows strong upgrade potential.

These regions may be better approached through selective strategic account targeting rather than broad outbound sales coverage.

### Incheon, Seoul, Daegu, and Busan

These regions show relatively strong sales accessibility.

They may be effective for channel partnerships, distributor management, SI collaboration, headquarters sales, and service coverage expansion.

---

## 8-1. BD 전략 해석

### 경기

경기는 제조업 사업체 수, 출하액, 등록공장 수 측면에서 가장 큰 시장입니다.

따라서 대규모 영업 커버리지, 파이프라인 생성, 대리점 확대, 다산업 타깃팅에 적합한 1순위 지역으로 볼 수 있습니다.

### 충남

충남은 시장 규모와 제조 고도화 가능성이 모두 높은 지역입니다.

반도체, 디스플레이, 배터리, 소재/부품, 첨단 제조시설 관련 자동화 솔루션의 타깃 지역으로 해석할 수 있습니다.

### 경남 / 경북

경남과 경북은 시장 규모, 제조 기반, 영업 접근성이 균형 잡힌 지역입니다.

기계, 산업장비, 자동차 부품, 조선, 중공업 관련 자동화 솔루션의 영업 타깃으로 적합합니다.

### 울산 / 전남

울산과 전남은 제조 고도화 가능성이 높은 지역입니다.

다만 광범위한 아웃바운드 영업보다는 대형 제조 고객, 핵심 공장, 앵커 계정 중심의 전략적 영업 방식이 더 적합합니다.

### 인천 / 서울 / 대구 / 부산

이 지역들은 영업 접근성이 상대적으로 높은 지역입니다.

직접 공장 자동화 타깃팅뿐 아니라 대리점, SI, 본사 영업, 파트너십, 서비스 커버리지 확대 관점에서 접근할 수 있습니다.

---

## 9. Visualization Summary / 시각화 요약

The notebook includes three core visualizations:

1. **Top 10 Regions by Opportunity Score**  
   Highlights the strongest overall opportunity regions, with the top three regions emphasized.

2. **Market Scale vs. Manufacturing Upgrade Potential**  
   Compares each region by total market size and upgrade potential, while highlighting key strategic regions.

3. **Sales Accessibility Ranking**  
   Shows which regions offer the strongest reachable sales base through registered factories and active industrial clusters.

노트북에는 세 가지 핵심 시각화가 포함되어 있습니다.

1. **Opportunity Score 기준 Top 10 지역**
2. **시장 규모 vs 제조 고도화 가능성 점도표**
3. **영업 접근성 기준 Top 10 지역**

---

## 10. Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Kaggle Notebook
- GitHub

---

## 11. Portfolio Value

This project demonstrates the ability to:

- Clean and standardize public datasets
- Build a business-oriented scoring model
- Translate data analysis into sales strategy
- Prioritize regions for go-to-market planning
- Communicate technical analysis as a business development portfolio

### 포트폴리오 가치

이 프로젝트는 다음 역량을 보여주기 위해 제작되었습니다.

- 공공데이터 수집 및 정리
- Python 기반 데이터 분석
- 지역명 표준화 및 데이터 병합
- 비즈니스 목적에 맞는 점수 모델 설계
- 분석 결과를 영업전략과 GTM 전략으로 전환
- 산업자동화/제조 솔루션 시장에 대한 BD 관점 제시

---

## 12. Limitations and Next Steps

This is a v1 model based on regional-level public data, so the results should be interpreted as a directional sales prioritization framework rather than a final account-level targeting list.

Future improvements may include:

- Industry-level segmentation
- Company-level account targeting
- Automation equipment category mapping
- Distributor and channel network data
- Revenue potential estimation by region and industry
- Integration with CRM or sales pipeline data

### 한계 및 다음 단계

이 분석은 지역 단위 공공데이터를 기반으로 한 v1 모델입니다.

따라서 최종 계정 타깃 리스트라기보다는 **지역별 영업 우선순위를 판단하기 위한 방향성 있는 프레임워크**로 해석하는 것이 적절합니다.

향후에는 다음 요소를 추가해 분석을 고도화할 수 있습니다.

- 산업별 세분화
- 기업 단위 계정 타깃팅
- 자동화 장비 카테고리 매핑
- 대리점 및 채널 네트워크 데이터
- 지역/산업별 매출 잠재력 추정
- CRM 또는 실제 세일즈 파이프라인 데이터 연동

---

## 13. References / 참고 출처

- KOSIS Korean Statistical Information Service: https://kosis.kr/
- KOSIS English Service: https://kosis.kr/eng/
- Public Data Portal Korea: https://www.data.go.kr/
- Public Data Portal English Service: https://www.data.go.kr/en/index.do
- FactoryOn: https://www.factoryon.go.kr/

---

## 14. Author

Created by **Namhun Kim**

Business Development | Strategic Partnerships | Industrial Technology | Data-Driven GTM Strategy



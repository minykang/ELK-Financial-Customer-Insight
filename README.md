# 💳 ELK 기반 금융 데이터 분석 및 잠정 고객 발굴

## 📌 프로젝트 개요
 본 프로젝트는 금융 실무 데이터를 기반으로 우리카드 고객의 라이프스테이지 변화에 따른 소비 패턴을 분석합니다. ELK 스택을 활용하여 소비 성장세가 뚜렷한 **잠정 고객**을 식별하고 데이터 기반의 정교한 타겟 마케팅 시나리오를 제안합니다.



---

<br>

## 🎯 프로젝트 목표 (Project Goals)

### 1. 비즈니스 관점
* **실무 데이터 인사이트 도출**: 8개 분기 시계열 데이터를 분석하여 유의미한 소비 트렌드 및 타겟 고객군 발굴
* **직관적인 의사결정 지원**: 복잡한 금융 데이터를 Kibana 대시보드로 시각화하여 마케팅 전략 수립의 가독성 확보


### 2. 기술적 관점
* **인프라 구축**: **LINUX OS** 환경 내 ELK 스택 설치 및 포트포워딩 설정
* **데이터 파이프라인**: DuckDB를 활용하여 대량의 데이터를 전처리하고 Elasticsearch에 최적화하여 인덱싱
* **성능 최적화**: 대시보드 조회 성능 향상을 위한 인덱스 매핑 최적화

---

<br>


## 👥 팀 구성 및 역할
| <img src="https://github.com/minykang.png" width="150px"> | <img src="https://github.com/janie71.png" width="150px"> | <img src="https://github.com/septeratz.png" width="150px"> | <img src="https://github.com/Sungjun24s.png" width="150px"> |
| :---: | :---: | :---: | :---: |
| **[강민영](https://github.com/minykang)** | **[이유진](https://github.com/janie71)** | **[septeratz](https://github.com/septeratz)** | **[Sungjun24s](https://github.com/Sungjun24s)** |



---


<br>

## 🛠 기술 스택 (Tech Stack)
* **Language/DB**: SQL, DuckDB (복합 CTE 및 Delta 로직 구현)
* **Search Engine**: **Elasticsearch** (대용량 금융 데이터 인덱싱)
* **Visualization**: **Kibana** (Lens를 활용한 다차원 시각화 및 대시보드 구축)
* **Collaboration**: Git / GitHub, VS Code

---
<br>


## 🔍 핵심 분석 1: 소비 증감 분석
8개 분기 데이터를 전반기(23Q3~24Q2)와 후반기(24Q3~25Q2)로 나누어 비교했습니다.
* **분석 로직**: $$Delta\_Value = \sum Second\_Half - \sum First\_Half$$
* **목적**: 0원을 기준으로 소비가 늘어난 Increase (+) 그룹을 잠정 우량 고객으로 식별.


### 1. 사회초년생

### 시각화 결과
![alt text](image.png)
> **Insight**: 히스토그램에서 0점 우측의 'Increase' 유저를 집중 마케팅 타겟으로 선정.

![alt text](image-1.png)
> **Insight**: 특정 시점의 과소비가 아닌, 분기별로 꾸준히 비중이 상승하는 성장형 고객 확인.

---

<br>

### 2. 신혼부부
결혼 준비 및 신혼 생활 시작 단계에서 발생하는 대규모 지출 패턴을 분석했습니다.

### 1. 타겟 고객 식별
![alt text](image-2.png)
> **Insight**: 신혼부부 그룹 역시 0점 우측의 **'Increase (+)'** 그룹이 핵심 타겟입니다. 결혼 전후로 소비 여력이 급격히 상승한 이 유저들을 대상으로 프리미엄 카드 발급 및 고액 할부 혜택 마케팅을 전개할 수 있습니다.

### 2. 업종별 소비 비중 분석 (Category Insight)
소비가 증가한 유저들이 실제로 어떤 분야에 지출을 집중하고 있는지 42개 세부 업종별로 분석했습니다.

![alt text](image-3.png)
> **Insight (Pie Chart)**:
> - **유통/쇼핑 (약 47%)**: 유통(대) 및 유통업영리 비중이 압도적이며 일상적인 쇼핑 혜택에 민감한 그룹임을 확인했습니다.
> - **요식업 (11.2%)**: 외식 및 배달 소비가 주요 지출 항목 중 하나로 나타났습니다.
> - **잠정 고객 제안**: 분석된 업종 비중에 맞춰 **대형마트 할인** 및 **배달 앱 캐시백** 서비스가 포함된 카드 상품을 제안할 수 있습니다.


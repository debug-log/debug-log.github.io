---
layout: project
title: 온라인 게임 이탈요인 분석 및 대시보드 구축
description: 설문으로 부정 경험 수집 후 이탈 유저와 잔존 유저의 경험을 비교
img: assets/projects/1_churn_analysis/preview.png
importance: 1
category: Research
date: 2023-06-01
role: 프로젝트 리딩, 참여율 50%
skills: Python, Spark, Tableau
---


---
<br>

#### 1. 배경

- 온라인 커뮤니티, VoC 수집을 통해 유저들이 겪는 여러 부정 경험을 수집한 상황
- 어떤 부정 경험이 정말 이탈에 영향을 주는지를 알고 싶음

<br>

#### 2. 목표

- 온라인 게임 유저의 주요 이탈 원인 분석을 파악하여 액션플랜 도출

<br>

#### 3. 과정

- 유저들의 주요 부정 경험들을 분류하여 설문조사 설계
    - 약 10가지 카테고리로 구분. 총 50여 개의 부정 경험을 정의함
- 이탈 위험이 높은 유저에게 설문을 배포하여 부정 경험 응답을 수집
    - 이탈 확률은 Data Scientist가 개발한 모델을 활용
- 수집된 설문 데이터는 ETL을 거쳐 Tableau에서 시각화할 수 있는 테이블로 적재
    - Spark, Airflow 활용
    - D+N Day 이탈 여부 판단, 유저 세그먼트 구분을 위한 데이터 조인

<div class="row">
    <div class="col-sm mt-md-0" style="text-align: center;">
        {% include figure.html path="assets/projects/1_churn_analysis/dashboard.png" title="Tableau로 시각화한 결과물 예시" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Tableau로 시각화한 결과물 예시
</div>

- Tableau를 활용하여 시각화

<br>

#### 4. 결과

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/1_churn_analysis/churn.png" title="이탈 유저와 잔존 유저의 응답 비교" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    이탈 유저와 잔존 유저의 응답 비교
</div>

- 설문 응답 이후 실제 이탈 여부를 트래킹하여 이탈 유저와 잔존 유저의 응답을 비교 분석
- 유저 세그먼트별 분석 (코어, 미들, 라이트 구분)


<br>

#### 5. 주요 성과

- 이탈 유저와 잔존 유저의 응답 결과를 비교하여 부정 경험의 우선순위화
- 우선순위가 높은 부정 경험에 대해 액션 플랜 수립 근거 마련

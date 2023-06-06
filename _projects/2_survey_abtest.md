---
layout: project
title: 설문조사 개인화 응답률 A/B 테스트
description: 설문조사 응답률 향상시키기 위해 개인화된 설문의 효과를 검증
img: assets/projects/2_survey_abtest/preview.png
importance: 2
category: Research
date: 2023-05-01
role: 테스트 설계 및 분석
---



---
<br>

#### 1. 배경

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/2_survey_abtest/survey_example.png" title="(1) 이미지 배너형 설문조사 예시" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/2_survey_abtest/personalization_example.jpeg" title="(2) 개인화 텍스트 기능 예시" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    (1) 이미지 배너형 설문조사 예시, (2) 개인화 텍스트 기능 예시
</div>

- 기존에는 게임 종료 화면의 이미지 배너 노출을 통해 설문 조사 참여를 유도함
- 이미지 배너 대신 유저의 게임 데이터를 가져와 개인화된 텍스트를 넣을 수 있는 기능이 추가됨
- 개인화 기능을 활용하여 설문을 노출한다면, 설문 참여율이 더 높아질 것이라는 가설을 세움


<br>

#### 2. 목표

- 개인화된 설문 노출 방식의 참여율 증가 효과를 검증
- 기존 이미지 배너 방식에 비해 효과가 유의미하다면, 해당 방식을 채택하여 전체 유저에게 적용

<br>

#### 3-1. 실험 (1주차)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/2_survey_abtest/survey_a_1.png" title="(A) 이미지 배너 (기존)" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/2_survey_abtest/survey_b.png" title="(B) 개인화 설문" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    (A) 이미지 배너 (기존), (B) 개인화 설문
</div>


- 사용자를 A그룹과 B그룹으로 분리하여 A안, B안을 노출함
- A그룹에는 기존에 노출하던 방식을 유지하고, B그룹은 유저 닉네임을 호명하며 설문 참여를 유도함
- 결과
  - B안의 노출 대비 설문 응답률이 A안 대비 약 3배 높았음
  - 유저들이 기존에 보지 못한 새로운 유형의 설문 유형이라 일시적으로 참여율이 높아졌을 수 있음

<br>

#### 3-2. 실험 (2주차)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/2_survey_abtest/survey_a_2.png" title="(A) 이미지 배너 (신규)" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/2_survey_abtest/survey_b.png" title="(B) 개인화 설문" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    (A) 이미지 배너 (신규), (B) 개인화 설문
</div>

- A그룹의 이미지 배너도 새로운 디자인으로 변경하고, B그룹은 개인화 설문을 그대로 유지
- 결과
  - B안의 노출 대비 설문 응답률이 A안 대비 약 2.5배 높았음
  - A, B그룹 모두 노출 대비 설문 응답률이 1주 차와 거의 동일함
  - 이미지 배너 타입에서는 새로운 디자인을 적용하더라도 응답률 변화가 거의 없었음

<br>

#### 3-3. 실험 (3주차)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/2_survey_abtest/survey_a_3.png" title="(A) 개인화 설문 (유저명 미포함)" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/2_survey_abtest/survey_b.png" title="(B) 개인화 설문 (유저명 포함)" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    (A) 개인화 설문 (유저명 미포함), (B) 개인화 설문 (유저명 포함)
</div>

- A그룹을 유저명을 포함하지 않고 고정된 텍스트로 노출, B그룹은 개인화 설문을 그대로 유지
- 결과
  - B안의 노출 대비 설문 응답률이 A안 대비 약 1.2배 높았음
  - 개인화된 설문의 효과가 유의미하다고 판단. 신뢰수준 95%에서 p-value가 약 0.05

<br>


#### 4. 주요 성과

- 개인화된 설문 노출의 효과를 측정할 수 있었음 (약 20% 상승)
- 계속 동일한 디자인의 설문을 노출하는 것보다 정기적으로 변경하는 것이 효과가 있음을 확인



---
layout: project
title: 설문 데이터 분석 툴 개발
description: 대량의 설문조사 주관식 응답 데이터를 분석하여 시각화
img: assets/projects/4_survey_tool/preview.png
importance: 4
category: Tool
date: 2022-08-01
role: 개발 전담
skills: VBA, Python (tkinter)



---




---
<br>

#### 1. 배경

- 설문조사 결과를 분석하는 데에 시간 리소스가 많이 발생함
    - 기존에는 엑셀 피벗테이블 기능을 활용하여 수동으로 분석함
- 반복적인 업무로 UX리서처들이 설문 데이터를 깊이 분석할 시간이 항상 부족했음


<br>

#### 2. 목표

- 설문 결과 분석에서 반복적입 작업을 최대한 자동화
- UX리서처들이 사용할 수 있도록 인하우스 툴 개발하기

<br>

#### 3. 과정

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/4_survey_tool/tool_vba.png" title="VBA로 개발한 엑셀 매크로" class="img-fluid rounded z-depth-1"  zoomable=true %}
    </div>
</div>
<div class="caption">
    VBA로 개발한 엑셀 매크로
</div>

- 초기에는 대부분이 MS Office를 사용하는 것을 고려하여 VBA로 자동화 툴을 개발함
    - PPT로 바로 복사가 가능하도록 차트 생성이 필요했음
- 약 1년 정도 사용하다보니 필요한 기능이 점차 늘어나고, VBA로는 유지보수하기도 어려웠음
- 향후 확장성을 고려하여 다양한 라이브러리를 활용할 수 있는 Python으로 GUI 툴을 개발하기로 결정

<br>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/4_survey_tool/tool_python.png" title="Python으로 개발한 GUI 설문조사 분석 툴" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Python으로 개발한 GUI 설문조사 분석 툴
</div>

- Python 기본 라이브러리에 포함된 tkinter로 GUI를 구현
    - 전반적인 디자인은 오픈소스 통계 분석 도구인 jamovi를 참조
- xlsx 또는 csv 파일을 불러와 데이터를 전처리하고, 분석할 수 있는 기능 구현함


<br>

#### 4. 결과

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/4_survey_tool/tool_result.png" title="(1) 빠른 요약 결과 예시" class="img-fluid rounded z-depth-1"  zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/4_survey_tool/report_result.png" title="(2) 서식을 입혀 보고서에 활용" class="img-fluid rounded z-depth-1"  zoomable=true %}
    </div>
</div>
<div class="caption">
    (1) 빠른 요약 결과 예시, (2) 서식을 입혀 보고서에 활용
</div>

- 전처리 기능
    - 불성실 응답 전처리: 동일한 문항만 선택해서 제출하는 불성실 응답 데이터를 구분
    - 주관식 길이 전처리: 너무 짧게 작성한 주관식 문항을 구분
- 분석 기능
    - 복수 응답 분석: 복수 선택한 답변을 콤마(,)로 구분 후 표를 생성하여 엑셀로 저장
    - 결과 빠른 요약: 문항(N개)과 교차 분석(M개)할 변수를 선택하여 N x M 개의 표를 생성하여 엑셀로 저장

<br>


#### 5. 주요 성과

- 설문 결과 분석에 걸리는 소요 시간을 약 90% 이상 단축



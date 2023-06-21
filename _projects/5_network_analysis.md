---
layout: project
title: 주관식 네트워크 분석 툴 개발
description: 대량의 설문조사 주관식 응답 데이터를 분석하여 시각화
img: assets/projects/5_network_analysis/preview.png
importance: 5
category: Tool
date: 2021-08-01
role: 유지 보수 및 고도화
skills: R (Shiny)
---




---
<br>

#### 1. 배경

- 대량의 설문조사 주관식 텍스트 데이터를 분석하려면 많은 시간과 비용이 들어감
- 워드클라우드는 단어 간의 연관성이나 주요 토픽을 알 수 없으며, 토픽 모델링은 UX 리서처 실무자들이 활용할 만큼의 성능이 나오지 않았음
- 단어-문서 간 연관성을 네트워크 분석을 통해 시각화한 툴을 유지보수함
    - 최초 개발했던 인원이 퇴사하여 담당자가 없던 상황에서 담당하게 됨


<br>

#### 2. 목표

- 대량의 설문조사 주관식에서 나온 의견들 중에서 주요 의견을 한 눈에 파악하기 쉬워야 함

<br>

#### 3. 과정

- 각 주관식 텍스트 데이터를 형태소 단위로 나눔
    - NLP4kec 패키지 사용 [[Link]](https://github.com/NamyounKim/NLP4kec)
- 전처리
    - 불용어 리스트에 포함된 단어는 제거
    - 사용자 지정 단어 제거
- 단어 빈도 구하기
    - Document-Term-Matrix를 생성하여 유저별로 언급한 단어의 빈도를 카운팅 (중복 제외)
- 단어간 상관계수 계산
    - TF-IDF 가중치를 적용하여 Document-Term-Matrix를 생성
    - 전체 Document에서 최소 [ ]% 이상 등장하지 않은 단어는 제거
    - DTM의 상관관계를 구하고, 연관성이 [ ]이하인 단어는 제거
- 단어의 빈도로 네트워크 node의 크기를, 단어간 상관계수로 네트워크 edge의 굵기를 다르게 표현  


<br>

#### 4. 결과

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/5_network_analysis/naver_shopping_positive.png" title="(1) 네이버 쇼핑 제품 후기 (긍정)" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/5_network_analysis/naver_shopping_negative.png" title="(2) 네이버 쇼핑 제품 후기 (부정)" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    (1) 네이버 쇼핑 제품 후기_긍정, (2) 네이버 쇼핑 제품 후기_부정. <a href="https://github.com/bab2min/corpus/tree/master/sentiment">[데이터 출처]</a>
</div>
- 시각화 결과
    - ggnet2 라이브러리를 이용해 네트워크 시각화

<br>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/5_network_analysis/shiny.png" title="Shiny 웹 어플리케이션" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Shiny를 활용하여 웹 어플리케이션으로 배포 
</div>

<br>

#### 5. 주요 성과

- 대량 설문의 주관식 분석 시간 비용을 절감
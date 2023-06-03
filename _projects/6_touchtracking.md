---
layout: project
title: 모바일 게임 터치트래킹 분석
description: 모바일 게임 가상 조익스틱 조작의 불편하다는 가설을 검증하기 위해 터치 영역을 히트맵으로 시각화한 프로젝트
img: assets/projects/6_touchtracking/preview.png
importance: 6
category: Research
date: 2020-07-01
role: 구현 및 시각화 전담
skills: Python
---



---
<br>

#### 1. 배경

- 신규 모바일 게임의 게임성을 검증하는 과정에서 조작성에 이슈가 있을 것으로 가설을 세움
- 캐릭터의 조작이 불편했으며, 근본적인 원인이 가상 조이스틱의 중심 영역이 유저의 생각보다 너무 쉽게 움직여 Thumb Zone을 자꾸 벗어나게 될 것이라는 가설을 세움


<br>

#### 2. 목표

- 사용자가 모바일 게임의 가상 조이스틱을 조작할 때 터치하는 영역을 시각화
- 조작에 이슈가 있을 것으로 판단하는 게임 vs 타 게임의 조작 범위를 비교하기

<br>

#### 3. 과정

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/6_touchtracking/adb.png" title="(1) adb를 활용해 디바이스 로그를 기록 중" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/6_touchtracking/touchlog.png" title="(2) 기록된 텍스트 파일" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    (1) adb를 활용해 디바이스 로그를 기록 중, (2) 기록된 텍스트 파일
</div>

- 안드로이드 디버깅 툴(adb)을 활용해 테스터가 플레이하는 동안의 터치 영역을 기록
- 디바이스에 기록된 터치 좌표 텍스트파일을 전처리하여, time 및 x, y 좌표 값을 가지는 DataFrame으로 변환  

<br>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.html path="assets/projects/6_touchtracking/output_brawlstars.mp4" class="img-fluid rounded z-depth-1" width="auto" controls=true %}
    </div>
</div>
<div class="caption">
    Brawl Stars 플레이 영상에 터치 기록을 시각화
</div>
- 터치 영역이 잘 트래킹 되는지 동영상에 매핑하여 확인함  


<br>

#### 4. 결과

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/6_touchtracking/brawlstars.png" title="(1) Brawl Stars 터치 히트맵" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/projects/6_touchtracking/battleground.png" title="(2) PUBG 모바일 터치 히트맵" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    (1) Brawl Stars 터치 히트맵, (2) PUBG 모바일 터치 히트맵
</div>
- 터치 영역을 이미지에 히트맵으로 시각화하여 타 게임의 히트맵과 비교함
  - 보안 이슈로 타 게임의 이미지를 활용함
- 히트맵을 확인한 결과, 가상 조이스틱이 너무 많이 움직여 Thumb Zone에서 많이 벗어나 불편하다는 것을 검증  

<br>

#### 5. 주요 임팩트

- 가상 조이스틱의 중심영역이 너무 많이 움직여 조작이 불편하다는 가설을 채택
- 테스터의 정성의견과 종합하여 개발팀에 조작 이슈에 대한 근거를 제시하여 조작 방식을 변경함

    



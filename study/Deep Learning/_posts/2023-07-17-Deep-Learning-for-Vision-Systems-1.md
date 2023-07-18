---
layout: post
title: Deep Learning for Vision Systems - 1
description: >
  Howdy! This is the summary note for "Deep Learning for Vision Systems"
#sitemap: false
hide_last_modified: true
categories: [Deep Learning]
---

# 1.1 컴퓨터 비전
모든 인공지능 핵심 개념은 스스로 처한 환경을 인식하고, 그 인식을 기반으로 무언가 조치를 취한다는 것이다. 컴퓨터 비전은 시각적 인지 부분을 다룬다. 

### 1.1.1 시각적 인지
시각적 인지 (visual perception)이란 시야나 시각적 입력으로 패턴을 관찰하는 행위를 관찰하는 행위를 말한다. 단순한 스캔에서 그치지 않고 주변 사물과 상태를 이해한다.

### 1.1.2 비전 시스템
이미지를 통해 어떤 일이 일어났는지 이해하는 것은 이미지 처리와는 전혀 다름. 이미지 처리는 이미지의 내용을 해석하기 위한 한 구성 요소일 뿐. 일반적인 시각 시스템은 이미지를 받아들이는 시각센서인 눈과 이미지를 해석하는 뇌로 구성됨. 시스템의 출력은 이미지에서 얻은 데이터를 기반으로 한 예측 결과이다. 컴퓨터 비전 알고리즘 역시 두가지 요소, 감지장치와 해석 장치로 나누어진다. 

### 1.1.3 감지 장치
시스템을 설계할 때는 시스템이 처한 주변환경을 잘 파악하는 감지장치를 선택해야 함. 목적에 맞게 시스템을 설계해야 함으로 목적을 파악하는 것으로 시작된다. 

### 1.1.4 해석 장치
컴퓨터 비전 알고리즘이 맡는 역할. 감지 장치에서 출력한 이미지를 받아 사물을 인식하는 특징과 패턴을 학습하는 역할. 인공 뇌를 만들려는 시도의 결과가 인공 신경망 ANN (Artificial Neural Network)이다. 뉴런이 주 처리 단위 역할을 하여 입력 신호를 받아 출력을 내보냄. 입력 신호가 일정 이상 활성화 되면 자기랑 연결된 모든 뉴런에 신호를 일으킴. 이를 연결하고 층을 구성하면 학습 능력을 보임. 이 기법이 딥러닝이다. 


# 1.2 컴퓨터 비전 응용 분야
image classification은 미리 정의한 유한한 수의 레이블을 이미지에 부여하는 과제이다. 여기서 활약하는 것이 CNN 합성곱 신경망이다. 

### 사물 탐지와 위치 인식
입력받은 이미지를 여러조각으로 나누어 각 조각을 대상으로 인식된 사물에 대해 레이블을 부여함.
### 화풍 모방하기
### 새로운 이미지 창조하기
생성적 적대 신경망 Generative Adversarial network 은 CNN을 발전시킨 모델로 기존에 없던 것을 창조한다. 
### 안면 인식
사람의 이미지를 정확하게 식별하거나 태그를 지정하는 기술.
### 이미지 추천 시스템

# 1.3 컴퓨터 비전 파이프라인 전체 처리 과정
해석 장치에서 이미지를 이해하기 위한 처리과정을 보자. 
1. 데이터 입력  
컴퓨터에서 카메라같은 장치를 통해 이미지를 입력 받는다. 일련의 이미지로 구성됨.  

2. 전처리  
입력을 표준화하는 전처리 단계이다. 크기 조정, 흐릿하게 하기, 회전, 모양 변경, 색상 조정등. 표준화를 해야 이미지의 비교 분석이 가능함.  

3. 특징 추출  
특징(feature)이란 사물을 식별할 수 있는 정보로 사물의 모양이나 색 등을 포함한다. 이 단계에서의 출력은 이미지의 사물 모양을 나타내는 특징 벡터(feature vector)이다.  

4. 머신러닝 모델  
추출된 특징을 분류 모델에 입력한다. 이미지 속 대상이 각 클래스 속할 확률이 출력됨.  

# 1.4 이미지 입력
## 1.4.1 함수로 나타낸 이미지  
이미지는 2차원 영역을 정의하는 x, y 두 변수의 함수 형태로 나타낼 수 있다. 이미지는 격자로 채운 픽셀로 구성되며, 각 좌표의 빛의 강도를 나타낸다. 회색조 이미지는 좌표 (x, y)에 위치한 픽셀의 빛의 강도 F(x, y)로 표현됨.  

컬러 이미지는 픽셀을 색의 강도를 나타내는 3개의 숫자로 표현한다. RGB, HSV, Lab 등의 체계는 다를지언정 픽셀값을 표현하는 방법은 동일함. RGB 이미지는 F(x, y) = [red(x, y), green(x, y), blue(x, y)]으로 표현 가능하다.  

이런 함수로 이미지를 생각하면 연산을 통해 새로운 이미지 G(x, y)로 변환도 가능하다. 

- 이미지 어둡게 : G(x ,y) = 0.5 * F(x, y)
- 이미지 밝게 : G(x, y) = 2 * F(x, y)
- 사물의 위치를 150 픽셀 아래로 : G(x, y) = F(x, y + 150)
- 회색 픽셀을 흰색 또는 검은색으로 변환 : G(x, y) = {0 if F(x, y) < 130, 255 otherwise}

## 1.4.2 컴퓨터가 보는 이미지
컴퓨터는 이미지를 픽셀값이 담긴 2차원 행렬로 본다. 700 x 700 크기의 회색조 이미지는 (700, 700) 크기의 행렬이 된다.

## 1.4.3 컬러 이미지
표준 RGB를 색상 체계를 사용하는 컬러 이미지는 빨간색, 초록색, 파란색의 강도를 나타내는 3차원 행렬이다. (700, 700, 3) 크기의 행렬이 되는 것.

# 1.5 이미지 전처리
최초 수집된 데이터는 보통 노이즈가 많고 출처가 다양한 만큼 데이터 클리닝 및 표준화 과정을 거쳐야 함. 전처리를 통해 모델의 정확도를 개선하고 불필요한 복잡도를 제거 가능하다. 
## 1.5.1 컬러 이미지를 회색조 이미지로 변경하기
이미지에서 대상을 인식하는 경우는 회색으로도 충분하다. 컬러 이미지는 메모리 용량을 더 차지하고 계산 복잡도도 증가함.   

의료분야나 자율주행의 차선 감지는 색의 강도에 크게 의지 하는 만큼 색이 중요하다. 이미지의 색이 중요한지 판별하는 방법은 육안으로 이미지를 확인해서 대상이 되는 사물을 확인가능한지 보는 것. 회색조에서 판별이 안되면 색상 정보를 같이 입력받아야 한다. 

# 1.6 특징 추출
머신러닝에서의 특징(feature)란 관찰된 현상에서의 측정할 수 있는 속성이나 특성을 말한다. 컴퓨터 비전에서의 특징이란 이미지에서 특정 대상에만 해당되는 특정 가능한 데이터이다. 선, 모서리, 이미지 조각이나 다른 것과 구분되는 색상 역시 특징이 될 수 있음. 좋은 특징이란 대상을 다른 대상과 쉽게 구분 짓게 해주는 속성이다. 머신러닝 모델은 원데이터(이미지)를 변환해 얻은 특징 벡터를 입력받아 대상의 특성을 학습한다. 

이미지를 특징 추출 알고리즘에 입력하면 여러 특징 값이 담긴 벡터를 출력함. 모델의 성능은 특징의 의해 결정된다. 좋은 특징은 다른 것과 구별되며, 추적과 비교과 쉽다. 배울, 밝기, 각도가 달라도 일관적이며 노이즈가 많아서 관찰 가능하다.  

## 1.6.3 특징 추출하기 (자동 추출과 수동 수출)
기존 머신러닝에서는 수동으로 특징을 선택하여 서포트 벡터 머신 SVM, 또는 에이다부스 AdaBoost와 같은 분류기에 입력해서 예측 결과를 얻었다. 사람이 수동으로 선택한 특징들을 다음과 같음.
- 기울기 방향성 히스토그램 Histogram of oritented gradients, HOG
- 하르 캐스케이드 Haar Cascades
- 크기 불변 특징 변환 Scale-invarient feature transform, SIFT
- 고속 강인한 특징 추출 speeded-up robust featuer, SURF

딥러닝은 신경망이 특징을 자동으로 추출하고 뉴런간에 연결에 부여된 가중치를 통해 출력에 미치는 각 특징의 중요도를 학습함. 특징 추출기와 분류기를 합친 것으로 둘 다 학습가능하다. 신경망은 가능한 한 모든 특징을 만들고 무작위의 가중치를 부여한다. 이를 학습을 통해 자주 나타나는 패턴을 높은 가중치를 부여하는 방향으로 흘러간다.  

특징을 사용하는 이유는 이미지에서 분류와 무관한 정보가 너무 많기 때문이다. 전처리 후 중요한 정보만 남겨 단순화시키고 불필요한 정보는 빼야 한다. 

# 1.7 분류 학습 알고리즘
신경망의 각 층은 특징을 추출한다. 첫 번째 층은 이미지의 패턴을 학습하고, 그 다음 층은 첫 번째 층의 패턴의 패턴을 학습하면서 특징 벡터를 만든다. 마지막 층에서 분류를 담당하여 이미지에 따라 노드가 발화된다.
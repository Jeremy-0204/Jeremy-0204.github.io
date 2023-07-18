---
layout: post
title: Supervised Machine Learning Regression and Classification - 1
description: >
  Howdy! This is the lecture note for lecture "Supervised Machine Learning: Regression and Classification" week 1
#sitemap: false
hide_last_modified: true
categories: [Machine Learning]
---

Coursera 플러스를 결제하고 앤드류 응 교수님의 Machine Learning 특화과정을 수강하기 시작했다.  

머신러닝 특화과정 말고도 딥러닝 특화과정이나 수학과정등 여러 강의들이 많길래 굳이 여러군데에서 복잡하게 강의를 챙겨듣기 보다는 한 곳에서 확실하게 개념을 잡자는 생각에 코세라 플러스를 결제하고 수강신청을 했다.  

본 강의노트들은 머신러닝 특화과정 중에서도 첫번째 강의인 Supervised Machined Learning의 week 1 내용을 들으면서 간략하게 중요한 내용 요약 및 이해가 잘 안되는 부분을 정리하기 위함이다.  

한 번 시작해볼까?  

# 1. Overview of Machine Learning
## Welcome to Machine Learning!

머신러닝은 정말 다양한 분야에서 사용되고 있음을 간략하게 설명하셨음.  

결국 핵심은 컴퓨터로 하여금 분명하게 (Explicitly) 학습하게 하는 것이다.  

## Applications of Machine Learning

왜 이렇게 다양하게 사용되는가?  

머신러닝은 인공지능의 한 분야로 기계가 스스로 학습하는 것을 의미함.  인간이 직접 프로그래밍을 해주는 것보다 더 explicit한 문제들을 해결 가능하기에 다양한 분야에서 적용이 가능해진 것이다.  

강의 중에 사람 수준의 사고방식을 가진 인공지능을 뜻하는 AGI (Artificial General Intelligence)를 언급하셨는데, 비록 먼이야기 같지만 이를 구현할 수 있는 최선의 방법이 Learning Algorithm을 사용하는 것이라 한다.  

학습 알고리즘이란 모델의 가중치를 학습하는 것으로 손실 함수와 최적화 기법으로 구성된다.  

https://docs.aws.amazon.com/ko_kr/machine-learning/latest/dg/learning-algorithm.html

# 2. Supervised vs. Unsupervised Machine Learning
## What is machine learning?
explicitly programmed 되지 않고도 학습할 수 있는 능력을 컴퓨터에게 제공하는 것. 

많이 배울수록 성능은 올라간다. 이렇게 학습하는 machine learning algorithm은 대표적인 2종류가 존재한다.

Supervised Learning (지도 학습)
실생활 문제에서 가장 많이 사용됨.

Unsupervised Learning (비지도 학습)
Recommender systems, Reinforcement learning 등.

## Supervised Learning
input to output 매핑을 학습하는 알고리즘이다. input x에 대한 정답 레이블 y로 학습시킨다. 

평수에 따른 집 가격을 예측해야 할때 정답에 얼마나 가까운 선을 그리느냐가 머신 러닝 모델이 학습할 내용이다.  

Regression은 무한대의 가능한 숫자들 중 한가지 숫자를 선택하는 것이다. 

Classification은 특정 카테고리나 클래스를 예측하는 것이다. 회귀와는 다르게 한정된 갯수중에서의 예측이라는 것. input은 여러개가 될 수도 있다. 

## Unsupervised Learning
주어진 데이터셋에서 특정한 패턴을 찾아내는 것이다. 대표적인 예로 CLustering Algorithm이 존재함. 구글 뉴스에서 비슷한 뉴스끼리 묶는것.   

지도학습은 입력값 x와 출력값 y로 구성되나, 비지도학습은 입력값 x로만 들어옴. 알고리즘은 특정 패턴이나 구조를 찾아야 함.  

Clustering - 비슷한 데이터 포인트끼리 그룹화시킴  
Anamoly Detection - Unusual Event를 찾아내는 것  
Dimensionality Reduction - 대량의 데이터셋을 정보의 손실을 최소화시켜 압축시킴  

# 3. Regression Model
## Linear Regression model
집 평수에 따른 가격을 예측하는 모델을 생각해보자. 우리는 평수에 따른 가격 데이터를 가지고 직선을 추출할 수 있다. 해당 직선에 데이터를 입력시켜 대응되는 출력값을 출력한다. 이때 구하고자 하는 값이 큰 정수거나 음수같은 수가 나오면 해당 문제는 회귀(regression) 문제라고 할 수 있다. 왜
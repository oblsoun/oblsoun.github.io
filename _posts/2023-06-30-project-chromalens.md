---
title: "Chroma Lens"
date: 2023-06-30
categories: [Project]
comments: true
sitemap :
  changefreq : daily
  priority : 1.0
---

색약자를 위한 이미지 색채 감지 프로젝트

개발 언어: Python

Dataset: [Roboflow](https://universe.roboflow.com/msa-ciwxj/yoon-2)

Model: Yolov8m

Framework: Django

IDE: Google COLAB, Pycharm

[시연 영상](https://youtu.be/LGonUX21H74)

[Github Link](https://github.com/oblsoun/chromalens)

- - -

✔️ **개발 배경**

- 색약자들이 일상생활 속에서 불분명한 색채 인식으로 인해 겪을 수 있는 불편함 해소

- - -

✔️ **개발 필요성**

- 색상을 추출하는 인공지능 서비스는 많지만 색 공간을 명시하고, 라벨링하는 서비스는 미흡

- 자율주행기술이 대두되면서 색을 감지하고 경계선을 인식하는 인공지능 개발 필요성 등장

- - -

✔️ **프로그램 특장점**

- 간편한 이미지 업로드

- 즉각적인 이미지 분석

- 색상 분류 및 색 공간 형태 명시

- 실시간 처리 가능

- - -

✔️ **개발 과정**

![개발 과정](https://user-images.githubusercontent.com/113246634/273899408-91c2d309-ed02-471d-85d5-c2fe122c4324.jpg)

- - -

✔️ **사용 과정**

![사용 과정](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/273899491-eec13495-c49b-427a-93c3-e2f23f32d157.jpg)

- - -

✔️ **모델 구현**

1. 데이터셋 구축

> - [Roboflow 링크](https://universe.roboflow.com/msa-ciwxj/yoon-2)
> 
> - 6개 클래스(brown, green, orange, purple, red, yellow)에 해당하는 색 이미지를 수집
> 
> - Poligon Tool로 라벨링 작업
> 
> - 신뢰도, 정확도를 낮추거나 과적합을 일으키는 데이터셋 필터링

2. 모델 설계

> - [Colab 링크](https://colab.research.google.com/drive/12toM9X_22CyYPObbtlJzoKYNFA7JG5yb?usp=sharing)
>
> - Confusion Matrix(혼동행렬)
>
> ![confusion_matrix_normalized](https://user-images.githubusercontent.com/113246634/273897986-bd9d81f8-0b73-4a59-8426-ae3c54b3cd06.png)

- - -

✔️ **기대효과 및 활용분야**

- 색 인식에 보다 원활한 시각적 의사소통을 보편적으로 가능하게 함

- 기계장치, 자율주행 차량 등이 중앙선, 신호등, 경고등 등을 인식
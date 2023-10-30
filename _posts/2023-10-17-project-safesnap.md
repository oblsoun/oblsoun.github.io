---
title: "안전네컷"
date: 2023-10-17
categories: [Project]
comments: true
sitemap :
  changefreq : daily
  priority : 1.0
---

[VOV 프로젝트](https://oblsoun.github.io/2023-10/project-vov) '실시간' 기능을 활용한 사진 촬영 프로젝트(포토부스)

개발 언어: Python

Dataset: [Roboflow](https://universe.roboflow.com/fingerprint-nze3i/vov-k9idv)

Model: Yolov5m

Framework: Django

IDE: Visual Studio Code

[Github Link](https://github.com/oblsoun/VOVsnap)

- - -

✔️ **프로젝트 목적**

- 기획 의도

> - AI 기반의 생채 정보 보안을 위한 지문 비식별화
>
> - 개인정보 데이터 관리의 중요성 인식 확산

- 프로젝트 내용

> - 지문 영역 인지 및 지문 식별 정보 추출
>
> - 추출된 지문 비식별화
>
> - 후처리된 파일 이메일 전송

- - -

✔️ **프로젝트 특장점**

- Mediapipe 라이브러리 및 YOLOv5 모델로 높은 정확도와 빠른 속도로 지문 추출

- - -

✔️ **주요 기술**

- Mediapipe 라이브러리를 사용하여 손 끝 위치를 감지

- [Custom YOLOv5m](https://colab.research.google.com/drive/1dKO153AU2HZRUqF23diTxx2qycikQkzL?usp=sharing) 모델을 사용하여 지문 식별(mAP50 0.903)

- - -

✔️ **기타 링크**

[Custom Dataset - Roboflow](https://universe.roboflow.com/fingerprint-nze3i/vov-k9idv)

[활용 예시](https://github.com/oblsoun/safesnap)
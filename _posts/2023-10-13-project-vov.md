---
title: "VOV"
date: 2023-10-13
categories: [Project]
comments: true
sitemap :
  changefreq : daily
  priority : 1.0
---

개인정보 비식별화 지원 서비스 개발 프로젝트

개발 언어: Python

Dataset: [Roboflow](https://universe.roboflow.com/fingerprint-nze3i/vov-k9idv)

Model: Yolov5m

Framework: Django

DB: AWS RDS(mariaDB)

IDE: Visual Studio Code

ETC: UML, SonarQube, EC2, S3

[Github Link](https://github.com/oblsoun/VOV)

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
> - 후처리된 파일 저장 및 전송

- - -

✔️ **프로젝트 특장점**

- Mediapipe 라이브러리 및 YOLOv5m 모델로 높은 정확도와 빠른 속도로 지문 추출

- 기존 지문 인식 시스템의 부족한 보호 기능 보완

- 보안을 위해 후처리된 이미지만 데이터베이스에 저장

- 안정적인 AWS 인프라 및 다양한 산업 분야에서 활용 가능

- 사용자 친화적 환경으로 업로드 및 결과 처리 용이

- - -

✔️ **주요 기술**

- Mediapipe 라이브러리를 사용하여 손 끝 위치를 감지

- [Custom YOLOv5m](https://colab.research.google.com/drive/1dKO153AU2HZRUqF23diTxx2qycikQkzL?usp=sharing) 모델을 사용하여 지문 식별(mAP50 0.903)

- AWS 인프라를 활용한 무중단 배포와 S3, RDS를 이용한 데이터 저장 및 클라우드 서비스 제공

- - -

✔️ **기술 스택**

- 서비스 구성도

![서비스 구성도](https://ifh.cc/g/KSLTG7.png)

- 메뉴 구성도

![메뉴 구성도](https://ifh.cc/g/p6jAbb.png)

- Usecase
  
![Usecase](https://ifh.cc/g/CO21JA.png)

- 알고리즘 명세서

![알고리즘 명세서](https://ifh.cc/g/D0KyKQ.jpg)

- - -

✔️ **테이블 설계**

![ERD](https://ifh.cc/g/CT7lMw.png)

- - -

✔️ **기타 링크**

[활용 예시](https://github.com/oblsoun/safesnap)
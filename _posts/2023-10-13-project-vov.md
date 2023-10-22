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

![서비스 구성도](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/273834515-7b7d23ec-a8d5-4e17-a5bc-f3f92b2e4a4b.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231022%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231022T124426Z&X-Amz-Expires=300&X-Amz-Signature=1101271355e2252841d170c69481b809ac105554b37452a6ed9464d53462a7aa&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)

- 메뉴 구성도

![메뉴 구성도](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/273842113-5e3f6af1-139f-4dc1-9fc1-dbf974e86096.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231022%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231022T124442Z&X-Amz-Expires=300&X-Amz-Signature=69ed8b8fe6cb63b232508bea2675d123a5821189d486853bcdcfb60605c67645&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)

- Usecase
  
![Usecase](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/273840913-677f3b93-11d4-4f00-8d6d-4c956a6b2802.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231022%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231022T124453Z&X-Amz-Expires=300&X-Amz-Signature=d19e9d1046fc7192eee359c3fa414257f471db50496a838800e174e36b7d288e&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)

- 알고리즘 명세서

![알고리즘 명세서](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/273845168-ff895aaf-1013-4a5a-99fd-af69649b7b24.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231022%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231022T124520Z&X-Amz-Expires=300&X-Amz-Signature=0351d9b54c096388ecd189b9e479265d7dc5b5b48747139ebb59bf24079957c5&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)

- - -

✔️ **테이블 설계**

![ERD](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/273836532-76dbc7e8-90e0-423d-9150-eeefe63b2fde.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231022%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231022T124540Z&X-Amz-Expires=300&X-Amz-Signature=ac5ba479eef9617f7be8d8ba5715a83ec00a0dfb4a104e405fb565f3912e7942&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)

- - -

✔️ **기타 링크**

[활용 예시](https://github.com/oblsoun/safesnap)
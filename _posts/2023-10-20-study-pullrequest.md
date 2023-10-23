---
title: "Github Pull Request 사용 방법"
date: 2023-10-20
categories: [Study]
comments: true
sitemap :
  changefreq : daily
  priority : 1.0
---

#### 개요

- [개요](#개요)
- [용어 설명](#용어-설명)
- [목적](#목적)
- [설정](#설정)
- [사용 방법](#사용-방법)

- - - 

#### 용어 설명

**Pull Request**: Repository에 대한 제안된 변경 사항

**Repository**: 프로젝트 파일, 각 파일의 수정 기록(Issue), 프로젝트의 작업을 논의하고 관리할 수 있는 공간

**branch**: Repository에 적용하는 변경 사항과 별도로 기능 개발, 버그 수정을 안전하게 작업할 수 있는 작업 영역

**push**: branch에서 만든 commit을 repository에 적용

**commit**: 변경 사항 기록

**merge**: 기본 branch에 변경 사항을 병합

---

#### 목적

- Github Repository의 개인 branch에 push한 변경 사항을 다른 사람에게 알림
- 공동 작업자와 변경 사항을 논의 및 검토
- 변경 사항을 기본 branch에 merge

- - -

#### 설정

branch 보호 설정

> **1. [Settings] > [Branches] > [Add branch protection rule]**
> 
> ![1](https://ifh.cc/g/gD740g.png)
> 
> **2. Branch name pattern 설정, Protect matching branches 내 Require a pull request before merging 체크박스 선택**
> 
> ![2](https://ifh.cc/g/6w7vDp.png)
> 
> **3. 승인 인원 설정**
> 
> ![3](https://ifh.cc/g/x0JFxb.png)
>
> **4. create 버튼 클릭**
>
> ![4](https://ifh.cc/g/fWz421.png)

- - -

#### 사용 방법

> **1. Git Push**
> 
> **2. Branches 확인**
> 
> ![5](https://ifh.cc/g/tbYdJP.png)
>
> **3. Compare & pull request 버튼 클릭**
> 
> ![6](https://ifh.cc/g/rB3WRt.png)
> 
> **4. merge할 브랜치 확인**
> 
> ![7](https://ifh.cc/g/4mH2WW.png)
> 
> **5. 필요 내용 입력 후 Create pull request 클릭**
> 
> 필요 내용: 제목, 설명, Reviewers, Assignees, Labels, Projects, Milestone
> 
> ![8](https://ifh.cc/g/F3oOm3.png)
> 
> **6. Merge pull request 클릭**
> 
> ![9](https://ifh.cc/g/YLZ4SP.png)
>
> **6-1. Merge pull request가 비활성화일 때**
> 
> [해결 방법](https://docs.github.com/ko/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-on-github)
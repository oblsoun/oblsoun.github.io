---
title: "3D Contribution 적용법"
date: 2023-10-28
categories: [Study]
comments: true
sitemap :
  changefreq : daily
  priority : 1.0
---

#### 개요

- [개요](#개요)
- [사용 계기](#사용-계기)
- [목적](#목적)
- [사용 방법](#사용-방법)
- [느낀점](#느낀점)

- - -

#### 사용 계기

Github 프로필을 작성하는 도중 여러 Github 사용자들의 README.md 파일을 구경하게 되었다. 

이때 시각적으로 Contribution을 확인할 수 있는 프로필을 보고 나도 하고 싶다는 생각에 3D Contribution을 찾아보게 되었다.

- - -

#### 목적

Github 프로필에 시각적으로 Contribution을 보여주기 위함

- - -

#### 사용 방법

**1. Repository 생성**

Repository name = Owner

(참고) 이미 존재하는 Repository이기 때문에 경고 표시가 뜸

![Repository 생성](https://ifh.cc/g/nq0nLX.png)

**2. Token 생성**

Settings > Developer Settings

Personal access tokens > Tokens(classic)

Generate new token > Generate new token(classic)

![Token 생성](https://ifh.cc/g/OCfzOV.png)

**3. Settings 설정**

본인 Repository 내 Settings

Security > Secrets and variables > Action

![Action](https://ifh.cc/g/nCS3TL.png)

New repository secret 클릭

![New repository secret](https://ifh.cc/g/r9CYbd.png)

Name: Token

Secret: Token 복사/붙여넣기

![Action Token](https://ifh.cc/g/F1ZbfL.png)

Add secret 클릭


**4. Action 설정**

Action 클릭

![Action](https://ifh.cc/g/2Fh4xn.png)

New workflow 클릭

![New workflow](https://ifh.cc/g/vh2kpg.png)

set up a workflow yourself 클릭

![set up a workflow yourself](https://ifh.cc/g/pa09F8.png)

파일 이름: main.yml > profile-3d.yml 변경

아래 내용 복사/붙여넣기

**깃허브이름**, **깃허브이메일** 이라고 작성된 부분은 각자 Github name, email로 수정

```
name: GitHub-Profile-3D-Contrib

on:
  schedule: # 03:00 JST == 18:00 UTC
    - cron: "0 18 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate-github-profile-3d-contrib
    steps:
      - uses: actions/checkout@v2
      - uses: yoshi389111/github-profile-3d-contrib@0.6.0
        env:
          GITHUB_TOKEN: ${{ secrets.TOKEN }}
          USERNAME: ${{ github.repository_owner }}
      - name: Commit & Push
        run: |
          git config user.name 깃허브이름
          git config user.email 깃허브이메일
          git add -A .
          git commit -m "generated"
          git push
```

Run workflow > Run workflow

![Run workflow](https://ifh.cc/g/RWaWFF.png)

**5. README 파일에 추가**

아래 코드 복사/붙여넣기(적용한 테마: south-season-animate)

```
![](./profile-3d-contrib/profile-south-season-animate.svg)
```

원하는 테마 적용

샘플 [https://github.com/yoshi389111/github-profile-3d-contrib.git](https://github.com/yoshi389111/github-profile-3d-contrib)

```
profile-3d-contrib/profile-green-animate.svg
profile-3d-contrib/profile-green.svg
profile-3d-contrib/profile-season-animate.svg
profile-3d-contrib/profile-season.svg
profile-3d-contrib/profile-south-season-animate.svg
profile-3d-contrib/profile-south-season.svg
profile-3d-contrib/profile-night-view.svg
profile-3d-contrib/profile-night-green.svg
profile-3d-contrib/profile-night-rainbow.svg
profile-3d-contrib/profile-gitblock.svg
```

- - -

#### 느낀점


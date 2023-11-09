---
title: "Groovy 사용을 가능하게 하는 플러그인"
date: 2023-11-09
categories: [Study]
comments: true
sitemap :
  changefreq : daily
  priority : 1.0
---

#### 개요
- [개요](#개요)
- [구성 파일 제공자 플러그인](#구성-파일-제공자-플러그인)
- [글로벌 포스트 스크립트 플러그인](#글로벌-포스트-스크립트-플러그인)
- [Groovy 플러그인](#groovy-플러그인)
- [Groovy Postbuild 플러그인](#groovy-postbuild-플러그인)
- [Groovy Remote Control 플러그인](#groovy-remote-control-플러그인)
- [Matrix Groovy Execution Strategy 플러그인](#matrix-groovy-execution-strategy-플러그인)
- [Scriptler 플러그인](#scriptler-플러그인)


#### [구성 파일 제공자 플러그인](https://plugins.jenkins.io/config-file-provider)

- Jenkins UI를 통해 로드된 구성파일(ex. Maven, XML, Groovy, 사용자 정의 파일 등에 대한 settings.xml)을 제공하는 기능 추가
- 이 파일은 작업의 작업공간에 복사

#### [글로벌 포스트 스크립트 플러그인](https://plugins.jenkins.io/global-post-script/)

- Jenkins가 관리하는 각 작업을 빌드 후에 글로벌로 구성된 Groovy Script 실행
- 동일한 Jenkins가 관리하는 다운스트림 작업을 트리거하거나 매개변수화된 작업에 전달된 매개변수를 기반으로 하는 원격 작업을 트리거하는 등 공유 매개변수 세트를 기반으로 작업을 수행해야 하는 경우

#### [Groovy 플러그인](https://plugins.jenkins.io/groovy/)

#### [Groovy Postbuild 플러그인](https://plugins.jenkins.io/groovy-postbuild)

- Jenkins JVM에서 Groovy Script 실행
- 일부 조건 확인 후 빌드 결과 변경, 빌드 기록에서 빌드 옆에 배지를 표시하거나 빌드 요약 페이지에 정보 표시

#### [Groovy Remote Control 플러그인](https://plugins.jenkins.io/groovy-remote)

- [Groovy Remote Control](http://groovy.codehaus.org/modules/remote/) 수신기를 제공하고 Jenkins에서 외부 애플리케이션 제어 가능하게 해

#### [Matrix Groovy Execution Strategy 플러그인](https://plugins.jenkins.io/matrix-groovy-execution-strategy)

- 매트릭스 프로젝트의 실행 순서와 유효한 조합을 결정

#### [Scriptler 플러그인](https://plugins.jenkins.io/scriptler)

- Scriptler 사용 시 Groovy Script를 저장/편집하고 모든 노드에서 실행 가능
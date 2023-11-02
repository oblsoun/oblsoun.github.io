---
title: "Jenkins Pipeline"
date: 2023-11-03
categories: [Study]
comments: true
sitemap :
  changefreq : daily
  priority : 1.0
---

#### 개요

- [개요](#개요)
- [정의](#정의)
- [역할](#역할)
- [목적](#목적)
- [Pipeline 생성 방법](#pipeline-생성-방법)
- [Jenkins File 작성 방법](#jenkins-file-작성-방법)
- [Scripted Pipeline](#scripted-pipeline)
- [Pipeline 생성 방법](#pipeline-생성-방법-1)

- - -

#### 정의
젠킨스의 플러그인

#### 역할
- 연속적인 이벤트
- Job의 그룹 실행

#### 목적
- 단순한 Job들이 많아지는 경우 Job을 관리하기 어려움
- Pipeline으로 작성 시 하나의 Job으로 묶으면 관리하기 편함
- 진행 상황, 직관적인 파악 가능

#### Pipeline 생성 방법
- WEB UI를 통해 Job 구성에서 Script 코드 작성
- SCM을 이용해 Jenkinsfile에 DSL(Domain-Specific Language)로 작성된 스크립트 코드 작성 필요
- Blueocean 플러그인으로 UI를 통해 스크립트 코드 작성

#### Jenkins File 작성 방법
- Groovy Script로 작성
- Declarative Pipeline
> Scripted Pipeline보다 쉽게 작성 가능
>
> Groovy 문법 기반
> 
> 최상단에 pipeline이라고 되어 있으면 declarative 문법으로 작성된 것

- Scripted Pipeline
> Declarative보다 효과적이고 많은 기능 포함 작성 가능
> 
> Groovy 문법 기반
> 
> 최상단에 node 지시어가 있으면 scripted 문법으로 작성된 것

- Declarative Pipeline와 Scripted Pipeline 동시 작성 불가

#### Scripted Pipeline
- **Directive(지시어)**
> - node: Scripted Pipeline을 실행하는 Jenkins 에이전트 / 최상단에 선언
> - dir: 명령어를 수행할 directory(폴더) 정의
> - stage: 파이프라인 각 단계, 어떤 작업을 할지 선언(작업 내용 작성)
> - git: git 원격 저장소에서 프로젝트 clone
> - sh: unix 환경에서 실행할 명령어 실행(윈도우: bat)
> - def: groovy 변수, 함수 선언(javascript에서 var)

- **작성 방법**

```
node('worker'){
  stage('source'){
    // stage에서 수행할 코드 작성
  }
}
```

```
// 예시 1
pipeline {
  agent any

  stages() {
    stage('git clone'){
      steps() {
        git 'https://github.com/git아이디/git레포지토리.git'
      }
    }

    stage('Test') {
      steps{
        echo 'Testing..'
      }
    }

    stage('execute sh') {
      steps {
        sh 'chmod 774 ./파일이름"
        sh './파일이름"
      }
    }
  }
}
```

```
// 예시 2
node {
    stage('git clone') {
        git 'https://github.com/git아이디/git레포지토리.git'
    }
    stage('Test') {
        echo 'Testing....'
    }
    stage('execute sh') {
		sh "chmod 774 ./파일이름"
        sh "./파일이"
    }
}
```

- **Flow Control**

```
// if문 사용 가능

node {
    stage('Example') {
        if (env.BRANCH_NAME == '메인브랜치') {
            echo '메인 브랜치'
        } else {
            echo '다른 브랜치'
        }
    }
}
```

```
// 예외 처리 가능

node {
    stage('Example') {
        try {
            sh 'exit 1'
        }
        catch (exc) {
            echo 'error'
            throw
        }
    }
}
```

#### Pipeline 생성 방법
- **Web UI에서 Jenkinsfile 작성**
> - Jenkins 대시보드에서 새로운 Item 선택 > Pipeline 선택
> - 설명 작성 후 Pipeline 탭 선택 > Definition에서 Pipeline script 선택 > 스크립트 작성 후 저장
> - Build Now 클릭

- **SCM을 이용해 Jenkinsfile 작성**
> - 테스트할 Repository에 Jenkinsfile 생성 후 샘플 코드 작성
> - Jenkins 대시코드에서 새로운 Item 선택 > 아이템 이름 작성 후 Pipeline 선택
> - Definition에서 Pipeline script from SCM 선택 > SCM 항목에서 Git 선택 > 원격 저장소 작성 > Credentials에서 계정 선택 > Branches to build에서 메인 branch 작성 > Script Path에서 Jenkinsfile 위치 작성(최상단일 경우 Default)
> - Build Triggers 항목에서 Github hook trigger for GITScm Polling 체크(메인 브랜치에 Push 했을 때 Build 됨)
> - Build Now 클릭(최초 1회 빌드됨)
> - 아무 파일 생성, 수정 후 원격 저장소의 메인 branch에 push, build 확인
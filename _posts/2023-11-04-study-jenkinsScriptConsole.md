---
title: "Jenkins Script Console"
date: 2023-11-04
categories: [Study]
comments: true
sitemap :
  changefreq : daily
  priority : 1.0
---

#### 개요
- [개요](#개요)
- [Jenkins Script Console](#Jenkins-Script-Console)
- [다중 컨텍스트](#다중-컨텍스트)
  - [컨트롤러에서 스크립트 콘솔 실행](#컨트롤러에서-스크립트-콘솔-실행)
  - [에이전트에서 스크립트 콘솔 실행](#에이전트에서-스크립트-콘솔-실행)
  - [에이전트의 컨트롤러 스크립트 콘솔에서 스크립트 실행](#에이전트의-컨트롤러-스크립트-콘솔에서-스크립트-실행)
  - [파일 읽기 및 쓰기](#파일-읽기-및-쓰기)
- [원격 액세스](#원격-액세스)
- [제출할 스크립트 콘솔의 단축키](#제출할-스크립트-콘솔의-단축키)
- [비디오 튜토리얼 및 추가 학습 자료](#비디오-튜토리얼-및-추가-학습-자료)
  

#### Jenkins Script Console
- 액세스는 권한에 따라 제어됨(Administer)
- Jenkins 런타임에 대한 웹 기반 Groovy Shell
- Groovy: 자바가 할 수 있는 거의 모든 작업을 수행할 수 있는 기능을 제공하는 언어
> - Jenkins 컨트롤러 및 에이전트에서 하위 프로세스를 생성, 임의 명령 실행
> - Jenkins 컨트롤러가 호스트에서 액세스할 수 있는 파일(ex. /etc/passwd:) 읽기 가능
> - Jenkins 내 구성된 자격 증명 해독
- Jenkins 인프라의 모든 부분에 영향을 주지 않도록 스크립트 콘솔을 실행할 수 있는 사용자(또는 관리자)를 중지하는 관리 제어 기능을 제공하지 않음
> - 일반 Jenkins 사용자에게 스크립트 콘솔 액세스 권한을 부여하는 것은 기본적으로 Jenkins 내에서 관리자 권한을 부여하는 것과 동일
- Jenkins 설정 구성 가능
> - 보안을 비활성화, 보안 재구성, Jenkins 프로세스 외부에서 호스트 운영 체제의 백도어 열기 가능
> - 많은 조직이 인프라에서 Jenkins를 중요하게 생각하기 때문에 공격자가 노력하지 않아도 인프라 내에서 수평으로 이동 가능하기 때문에 중요함
- 원래 Jenkins 개발자를 위한 디버깅 인터페이스로 의도되었지만 이후 Jenkins 관리자가 Jenkins를 구성하고 Jenkins 런타임 문제를 디버깅하는 데 사용하는 인터페이스로 성장했기 때문에 매우 강력
- Jenkins Script Console이 제공하는 기능으로 인해 Jenkins와 해당 에이전트는 root 사용자(Linux) 또는 다른 OS의 시스템 관리자로 실행되어서는 안 됨

#### 다중 컨텍스트
- Jenkins Script Console은 컨트롤러나 구성된 에이전트에서 실행 가능

##### 컨트롤러에서 스크립트 콘솔 실행
- Jenkins 관리 > 스크립트 콘솔 접근 가능
- /script 또는 Jenkins 인스턴스의 하위 URL 방문

##### 에이전트에서 스크립트 콘솔 실행
- Jenkins 관리 > 노드 관리 방문
- 상태 페이지를 보려면 노드 선택
- 왼쪽 메뉴에는 해당 특정 에이전트의 "스크립트 콘솔"을 열 수 있는 메뉴 항목 존재

##### 에이전트의 컨트롤러 스크립트 콘솔에서 스크립트 실행
- 개별 에이전트의 컨트롤러 스크립트 콘솔에서 스크립트 실행 가능
- 마스터 스크립트 콘솔의 에이전트에서 스크립트 실행

```
// 예시

import hudson.util.RemotingDiagnostics
import jenkins.model.Jenkins

String agentName = 'your agent name'
//groovy script you want executed on an agent
groovy_script = '''
println System.getenv("PATH")
println "uname -a".execute().text
'''.trim()

String result
Jenkins.instance.slaves.find { agent ->
    agent.name == agentName
}.with { agent ->
    result = RemotingDiagnostics.executeGroovy(groovy_script, agent.channel)
}
println result
```

##### 파일 읽기 및 쓰기
- 컨트롤러 스크립트 콘솔을 통해 컨트롤러나 에이전트에서 직접 파일을 읽고 쓰기 가능
- Jenkins 컨트롤러에 파일 쓰기

```
new File('/tmp/file.txt').withWriter('UTF-8') { writer ->
    try {
        writer << 'hello world\n'
    } finally {
        writer.close()
    }
}
```

- Jenkins 컨트롤러에서 파일 읽기

```
new File('/tmp/file.txt').text
```

- 에이전트 채널을 통해 에이전트에 파일 쓰기

```
import hudson.FilePath
import hudson.remoting.Channel
import jenkins.model.Jenkins

String agentName = 'some-agent'
String filePath = '/tmp/file.txt'

Channel agentChannel = Jenkins.instance.slaves.find { agent ->
    agent.name == agentName
}.channel

new FilePath(agentChannel, filePath).write().with { os ->
    try {
        os << 'hello world\n'
    } finally {
        os.close()
    }
}
```

- 에이전트 채널을 통해 에이전트에서 파일 읽기

```
import hudson.FilePath
import hudson.remoting.Channel
import jenkins.model.Jenkins

import java.io.BufferedReader
import java.io.InputStreamReader
import java.nio.charset.StandardCharsets
import java.util.stream.Collectors

String agentName = 'some-agent'
String filePath = '/tmp/file.txt'

Channel agentChannel = Jenkins.instance.slaves.find { agent ->
    agent.name == agentName
}.channel

String fileContents = ''
new FilePath(agentChannel, filePath).read().with { is ->
    try {
        fileContents = new BufferedReader(
            new InputStreamReader(is, StandardCharsets.UTF_8))
                .lines()
                .collect(Collectors.joining("\n"))
    } finally {
        is.close()
    }
}

// print contents of the file from the agent
println '==='
println(fileContents)
println '==='
```

#### 원격 액세스
Jenkins 관리자는 HTTP POST 요청을 /script/url 또는 /scriptText/.

- Bash를 통한 curl 예제

```
curl -d "script=<your_script_here>" https://jenkins/script
# or to get output as a plain text result (no HTML)
curl -d "script=<your_script_here>" https://jenkins/scriptText
```

- bash를 통해 Groovy 파일을 제출하는 Curl

```
curl --data-urlencode "script=$(< ./somescript.groovy)" https://jenkins/scriptText
```

- bash를 통해 사용자 이름과 API 토큰을 제공하는 Groovy 파일을 제출하는 Curl

```
curl --user 'username:api-token' --data-urlencode \
  "script=$(< ./somescript.groovy)" https://jenkins/scriptText
```

- 사용자 이름과 API 토큰을 제공하는 그루비 파일을 제출하는 Python

```
with open('somescript.groovy', 'r') as fd:
    data = fd.read()
r = requests.post('https://jenkins/scriptText', auth=('username', 'api-token'), data={'script': data})
```

#### 제출할 스크립트 콘솔의 단축키
- 윈도우/리눅스: Ctrl + Enter
- 맥: Command + Enter

#### 비디오 튜토리얼 및 추가 학습 자료
- Jenkins Script Console 녹화 영상
> - [Jenkins World 2017: Jenkins Script Console 마스터하기](https://youtu.be/qaUPESDcsGg?feature=shared) - 44분 - 샘플 사용 및 보안 토론
> - [LA Jenkins Area Meetup 2016 - Jenkins 내부 해킹 - Jenkins 스크립트 콘솔]([https://www.youtube.com/watch?v=T1x2kCGRY1w](https://youtu.be/T1x2kCGRY1w?feature=shared)https://youtu.be/T1x2kCGRY1w?feature=shared) - 39분 - 샘플 사용
- Script Console에서 스크립트 작성 능력 확장
> - [Groovy 배우기](https://groovy-lang.org/learn.html) / [Groovy Pipeline 및 공유 Pipeline Library](https://www.jenkins.io/doc/book/pipeline/) / [Groovy 플러그인](https://plugins.jenkins.io/groovy/) / [Job DSL 플러그인](https://plugins.jenkins.io/job-dsl/)
> - [코드 완성 기능을 갖춘 Jenkins용 Groovy Script 작성](https://www.mdoninger.de/2011/11/07/write-groovy-scripts-for-jenkins-with-code-completion.html)
> > - IDE 내에서 Maven 프로젝트 생성
> > - org.jenkins-ci.main:jenkins-core(및 현재 예상되는 기타 플러그인)에 의존
> > - Jenkins API 개체 및 메서드의 코드 완성 기능을 사용하여 Groovy Script 작성 가능

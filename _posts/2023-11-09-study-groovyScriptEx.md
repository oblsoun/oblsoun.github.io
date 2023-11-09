---
title: "Groovy Script 예시"
date: 2023-11-09
categories: [Study]
comments: true
sitemap :
  changefreq : daily
  priority : 1.0
---

#### 개요
- [개요](#개요)
- [오래된 스크립트](#오래된-스크립트)
  - [Jenkins의 로컬 복사본 시작](#jenkins의-로컬-복사본-시작)
- [Scriptler 플러그인 Groovy Script](#scriptler-플러그인-groovy-script)
  - [Jenkins 서버의 모든 작업에 대해 Chuck Norris 플러그인 활성화](#--jenkins-서버의-모든-작업에-대해-chuck-norris-플러그인-활성화)
  - [모든 작업에 알림 플러그인 추가](#모든-작업에-알림-플러그인-추가)
  - [서버의 모든 작업에서 옵션 활성화](#서버의-모든-작업에서-옵션-활성화)
  - [Hg에서 체크아웃된 branch 일괄 업데이트](#hg에서-체크아웃된-branch-일괄-업데이트)
  - [프로젝트 대량 이름 바꾸기](#프로젝트-대량-이름-바꾸기)
  - [Freestyle 작업에 등록된 모든 Maven 작업을 찾아 JVM 옵션을 새 값으로 변경](#freestyle-작업에-등록된-모든-maven-작업을-찾아-jvm-옵션을-새-값으로-변경)
  - [SSH 구성을 통한 게시 변경](#ssh-구성을-통한-게시-변경)
  - [21:00~07:00 및 주말에 비활성화](#21000700-및-주말에-비활성화)
  - [SVN 경로의 버전 번호 변경](#svn-경로의-버전-번호-변경)
  - [특정 보기에 속한 모든 프로젝트를 열거하고 복제](#특정-보기에-속한-모든-프로젝트를-열거하고-복제)
  - [모든 프로젝트의 메일 알림을 Mail-Ext 게시자 플러그인으로 대체, 기존 수신자 재사용](#모든-프로젝트의-메일-알림을-mail-ext-게시자-플러그인으로-대체-기존-수신자-재사용)
  - [빌드 후 작업 공간 파일 디렉토리에 남아있는 모든 tml 파일 삭제](#빌드-후-작업-공간-파일-디렉토리에-남아있는-모든-tml-파일-삭제)
  - [비활성화된 모든 작업에 대한 작업 공간 삭제](#비활성화된-모든-작업에-대한-작업-공간-삭제)
  - [Jenkins 서버의 모든 작업을 비활성화](#jenkins-서버의-모든-작업을-비활성화)
  - [모든 에이전트 노드에 대한 정보 표시](#모든-에이전트-노드에-대한-정보-표시)
  - [모든 작업에 대한 매개변수 표시](#모든-작업에-대한-매개변수-표시)
  - [사용하는 빌드 단계별로 작업 그룹 표시](#사용하는-빌드-단계별로-작업-그룹-표시)
  - [모든 작업에 대해 알림에 사용되는 메일 수신자 목록 표시](#모든-작업에-대해-알림에-사용되는-메일-수신자-목록-표시)
  - [Jenkins는 모니터를 사용하여 다양한 동작을 검증. 하나를 닫으면 Jenkin는 다시 활성화하도록 제안하지 않음. 스크립트 사용 시 모든 모니터 상태 확인 후 재활성화 가능](#jenkins는-모니터를-사용하여-다양한-동작을-검증-하나를-닫으면-jenkin는-다시-활성화하도록-제안하지-않음-스크립트-사용-시-모든-모니터-상태-확인-후-재활성화-가능)
  - [모든 작업에 대한 타이머 트리거 표시](#모든-작업에-대한-타이머-트리거-표시)
  - [모든 에이전트에서 Jenkins 도구 위치 표시](#모든-에이전트에서-jenkins-도구-위치-표시)
  - [서버의 모든 작업에서 타임스탬퍼 플러그인 활성화](#서버의-모든-작업에서-타임스탬퍼-플러그인-활성화)
  - [실패한 모든 작업 목록 표시](#실패한-모든-작업-목록-표시)
  - [Addon: Restart](#--addon-restart)
  - [현재 실행 중이며 N초 이상 실행된 빌드 찾기](#현재-실행-중이며-n초-이상-실행된-빌드-찾기)
  - [빌드 권한이 있는 사용자 및 그룹에 취소 권한 부여](#빌드-권한이-있는-사용자-및-그룹에-취소-권한-부여)
  - [Jenkins HTTP 세션 무효화](#jenkins-http-세션-무효화)
  - [모든 작업에서 수동으로 로그 회전 실행](#모든-작업에서-수동으로-로그-회전-실행)
  - [수동으로 연결이 끊어지지 않은 경우 오프라인 노드를 모니터링 후 다시 시작](#수동으로-연결이-끊어지지-않은-경우-오프라인-노드를-모니터링-후-다시-시작)
  - [모니터링 플러그인 사용 시 http 세션, 스레드, 메모리, JVM 또는 MBean에 대한 데이터를 표시하는 여러 스크립트](#모니터링-플러그인-사용-시-http-세션-스레드-메모리-jvm-또는-mbean에-대한-데이터를-표시하는-여러-스크립트)
  - [매개변수화된 시스템 Groovy Script](#매개변수화된-시스템-groovy-script)
  - [Maven release build에서 사용자 이름 미리 선택](#maven-release-build에서-사용자-이름-미리-선택)
  - [자격 증명 및 해당 ID 목록 인쇄](#자격-증명-및-해당-id-목록-인쇄)
  - [Maven 작업에서 비활성화된 모든 모듈 제거](#maven-작업에서-비활성화된-모든-모듈-제거)
  - [Artifact Deployer 플러그인이 각 빌드에 대해 불필요하게 저장한 배포된 Artifact 목록 제거](#artifact-deployer-플러그인이-각-빌드에-대해-불필요하게-저장한-배포된-artifact-목록-제거)
  - [Git 플러그인이 각 빌드에 대해 불필요하게 저장한 BuildsByBranch의 정적 목록 제거](#git-플러그인이-각-빌드에-대해-불필요하게-저장한-buildsbybranch의-정적-목록-제거)
  - [모든 저장소에 대한 사용자 정의 설정으로 GitBlitRepositoryBrowser 설정](#모든-저장소에-대한-사용자-정의-설정으로-gitblitrepositorybrowser-설정)
  - [빌드 후 단계를 설치하고 활성화하여 배포 목표가 있는 모든 Maven 작업 업데이트](#빌드-후-단계를-설치하고-활성화하여-배포-목표가-있는-모든-maven-작업-업데이트)
  - [SVN 브라우저 업데이트](#svn-브라우저-업데이트)
  - [Jenkins 서버에 있는 모든 작업의 작업 공간 제거](#jenkins-서버에-있는-모든-작업의-작업-공간-제거)
  - [모든 노드에 있는 특정 작업의 작업 공간 지우기](#모든-노드에-있는-특정-작업의-작업-공간-지우기)

#### 오래된 스크립트 
Jenkins 소스코드에 직접 액세스하는 Groovy 스크립트 특성으로 인해 Script Console Script는 Jenkins 소스코드에서 쉽게 구식이 된다. Jenkins 코어 또는 Jenkins 플러그인의 공용 메소드 및 인터페이스가 변경되었으므로 스크립트를 실행하고 예외를 받는 것이 가능합니다.

##### Jenkins의 로컬 복사본 시작

```
export JENKINS_HOME="./my_jenkins_home"
java -jar jenkins.war
```

> Jenkins 중지 시: Ctrl + C <br>
> 프로덕션 Jenkins 인스턴스에서 Script Console 예제를 시도하는 것은 권장 X <br>
> Jenkins용 Groovy 스크립트 예시 <br>
>  [CloudBees 젠킨스 스트립트 저장소](https://github.com/cloudbees/jenkins-scripts) <br>
>  [scriptler/Jenkins CI > jenkins-scripts 저장소](https://github.com/jenkinsci/jenkins-scripts) ([Scriptler 플러그인](https://plugins.jenkins.io/scriptler)용 스크립트) <br>
>  [Sam Gleske의 jenkins-script-console-scripts 저장소](https://github.com/samrocketman/jenkins-script-console-scripts) <br>
>  [Sam Gleske의 jenkins-bootstrap-shared 저장소는 scrips/디렉토리 아래에 존재](https://github.com/samrocketman/jenkins-bootstrap-shared)

#### Scriptler 플러그인 Groovy Script
##### - Jenkins 서버의 모든 작업에 대해 Chuck Norris 플러그인 활성화

```
import jenkins.model.*


for(item in Jenkins.instance.items) {
     println("job $item.name")
     item.publishersList.replace(new  hudson.plugins.chucknorris.CordellWalkerRecorder());
}
```

#####  모든 작업에 알림 플러그인 추가

```
for (item in Hudson.instance.items) { 
  notification = item.properties.find { it.getKey().getClass() == com.tikal.hudson.plugins.notification.HudsonNotificationPropertyDescriptor }    
  if (notification != null) {
    continue
  }

  println(">>>>>>>> Adding notification plugin to $item.name")   
  protocol = com.tikal.hudson.plugins.notification.Protocol.UDP
  endpoint = new com.tikal.hudson.plugins.notification.Endpoint(protocol, '172.16.24.204:11337')
  notification = new com.tikal.hudson.plugins.notification.HudsonNotificationProperty([endpoint])

  item.addProperty(notification)
  item.save()
}
```

#####  서버의 모든 작업에서 옵션 활성화

```
import hudson.model.*
import hudson.maven.*
import hudson.tasks.*

for(item in Hudson.instance.items) {
  println("job $item.name")
  hasClaim = false;
  for(p in item.publishers )
  {
    if(p instanceof hudson.plugins.claim.ClaimPublisher)
    {
      hasClaim = true;
    }
  }
  if(!hasClaim)
  {
    println(">>>>>>>> Adding claim right to $item.name")
    item.getPublishersList().add(new  hudson.plugins.claim.ClaimPublisher() );
    item.save()
  }
}
```

#####  Hg에서 체크아웃된 branch 일괄 업데이트

```
def oldBranch = "NAME_OF_OLD_BRANCH" // update this
def newBranch = "NAME_OF_NEW_BRANCH" // update this
def jobNamePattern = "YourRegExPattern" // update this
def freeStyleJobs = hudson.model.Hudson.instance.getItems(hudson.model.FreeStyleProject.class)
for (job in freeStyleJobs)
{
  def oldScm = job.getScm()
  if (oldScm.getType().indexOf("Mercurial") 1 && job.name.matches(jobNamePattern))
  {
    if (oldScm.getBranch().equals(oldBranch))
    {
      print "Job '${job.name}' has branch '${oldBranch}' and will be updated to '${newBranch}'"
      // uncomment the next two lines to actually perform the operation. Else it simulates a dry-run
      //def newHgSCM = new  hudson.plugins.mercurial.MercurialSCM(oldScm.getInstallation(),  oldScm.getSource(), newBranch, oldScm.getModules(), oldScm.getSubdir(),  oldScm.getBrowser(), oldScm.isClean())
      //job.setScm(newHgSCM)      println "[OK]"  
    } else if (oldScm.getBranch().equals(newBranch))
    {
      println "Job '${job.name}' already is on branch '${newBranch}'"  
    } else
    {
      println "Job '${job.name}' is on branch '${oldScm.getBranch()}' and will not be updated" 
    }
  }
}
```

#####  프로젝트 대량 이름 바꾸기

```
import hudson.model.*

disableChildren(Hudson.instance.items)

def disableChildren(items) {
  for (item in items) {
    if (item.class.canonicalName != 'com.cloudbees.hudson.plugins.folder.Folder') {
	if (( m = item.name =~ /^(Findur.OpenComponent)(\..*)$/)){
          println(item.name)
          println m.group(1) + " " + m.group(2)
          newname = m[0][1] + 's' + m.group(2)
          item.renameTo(newname)
      }
    } else {
	disableChildren(((com.cloudbees.hudson.plugins.folder.Folder) item).getItems())
    }
  }
}
```

#####  Freestyle 작업에 등록된 모든 Maven 작업을 찾아 JVM 옵션을 새 값으로 변경

```
import hudson.model.*
import hudson.maven.*
import hudson.tasks.*

def newJvmOptions="-Xshare:auto -Xms64m -Xmx512m -XX:MaxPermSize=256M"

// For each project
for(item in Hudson.instance.allItems) {
  if(item instanceof FreeStyleProject) {
    println("JOB : "+item.name);
    // Find current recipients defined in project
    println(">FREESTYLE PROJECT");
    for (builder in item.builders){
      println(">> "+builder);
      if (builder instanceof Maven) {
        println(">>MAVEN BUILDER");
        println(">>TARGETS : "+builder.targets);
        println(">>NAME : "+builder.mavenName);
        println(">>POM : "+builder.pom);
        // .properties is overridden by groovy
        println(">>PROPERTIES : "+builder.@properties);
        println(">>JVM-OPTIONS : "+builder.jvmOptions);
        println(">>USE PRIVATE REPO : "+builder.usePrivateRepository);
        println(">>USER SETTINGS : "+builder.settings);
        println(">>GLOBAL SETTINGS : "+builder.globalSettings);
        def newBuilder = new Maven(builder.targets,builder.mavenName,builder.pom,builder.@properties,newJvmOptions,builder.usePrivateRepository,builder.settings,builder.globalSettings);
        item.buildersList.replace(newBuilder);
      }
    }
    println("\n=======\n");
  }
}
```

#####  SSH 구성을 통한 게시 변경

```
import java.util.*
import hudson.model.*
import hudson.maven.*
import hudson.maven.reporters.*
import hudson.matrix.*
import hudson.tasks.*
import hudson.util.DescribableList
import jenkins.plugins.publish_over_ssh.*
import jenkins.plugins.publish_over.*

hudson.model.Hudson.instance.items.findAll{job -> job.isBuildable() }.each{
job -> 

  if(job instanceof FreeStyleProject) {
    for (builder in job.builders){
      if(builder instanceof BapSshBuilderPlugin) {
        ArrayList<BapPublisher> publishers = builder.delegate.delegate.publishers
        
        for(publisher in publishers) {
          if (publisher.configName == "bad-server") {
            println "Changing job: ${job.name}"
            publisher.configName = "good-server"
          }
        }
      }
    }
  }
}
```

#####  21:00~07:00 및 주말에 비활성화

```
import hudson.model.*
import hudson.triggers.*


TriggerDescriptor SCM_TRIGGER_DESCRIPTOR = Hudson.instance.getDescriptorOrDie(SCMTrigger.class)
assert SCM_TRIGGER_DESCRIPTOR != null;

for(item in Hudson.instance.items)
{
  println("Working on project <$item.name>")
  
  def trigger = item.getTriggers().get(SCM_TRIGGER_DESCRIPTOR)
  if(trigger != null && trigger instanceof SCMTrigger)
  {
    print("> $trigger.spec")
    String[] parts = trigger.spec.split(" ");
    
    //Do wanted modifs
    if(parts[1] == "*" )
    {
      parts[1] = "7-21"
    }
    if(parts[4] == "*")
    {
      parts[4] = "1-5"
    }
    //end modifs
    
    StringBuilder newSpec = new StringBuilder();
    for(p in parts)
    {
      newSpec.append(p+" ");
    }
    
    println(" => $newSpec");

    def newTrigger = new SCMTrigger(newSpec.toString())
    newTrigger.job = item

    item.removeTrigger(SCM_TRIGGER_DESCRIPTOR)
    item.addTrigger(newTrigger)
  }
  else
  {
    println "> Nothing to do"
  }
}
```

#####  SVN 경로의 버전 번호 변경

```
import hudson.scm.*
//import hudson.model.*

/** Old Version for the SVN-Path */
oldVersion  = "1.28"

/** New Version for the SVN-Path */
newVersion  = "1.29"

/** Path to the SVN-Repo containing with the following */
svnpath = "repo/testjob"

 /** Jobs containing with */
jobs = "testjob"

/** Should we override existing values? */
overrideExistingValues = false

/** Display Konfiguration */
println "### Overwrite SVN-Version ###"
println "oldVersion:     " + oldVersion
println "newVersion:     " + newVersion
println "Jobs with:      " + jobs
println "Repo_with_Path: " + svnpath


// ----- Do the work. -----

// Access to the Hudson Singleton
hudsonInstance = hudson.model.Hudson.instance

// Retrieve all Jobs which starts with -jobs-
allItems = hudsonInstance.items
chosenJobs = allItems.findAll{job -> job.name.contains(jobs)}

// Table header
col1 = "Job".center(35)
col2 = "OldPath".center(120)
col3 = "NewPath".center(120)
header = "$col1 | $col2 | $col3"
line = header.replaceAll("[Change Version-Number in SVN-path^|]", "-").replaceAll("\\|", "+")

println line
println header
println line

// Do work and create the result table
chosenJobs.each { job ->
 if(!(job instanceof hudson.model.ExternalJob)) {
   // No SCM-Configuration possible for External Jobs!
   if (job.scm instanceof SubversionSCM) {
     // Job has a SubversionSCM-Konfiguration
     def oldSvnPath = [][]
     def newSvnPath = [][]
     job.scm.locations.each{
       //For every Subversion-Location
       if (it.remote.contains(svnpath)) {
         //SVN-Path contains the given Path
         oldRemote = it.remote.padRight(119)
         jobname  = job.name.padRight(35)
         newRemote = it.remote
         if (it.remote.contains(oldVersion)) {
           //SVN-Path contains the old Version, which should be replaced
           newRemote = it.remote.replaceAll(/$oldVersion/,"$newVersion")  //Replace
           //Build new SVN-Location (it is not possible to change a value in the existing configuration)
           newSvnPath.add(new hudson.scm.SubversionSCM.ModuleLocation(newRemote,it.local))

           //For Visualisation of the changed Value
           newRemote = newRemote.padRight(120,"<")
           // Output Result for this Subversion-Location
           println "$jobname | $oldRemote ]> $newRemote"
         } else {
           //Visualisation of value which is not changed
           newRemote = newRemote.padRight(120)
           // Output Result for this Subversion-Location
           println "$jobname | $oldRemote  | $newRemote"
         }
       }

     }
     // Every Location was checked. Building new SVN-Configuration with the new SVN-Locations
     newscm = new hudson.scm.SubversionSCM(newSvnPath, job.scm.workspaceUpdater, job.scm.browser,
     job.scm.excludedRegions, job.scm.excludedUsers, job.scm.excludedRevprop, job.scm.excludedCommitMessages, job.scm.includedRegions)
     if (overrideExistingValues){
       // Only write values, when overrideExistingValues is true
       job.scm = newscm;
     }
     println line
     //Job is done
   }
 }
}
println line
//done
```

#####  특정 보기에 속한 모든 프로젝트를 열거하고 복제

```
import hudson.model.*
 
def str_view = "MyProduct_Release_1.0"
def str_search = "Rel_1.0"
def str_replace = "Rel_1.1"
 
def view = Hudson.instance.getView(str_view)
 
//copy all projects of a view
for(item in view.getItems())
{

  //create the new project name
  newName = item.getName().replace(str_search, str_replace)

 
  // copy the job, disable and save it
  def job = Hudson.instance.copy(item, newName)
  job.disabled = true
  job.save()
  
  // update the workspace to avoid having two projects point to the same location
  AbstractProject project = job
  def new_workspace = project.getCustomWorkspace().replace(str_search, str_replace)
  project.setCustomWorkspace(new_workspace)
  project.save()
  
  println(" $item.name copied as $newName")

}
```

#####  모든 프로젝트의 메일 알림을 Mail-Ext 게시자 플러그인으로 대체, 기존 수신자 재사용

```
import hudson.model.*
 
def str_view = "MyProduct_Release_1.0"
def str_search = "Rel_1.0"
def str_replace = "Rel_1.1"
 
def view = Hudson.instance.getView(str_view)
 
//copy all projects of a view
for(item in view.getItems())
{

  //create the new project name
  newName = item.getName().replace(str_search, str_replace)

 
  // copy the job, disable and save it
  def job = Hudson.instance.copy(item, newName)
  job.disabled = true
  job.save()
  
  // update the workspace to avoid having two projects point to the same location
  AbstractProject project = job
  def new_workspace = project.getCustomWorkspace().replace(str_search, str_replace)
  project.setCustomWorkspace(new_workspace)
  project.save()
  
  println(" $item.name copied as $newName")

}
```

#####  빌드 후 작업 공간 파일 디렉토리에 남아있는 모든 tml 파일 삭제

```
import hudson.model.*

def counter = 0

// Create a ref for closure
def delClos

// Define closure
delClos = {
	it.eachDir( delClos );
	if(it.getName().contains("workspace-files")) {
		it.eachFile {
			if(it.getName().endsWith(".tmp") ){
				println "Deleting file ${it.canonicalPath}";
				it.delete()
				counter++;
			}
		}
	}
}

// Apply closure
for(item in Hudson.instance.items) {
	println "Applying on " + item.rootDir
	delClos( item.rootDir )
}
println counter + " files deleted"
```

#####  비활성화된 모든 작업에 대한 작업 공간 삭제

```
//michaeldkfowler
import jenkins.model.*
Jenkins.instance.getAllItems(AbstractProject.class)
.findAll {it.disabled}
    .each {
      println("Wiping workspace for "+it.fullName)
      it.doDoWipeOutWorkspace()
    }
```

#####  Jenkins 서버의 모든 작업을 비활성화

```
import hudson.model.*


disableChildren(Hudson.instance.items)

def disableChildren(items) {
  for (item in items) {
    if (item.class.canonicalName == 'com.cloudbees.hudson.plugins.folder.Folder') {
        disableChildren(((com.cloudbees.hudson.plugins.folder.Folder) item).getItems())
    } else if (item.class.canonicalName != 'org.jenkinsci.plugins.workflow.job.WorkflowJob') {
      item.disabled=true
      item.save()
      println(item.name)
    }
  }
}
```

#####  모든 에이전트 노드에 대한 정보 표시

```
for (aSlave in hudson.model.Hudson.instance.slaves) {
  println('====================');
  println('Name: ' + aSlave.name);
  println('getLabelString: ' + aSlave.getLabelString());
  println('getNumExectutors: ' + aSlave.getNumExecutors());
  println('getRemoteFS: ' + aSlave.getRemoteFS());
  println('getMode: ' + aSlave.getMode());
  println('getRootPath: ' + aSlave.getRootPath());
  println('getDescriptor: ' + aSlave.getDescriptor());
  println('getComputer: ' + aSlave.getComputer());
  println('\tcomputer.isAcceptingTasks: ' + aSlave.getComputer().isAcceptingTasks());
  println('\tcomputer.isLaunchSupported: ' + aSlave.getComputer().isLaunchSupported());
  println('\tcomputer.getConnectTime: ' + aSlave.getComputer().getConnectTime());
  println('\tcomputer.getDemandStartMilliseconds: ' + aSlave.getComputer().getDemandStartMilliseconds());
  println('\tcomputer.isOffline: ' + aSlave.getComputer().isOffline());
  println('\tcomputer.countBusy: ' + aSlave.getComputer().countBusy());
  //if (aSlave.name == 'NAME OF NODE TO DELETE') {
  //  println('Shutting down node!!!!');
  //  aSlave.getComputer().setTemporarilyOffline(true,null);
  //  aSlave.getComputer().doDoDelete();
  //}
  println('\tcomputer.getLog: ' + aSlave.getComputer().getLog());
  println('\tcomputer.getBuilds: ' + aSlave.getComputer().getBuilds());
}
```

#####  모든 작업에 대한 매개변수 표시

```
import hudson.model.*

for(item in Hudson.instance.items) {
  prop = item.getProperty(ParametersDefinitionProperty.class)
  if(prop != null) {
    println("--- Parameters for " + item.name + " ---")
    for(param in prop.getParameterDefinitions()) {
      try {
        println(param.name + " " + param.defaultValue)
      }
      catch(Exception e) {
        println(param.name)
      }
    }
    println()
  }
}
```
#####  사용하는 빌드 단계별로 작업 그룹 표시

```
import hudson.model.*
import hudson.tasks.*

//All the projects on which we can apply the getBuilders method
def allProjects = Hudson.instance.items.findAll{ it instanceof Project }

//All the registered build steps in the current Jenkins Instance
def allBuilders = Builder.all()

//Group the projects by the build steps used
def projectsGroupByBuildSteps = allBuilders.inject([:]){
   map, builder ->   
   map[builder.clazz.name] = allProjects.findAll{it.builders.any{ it.class.name.contains(builder.clazz.name)}}.collect{it.name}
   map
}

//presentation
projectsGroupByBuildSteps.each{
   println """--- $it.key ---
   \t$it.value\n"""
}
```

#####  모든 작업에 대해 알림에 사용되는 메일 수신자 목록 표시

```
import hudson.plugins.emailext.*
import hudson.model.*
import hudson.maven.*
import hudson.maven.reporters.*
import hudson.tasks.*

// For each project
for(item in Hudson.instance.items) {
 println("JOB : "+item.name);
 // Find current recipients defined in project
 if(!(item instanceof ExternalJob)) {
 if(item instanceof MavenModuleSet) {
 println(">MAVEN MODULE SET");
 // Search for Maven Mailer Reporter
 println(">>Reporters");
 for(reporter in item.reporters) {
 if(reporter instanceof MavenMailer) {
 println(">>> reporter : "+reporter+" : "+reporter.recipients);
 }
 }
 } else
 if(item instanceof FreeStyleProject) {
 println(">FREESTYLE PROJECT");
 }
 println(">>Publishers");
 for(publisher in item.publishersList) {
 // Search for default Mailer Publisher (doesn't exist for Maven projects)
 if(publisher instanceof Mailer) {
 println(">>> publisher : "+publisher+" : "+publisher.recipients);
 } else
 // Or for Extended Email Publisher
 if(publisher instanceof ExtendedEmailPublisher) {
 println(">>> publisher : "+publisher+" : "+publisher.recipientList);
 }
 }
 } else {
 println("External Jobs cannot have MailNotificationsRecipients")
 }
 println("\n=======\n");
}
```

#####  Jenkins는 모니터를 사용하여 다양한 동작을 검증. 하나를 닫으면 Jenkin는 다시 활성화하도록 제안하지 않음. 스크립트 사용 시 모든 모니터 상태 확인 후 재활성화 가능

```
hudson.model.Hudson.instance.administrativeMonitors.each{
    println "* Monitor : "+it.id
    println "** Enabled : "+it.enabled
    println "** Activated : "+it.activated
    println "========="
}
```

#####  모든 작업에 대한 타이머 트리거 표시

```
import hudson.model.*
import hudson.triggers.*

for(item in Hudson.instance.items) {
	for(trigger in item.triggers.values()) {
		if(trigger instanceof TimerTrigger) {
			println("--- Timer trigger for " + item.name + " ---")
			println(trigger.spec + '\n')
		}
	}
}
```

#####  모든 에이전트에서 Jenkins 도구 위치 표시

```
import hudson.model.*
import hudson.node_monitors.*
import hudson.slaves.*
import java.util.concurrent.*
import hudson.tools.ToolDescriptor;
import hudson.tools.ToolInstallation;
jenkins = Hudson.instance
  
TaskListener log;
  
def getEnviron(computer) {
   def env
   def thread = Thread.start("Getting env from ${computer.name}", { env = computer.environment })
   thread.join(2000)
   if (thread.isAlive()) thread.interrupt()
   env
}

def slaveAccessible(computer) {
    getEnviron(computer)?.get('PATH') != null
}

for (aSlave in jenkins.slaves) {
   def computer = aSlave.computer
  
     println "Checking computer ${computer.name}:"
     def isOK = (slaveAccessible(computer) && !computer.offline)
     if (isOK) {

     
        for (ToolDescriptor<?> desc : ToolInstallation.all()) {
            for (ToolInstallation inst : desc.getInstallations()) {
                println ('\tTool Name: ' + inst.getName());
                println ('\t\tTool Home: ' + inst.translateFor(aSlave,log));
            }  
 }  
    } else {
        println "  ERROR: can't get PATH from slave: node is offline."
    }       
}
```

#####  서버의 모든 작업에서 타임스탬퍼 플러그인 활성화

```
for (item in Hudson.instance.items) {
  println("\njob: $item.name")
  hasTimestamper = false;
  item.buildWrappersList.each {
    if (it instanceof hudson.plugins.timestamper.TimestamperBuildWrapper) {
      hasTimestamper = true;
    }
  }
  if (!hasTimestamper) {
    println(">>>>>>>> Adding timestamper right to $item.name")
    item.buildWrappersList.add(new hudson.plugins.timestamper.TimestamperBuildWrapper());
    item.save()
  }
}
```

#####  실패한 모든 작업 목록 표시

```
// Get the list of failed jobs
activeJobs = hudson.model.Hudson.instance.items.findAll{job -> job.isBuildable()}
failedRuns = activeJobs.findAll{job -> job.lastBuild != null && job.lastBuild.result == hudson.model.Result.FAILURE}
// Do something with them - e.g. listing them
failedRuns.each{run -> println(run.name)}
```

##### >  Addon: Restart

```
startServer = "admin computer"
startNote   = "bulk start"
cause = new hudson.model.Cause.RemoteCause(startServer, startNote)
failedRuns.each{run -> run.scheduleBuild(cause)}
```

#####  현재 실행 중이며 N초 이상 실행된 빌드 찾기

```
int MAX_ALLOWED_DURATION_IN_SECONDS = 3600 * 6 // 6 hours


  def busyExecutors = Jenkins.instance.computers
                                .collect { 
                                  c -> c.executors.findAll { it.isBusy() }
                                }
                                .flatten() // reminder: transforms list(list(executor)) into list(executor)

def ok = true

println "Busy Executors list"
busyExecutors.each { e -> 
  println e ; 
  int durationInSeconds = (System.currentTimeMillis() - e.executable.getTimeInMillis())/1000.0
  
  if(durationInSeconds > MAX_ALLOWED_DURATION_IN_SECONDS )
  {
    ok = false;
  }
  println "\t duration=$durationInSeconds"
  println "" 
}

println "Done"

return ok
```

#####  빌드 권한이 있는 사용자 및 그룹에 취소 권한 부여

```
import hudson.security.*
import jenkins.security.*
import jenkins.model.Jenkins


boolean dryrun=true

if (dryrun) {
  println ''.center(100,'!')
  println 'This is a dryrun, nothing will be changed'.center(100,'!')
  println 'Change this line: boolean dryrun=false to boolean dryrun=true to make the real change'.center(100,'!')
  println ''.center(100,'!')
}

switch (Jenkins.instance.authorizationStrategy){
  case GlobalMatrixAuthorizationStrategy:
    println '\nGlobal Matrix Strategy defined. Fixing Cancel permissions...\n'
    def sids = Jenkins.instance.authorizationStrategy.getAllSIDs().plus('anonymous')
    for (sid in sids){
      if (Jenkins.instance.authorizationStrategy.hasPermission(sid,hudson.model.Item.BUILD)){
        println '----'+sid+' has Build permission and Cancel permission will be add'
        if (!dryrun) Jenkins.instance.authorizationStrategy.add(hudson.model.Item.CANCEL,sid)
      }
    }
    if (!dryrun) Jenkins.instance.save()
  case ProjectMatrixAuthorizationStrategy:
    println '\nProject Matrix Strategy defined. fixing Cancel permissions...\n'
    def jobs = Jenkins.instance.items
    jobs.each {
      println it.name.center(80,'-')
      def authorizationMatrixProperty = it.getProperty(AuthorizationMatrixProperty.class)
      def sids = authorizationMatrixProperty?.getAllSIDs().plus('anonymous')
      for (sid in sids){
        if (authorizationMatrixProperty?.hasPermission(sid,hudson.model.Item.BUILD)){
          println ''+sid+' has Build permission and Cancel permission will be add'
          if (!dryrun) authorizationMatrixProperty?.add(hudson.model.Item.CANCEL,sid)
        }
      }
      if (!dryrun) it.save()
    }
    break
  default:
    println "No permission need to be mofdified gloabally"
    break
}

return
```

#####  Jenkins HTTP 세션 무효화

```
import java.io.Serializable;
import java.util.ArrayList;
import java.util.Collection;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;
import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;
import java.util.concurrent.ConcurrentMap;
import java.util.concurrent.atomic.AtomicInteger;

import javax.servlet.ServletContextEvent;
import javax.servlet.ServletContextListener;
import javax.servlet.http.HttpSession;
import javax.servlet.http.HttpSessionActivationListener;
import javax.servlet.http.HttpSessionEvent;
import javax.servlet.http.HttpSessionListener;
import net.bull.javamelody.*;
  
def chuck = SessionListener.newInstance();
println ("Session Info: ");
println chuck.getAllSessionsInformations();
sessionCount = chuck.getSessionCount();
println ("Number of Session: " + sessionCount);
maxSessionCount = 70;
if ( sessionCount > maxSessionCount ) {
          println ("Open Session " + sessionCount + " more than " + maxSessionCount);
          println "Invalidating...";
          chuck.invalidateAllSessions();
}
```

#####  [모든 작업에서 수동으로 로그 회전 실행](https://www.jenkins.io/doc/book/managing/nodes/)

#####  수동으로 연결이 끊어지지 않은 경우 오프라인 노드를 모니터링 후 다시 시작

```
//michaeldkfowler
import jenkins.model.*
Jenkins.instance.getAllItems(AbstractProject.class)
.findAll { it.logRotator }
    .each {
      it.logRotator.perform(it)
    }
```

#####  모니터링 플러그인 사용 시 http 세션, 스레드, 메모리, JVM 또는 MBean에 대한 데이터를 표시하는 [여러 스크립트](https://wiki.jenkins.io/display/JENKINS/Monitoring+Scripts)

#####  매개변수화된 시스템 Groovy Script

```
import hudson.model.*

// get current thread / Executor
def thr = Thread.currentThread()
// get current build
def build = thr?.executable


// get parameters
def parameters = build?.actions.find{ it instanceof ParametersAction }?.parameters
parameters.each {
   println "parameter ${it.name}:"
   println it.dump()
   println "-" * 80
}


// ... or if you want the parameter by name ...
def hardcoded_param = "FOOBAR"
def resolver = build.buildVariableResolver
def hardcoded_param_value = resolver.resolve(hardcoded_param)


println "param ${hardcoded_param} value : ${hardcoded_param_value}"
```

#####  Maven release build에서 사용자 이름 미리 선택

```
import hudson.model.*
import hudson.maven.*
import hudson.tasks.*
import org.jvnet.hudson.plugins.m2release.*

for(item in Hudson.instance.items) {
  if (item instanceof MavenModuleSet)
  {
    println("\njob $item.name ");
    rw = item.getBuildWrappers().get(M2ReleaseBuildWrapper.class);
    if (rw == null)
    {
      println("release build not configured");
    }
    else 
    {
     println("append Username: "+rw.isSelectAppendHudsonUsername())
     rw.setSelectAppendHudsonUsername(true)
     item.save()
    }
  }  
}
```

#####  자격 증명 및 해당 ID 목록 인쇄

```
  def creds = com.cloudbees.plugins.credentials.CredentialsProvider.lookupCredentials(
      com.cloudbees.plugins.credentials.common.StandardUsernameCredentials.class,
      Jenkins.instance,
      null,
      null
  );
  for (c in creds) {
       println(c.id + ": " + c.description)
  }
```

#####  Maven 작업에서 비활성화된 모든 모듈 제거

```
Jenkins.instance.getAllItems(hudson.maven.MavenModuleSet.class).findAll{job -> job.isBuildable()}.each{
job ->
  job.getDisabledModules(true).each{module -> module.delete()} 
  println(job.name+" cleaned")
}
```

#####  Artifact Deployer 플러그인이 각 빌드에 대해 불필요하게 저장한 배포된 Artifact 목록 제거

```
import hudson.model.*

hudsonInstance = hudson.model.Hudson.instance
allItems = hudsonInstance.items

// Iterate over all jobs and find the ones that have a org.jenkinsci.plugins.artifactdeployer.DeployedArtifacts
// as an action.

def jobCounter = 0;
def totalBuildCounter = 0;

for (job in allItems) {
  def buildCounter = 0;
  for (build in job.getBuilds()) {
    // It is possible for a build to have multiple actions
    def adActions = build.getActions(org.jenkinsci.plugins.artifactdeployer.DeployedArtifacts.class)
    if (adActions != null && !adActions.isEmpty()) {
      for (action in adActions) {
        build.actions.remove(action)
      }
      build.save();
      buildCounter++;
    }
  }
  if (buildCounter > 0) {
      println("Job: " + job.name + " cleaned " + buildCounter + " builds");
      jobCounter++;
      totalBuildCounter += buildCounter;
  }  
}

println("Cleaned " + jobCounter + " jobs and a total of " + totalBuildCounter + " builds");
```

#####  [Git 플러그인이 각 빌드에 대해 불필요하게 저장한 BuildsByBranch의 정적 목록 제거](https://plugins.jenkins.io/git/)

#####  모든 저장소에 대한 사용자 정의 설정으로 GitBlitRepositoryBrowser 설정

```
import hudson.model.*
import hudson.triggers.*
import hudson.plugins.git.browser.GitBlitRepositoryBrowser

// you might want to change here
def url = 'https://mygitblitserver/gitblit/'
def i = 0
for(item in Hudson.instance.items) {
  def scm = item.scm
  if((scm instanceof hudson.plugins.git.GitSCM) && !(scm.browser instanceof GitBlitRepositoryBrowser)) {
    println('##########')
    println(scm.dump())
    // you might want to change here
    def match = scm.userRemoteConfigs =~ /\/spu\/test\/git\/(.*?.git)/
    if(match) {
      i++
      def projectName = match[0][1]
      println projectName
      scm.browser = new GitBlitRepositoryBrowser(url, projectName)
    }
  }
}
println("$i projects updated")
```

#####  빌드 후 단계를 설치하고 활성화하여 배포 목표가 있는 모든 Maven 작업 업데이트

```
import java.util.*
import hudson.model.*
import hudson.maven.*
import hudson.maven.reporters.*
import hudson.matrix.*
import hudson.tasks.*

hudson.model.Hudson.instance.items.findAll{job -> job.isBuildable() && job instanceof MavenModuleSet}.each {
job -> 
  println(job.name)
  if (job.goals.indexOf("deploy")>0) {
    println("* Must update goals (deploy -> install) : " + job.goals)
    def newGoals = job.goals.replaceAll("deploy", "install");
    println("* New goals : " + newGoals)
    // Comment the 3 following lines for a first run to check goals modifications without modifying anything
    job.goals = newGoals
    job.archivingDisabled = false // It is necessary to archive artifacts to deploy them after the build
    job.publishers.replace(new hudson.maven.RedeployPublisher(null, null, true, false));
    println("* Redeploy publisher added");
  } else {
    println("* This maven job doesn't deploy its artifacts");
  }
}
```

#####  SVN 브라우저 업데이트

```
import hudson.model.*
import hudson.maven.*
import hudson.tasks.*
import hudson.scm.*
import hudson.scm.browsers.*

for(item in Hudson.instance.items) {
  hasClaim = false;
  if (item.scm instanceof SubversionSCM)
  {
      println("\njob $item.name")
      println(item.scm.browser);
      if (item.scm.browser instanceof Sventon2)
      {
        println(item.scm.browser.url);
        println(item.scm.browser.repositoryInstance);
      }
      else
      {
        // add the repo browser details.
        browser = new hudson.scm.browsers.Sventon2(new URL("http://...../"), ".....")

        // unfortunately can't just add a browser - need to create a new scm entry, which is complex...
        scm = new  SubversionSCM(Arrays.asList(item.scm.locations), item.scm.workspaceUpdater, browser, item.scm.excludedRegions, item.scm.excludedUsers, item.scm.excludedRevprop, item.scm.excludedCommitMessages, item.scm.includedRegions, item.scm.ignoreDirPropChanges)

        item.scm = scm
        item.save()
        println("Updated repo browser");
      }
  }
}
```

#####  Jenkins 서버에 있는 모든 작업의 작업 공간 제거

```
import hudson.model.*
// For each project
for(item in Hudson.instance.items) {
  // check that job is not building
  if(!item.isBuilding()) {
    println("Wiping out workspace of job "+item.name)
    item.doDoWipeOutWorkspace()
  }
  else {
    println("Skipping job "+item.name+", currently building")
  }
}
```

#####  모든 노드에 있는 특정 작업의 작업 공간 지우기

```
import hudson.model.*
// For each job
for (item in Hudson.instance.items)
{
  jobName = item.getFullDisplayName()
  // check that job is not building
  if (!item.isBuilding())
  {
    // TODO: Modify the following condition to select which jobs to affect
    if (jobName == "MyJob")
    {
      println("Wiping out workspaces of job " + jobName)
      customWorkspace = item.getCustomWorkspace()
      println("Custom workspace = " + customWorkspace)

      for (node in Hudson.getInstance().getNodes())
      {
        println("  Node: " + node.getDisplayName())
        workspacePath = node.getWorkspaceFor(item)
        if (workspacePath == null)
        {
          println("    Could not get workspace path")
        }
        else
        {
          if (customWorkspace != null)
          {
            workspacePath = node.getRootPath().child(customWorkspace)
          }

          pathAsString = workspacePath.getRemote()
          if (workspacePath.exists())
          {
            workspacePath.deleteRecursive()
            println("    Deleted from location " + pathAsString)
          }
          else
          {
            println("    Nothing to delete at " + pathAsString)
          }
        }
      }
    }
  }
  else
  {
    println("Skipping job " + jobName + ", currently building")
  }
}
```

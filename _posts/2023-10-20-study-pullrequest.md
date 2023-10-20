---
title: "Github Pull Request 사용 방법"
date: 2023-10-20
categories: [Study]
comments: true
sitemap :
  changefreq : daily
  priority : 1.0
---

**Pull Request**: Repository에 대한 제안된 변경 사항

**Repository**: 프로젝트 파일, 각 파일의 수정 기록(Issue), 프로젝트의 작업을 논의하고 관리할 수 있는 공간

**branch**: Repository에 적용하는 변경 사항과 별도로 기능 개발, 버그 수정을 안전하게 작업할 수 있는 작업 영역

**push**: branch에서 만든 commit을 repository에 적용

**commit**: 변경 사항 기록

**merge**: 기본 branch에 변경 사항을 병합

---
:heavy_check_mark:  **1. 목적**
- Github Repository의 개인 branch에 push한 변경 사항을 다른 사람에게 알림
- 공동 작업자와 변경 사항을 논의 및 검토
- 변경 사항을 기본 branch에 merge


:heavy_check_mark: **2. 설정**

branch 보호 설정

> **1. [Settings] > [Branches] > [Add branch protection rule]**
> 
> ![1](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/275371413-f78ce73f-fa30-4686-9454-f10a7b892bdd.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231020%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231020T023243Z&X-Amz-Expires=300&X-Amz-Signature=f4ec15f53d4e8cb8a31b22fafb23b28b40249b3c9db55571ef5b4bfbae7da156&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)
> 
> **2. Branch name pattern 설정, Protect matching branches 내 Require a pull request before merging 체크박스 선택**
> 
> ![2](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/275372076-f3a6a081-0af1-44b7-baf3-7758f8cd6ca2.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231020%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231020T023334Z&X-Amz-Expires=300&X-Amz-Signature=42258ba3df1b8627227e83a0e369727f82762143f80e50d39e8d6458dc68b7f9&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)
> 
> **3. 승인 인원 설정**
> 
> ![3](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/275372378-ee22d805-cb80-40e3-bc8e-b7c629f4d340.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231020%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231020T023350Z&X-Amz-Expires=300&X-Amz-Signature=c0e2523a732e4a86b6ac41c35b3476e12823009da16b92d37c6ab746bba5be1e&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)
>
> **4. create 버튼 클릭**
>
> ![3-1](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/275377818-27804491-a099-46d3-bfac-9c3726b7591c.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231020%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231020T023408Z&X-Amz-Expires=300&X-Amz-Signature=e14fe0dbe5910749f53056672459e6ace90e250f2de9579383e2e460aace4212&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)


:heavy_check_mark: **3. 사용 방법**

> **1. Git Push**
> 
> **2. Branches 확인**
> 
> ![4](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/275374259-15e87355-65f6-4273-92a9-3ec54dc65656.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231020%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231020T023435Z&X-Amz-Expires=300&X-Amz-Signature=140c2d2557c791a3fe18275b67875435e2bb58e62837e2fadbdfdbc3dcbde741&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)
>
> **3. Compare & pull request 버튼 클릭**
> 
> ![5](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/275374357-95891356-e0f1-429b-bc3a-84646f664d1e.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231020%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231020T023450Z&X-Amz-Expires=300&X-Amz-Signature=d115fef6e567a6fe0d63f27d1dac98471af04ef6d434610a920d5173e65e0390&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)
> 
> **4. merge할 브랜치 확인**
> 
> ![6](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/275374731-2bfbf661-dd10-4e6b-a3fd-65d09877f63c.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231020%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231020T023503Z&X-Amz-Expires=300&X-Amz-Signature=0222785e933506cdd8b70766b042b4d3ee9609952fffa7730f9d5b2413a36da3&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)
> 
> **5. 필요 내용 입력 후 Create pull request 클릭**
> 
> 필요 내용: 제목, 설명, Reviewers, Assignees, Labels, Projects, Milestone
> 
> ![6-1](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/275374842-69227a89-3ce8-4b07-b5ef-c2d2f7bbd383.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231020%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231020T023520Z&X-Amz-Expires=300&X-Amz-Signature=40c0c82b6e54070eeb9967e65baad4ac7ac1bb1183894474e54d3192a861b8e7&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)
> 
> **6. Merge pull request 클릭**
> 
> ![7](https://github-production-user-asset-6210df.s3.amazonaws.com/113246634/275374921-ba9e0c75-b5c2-4538-b0b2-1f5309858827.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231020%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231020T023536Z&X-Amz-Expires=300&X-Amz-Signature=0ef7f8c0be7386a5b2e34e72482dd72725f9c8d215e846d36965cac0f7d3c0bc&X-Amz-SignedHeaders=host&actor_id=113246634&key_id=0&repo_id=673132111)
>
> **6-1. Merge pull request가 비활성화일 때**
> 
> [해결 방법](https://docs.github.com/ko/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-on-github)
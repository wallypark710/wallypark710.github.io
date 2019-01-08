---
layout: post
title: "[Git] How to use Git"
date: 2018-07-10 10:00:00
categories:

---



# How to use Git

## Intro

버전 관리 시스템. 사실 지금까지는 버전을 잘 관리해야겠다는 생각조차 잘 하지 못했다. 대부분의 개발은 혼자 진행 했었고, 내 나름대로 잘 관리한다고 생각했다. 사실 지금까진 결과만을 보고 있었다. 잘 돌아간다면 그걸로 끝이었다. 나의 크나큰 착각이었다. 협업을 하지 않더라도 코드수정의 발자국들은 중요하다는걸 뒤늦게 깨닳았다. 물론 협업을 할 때는 두 말 할 필요가 없다. 이제 안되면 날리고 다시하지라는 생각은 저 멀리 던져버려야 한다. 버전 관리의 중요성을 알았으니, 이제 어떻게 쓰는지 알아야할 때이다.



## What is Git ?

Git은 프로그램 등의 소스 코드 관리를 위한 분산 버전 관리 시스템이다. Git의 작업 폴더는 모두 전체 기록과 각 기록을 추적할 수 있는 정보를 포함하고 있으며 네트워크에 접근하거나 중앙 서버에 의존하지 않는다. 쉽게말해 진행되고있는 작업의 수정사항을 모두 기록하며 원하는 특정지점으로 되돌리기가 매우 용이하다. 다수의 사람들과 함께 작업할경우 각각의 변동사항을 체계적으로 관리할 수 있다.



## What is Github?

먼저 Git 과 Github은 다르다. Github은 분산 버전 관리 툴인 Git을 사용하는 프로젝트를 지원하는 웹호스팅 서비스이다. 쉽게말해 Git에 네트워크를 연결한것이 Github이다.



## Basic Git Workflow

1. 깃 사용자명/ 이메일 구성하기.

   ```text
   $git config user.name "USER_NAME"
   $git config user.email "EMAIL_ADDRESS"
   ```

2. 깃허브에 있는 원격 저장소를 로컬 저장소로 가져오기.

   ```text
   $git clone (github_repository_address)
   ```

3. 현재 깃의 상황을 확인하기. 

   ```text
   $git status
   ```

   - 새로운 파일의 추가나 여러 파일의 수정 여부등 깃의 상황을 한눈에 볼 수 있다.

4. 파일의 어떤 부분이 변경이되었는지를 확인.

   ```text
   $git diff
   ```

5. 어떤 파일을 원격 저장소(github)에 올릴지를 지정해주기.

   ```text
   $git add (file_name)
   ```

   - 원격 저장소에 올리기전 반드시 해야하는 작업

6. 어떤 부분이 변경되었는지를 기록

   ```text
   $git commit -m 'input message'
   ```

   - git commit 만 할 경우 vi 에디터로 이동하여 메세지를 입력하게 된다. 

7. 원격 저장소에 올리기

   ```text
   $git push origin master
   ```

8. 로컬에서 저장소를 만들때

   - github에 저장소를 먼저 만든다.

   - 지정하고자 하는 로컬 디렉터리로 이동

     ```text
     $git init
     $git remote add origin (github_repository_address)
     ```

9. 파일 이름 변경

   ```text
   $git mv (변경할 파일 이름) (수정된 파일 이름)
   ```

   - 이후 commit 과 push를 진행하면 github에 수정된 내용이 갱신된다.



1. 마지막 커밋 고치기

   ```text
   $git commit --amend
   ```

2. 깃 커밋 로그 확인하기

   ```text
   $git log
   ```





# Remote Flow

여러명이 함께 코드를 작성하는 경우 git의 remote를 이용하여 코드를 공유할 수 있다.



- 다른 저장소를 remote로 연결하기

  ```text
  $ git remote add [custom_name] [repo_address]
  ```

- 다른 저장소의 코드를 가져오기

  ```text
  $ git pull [custom_name] [branch_name]
  ```

- 각각의 저장소를 clone한 뒤에 ① ② ③ ④ 순서를 반복하면서 진행된다.

  ![flow](/images/flow.png)



- remote 삭제하기

  ```javascript
  $ git remote rm [custom_name]
  ```

- 직전 log로 돌아가기 ( 직전 상태로 돌아가기 )

  ```text
  $ git reset --hard HEAD~1
  ```

  : `--hard` 옵션은 log와 실제 파일내용까지 모두 이전 상태로 돌아간다.

  : `--soft` 옵션은 실제 파일내용은 돌아가지않고 커밋할수 있는 상태로 돌아간다. 그리고 log는 지워진다.
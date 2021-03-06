---
title: "Jenkins에서 Maven Project 빌드하기"
date: 2019-06-01
categories: jenkins
comments: true
---


>Jenins Guide 03  
create maven job

Jenkins에서 Maven Project 빌드 방법에 대한 가이드입니다.

(Github을 통해 소스코드를 받습니다.)

## Step 1:  Maven Integration plugin 설치
> 이미 설치된 플러그인이면 Skip  
'새로운 Item' 클릭 후 Maven project 생성 버튼이 존재하는지 확인

1. 좌측 메뉴 **Jenkins관리** 클릭
2. 플러그인 관리 클릭
3. 설치 가능 목록에 "Maven Integration" 존재하면 설치
![예제1]({{ "/assets/images/20190601-2/example1.gif"}})

## Step 2: new Job 생성
1. Jenkins Home 이동
2. 좌측 메뉴 **새로운 Item** 클릭
3. Item Type에 Maven project 선택
![예제2]({{ "/assets/images/20190601-2/example2.png"}})

## Step 3: Job 환경설정
1. 소스 코드 관리
    1. Repository URL: 프로젝트 다운로드 URL 입력 (예: https://github.com/rerewww/jerry.git)
    2. Credentials Add -> Jenkins(default) -> Kind: Username with password 선택
    3. Github용 Username, Password 입력
    4. ID, Description에서 생성할 키의 ID와 설명 입력
![예제3]({{ "/assets/images/20190601-2/example3.png"}})
2. Build
    1. Root POM: pom.xml파일이 프로젝트 루트가 아닌 다른 위치에 있다면 수정
    2. Goals and options: mvn options 예) clean compile
![예제4]({{ "/assets/images/20190601-2/example4.png"}})
3. 저장
4. 생성된 Job에서 **Build Now** 클릭 후 빌드 시작
![예제5]({{ "/assets/images/20190601-2/example5.png"}})


---
title: "Jenkins JDK, Maven 설정"
date: 2019-06-01
categories: jenkins
comments: true
---


>Jenins Guide 02   
Setting JDK or Maven on Jenkins

Jenkins에서 JDK와 Maven 설정 가이드(Windows기반)입니다.

## Step 1:JDK 설치
1. [JDK8 다운로드](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) Windows용 설치파일을 다운로드
2. 다운로드한 파일을 실행하여 설치
3. 제어판 -> 시스템 -> 고급 시스템 설정 -> 환경변수 이동
4. JAVA_HOME 경로 확인

## Step 2: Maven 설치
1. [Maven 3.6.1 다운로드](https://maven.apache.org/download.cgi) Binary zip파일을 다운로드
2. 원하는 곳에 압축을 풉니다.
3. 제어판 -> 시스템 -> 고급 시스템 설정 -> 환경변수 이동
4. Path 값 편집 -> 'Maven 설치된 디렉토리\bin' 확인
    - C:\apache-maven-3.6.0-bin\apache-maven-3.6.0\bin
5. 콘솔창을 열어 ```mvn``` 실행이 되는지 확인

## Step 3: Jenkins JDK, Maven 연동
1. 설치한 Jenkins 페이지 접속
2. 좌측 메뉴 **Jenkins 관리** 클릭
3. Global Tool Configuration메뉴 클릭

### Step 3.1: JDK 연동
1. JDK installations... 클릭
![예제1]({{ "/assets/images/20190601-1/example1.png"}})
- Name=일반적으로 JDK버전 입력
- JAVA_HOME=시스템 환경변수의 JAVA_HOME 값
2. Apply 클릭

### Step 3.1: JDK 연동
1. Maven installations... 클릭
![예제2]({{ "/assets/images/20190601-1/example2.png"}})
- Name=일반적으로 JDK버전 입력
- MAVEN_HOME=Maven이 설치된 경로
2. Apply 클릭

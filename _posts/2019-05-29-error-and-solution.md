---
title: "스프링MVC 기반의 JSP파일에서 JS파일을 찾을 수 없는 오류"
date: 2019-05-29
categories: spring
comments: true
---


## 오류
> org.springframework.web.servlet.DispatcherServlet.noHandlerFound No mapping for GET /dist/build.js  
Not Detecting JS file in Spring MVC based JSP file

![예제1]({{ "/assets/images/20190529/example1.png"}})
```
<html>
  <head>
    <script type="text/javascript" charset="utf-8" src="/dist/build.js"></script>
  </head>
  <body></body>
</html>
```
- webpack으로 빌드된 스크립트(/dist/build.js)를 .jsp에서 사용하고 있습니다.
- dist 디렉토리의 경로를 찾을 수 없어서 발생한 오류입니다.

## 해결방법
위치 : dispatcher-servlet.xml

```<mvc:resources mapping="/dist/**" location="/dist/"/>``` 

사용할 리소스 디렉토리 경로를 위와 같이 수정합니다.

## 참고
디렉토리 구조가 다를 수 있으므로, 경로를 확인해주세요.


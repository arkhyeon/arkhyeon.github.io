---
layout: single
title: "Spring & Spring Boot + YML"
excerpt: "YAML Ain't Markup Language[YAML은 마크업 언어가 아니다]"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, YML]

toc: true
toc_sticky: true
 
date: 2022-03-03
last_modified_at: 2022-03-03
---

# Spring & Spring Boot + YML

```

1. 간편한 설정
2. 편리한 의존성 관리 / 자동 권장 버전 관리
3. 내장 서버로 인한 간단한 배포 서버 구축
4. 다른 스프링 프레임워크 요소를 쉽게 사용 [Spring Security, Data JPA...]

```
 - 개발자들의 겨울이 끝났다 > Spring > 조금 더 봄 > Spring Boot
 - 쉽게 단독적이고 상용화 수준의 스프링 기반 애플리케이션을 만들 수 있다.


 - 모든 dependency(의존)를 버전까지 정확하게 기입  
  \> 버전 관리도 권장 버전으로 자동 설정 + Gradle 사용 시 더 짧은 dependency
 - configuration(설정)도 길다  
  \> 간단하게 application.properties에 설정가능  
  \> application.yml(YAML Ain't Markup Language[YAML은 마크업 언어가 아니다])에 뎁스로 설정해 가독성 높임
  ![YML](https://miro.medium.com/max/700/1*fDreWkSTvQwIXZnRKmaX6g.png)
 - 서버 구동 시간 절반 가까이 단축(Tomcat에서 간단하게 jetty로 바꾸기 가능)
 - 내장 서블릿 컨테이너 덕분에 jar 파일로 간단 배포


```

>[우아한 테크 Nick.](https://www.youtube.com/watch?v=6h9qmKWK6Io)
---

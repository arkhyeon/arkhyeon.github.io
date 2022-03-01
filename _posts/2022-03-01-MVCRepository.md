---
layout: single
title: "MVC, Repository"
excerpt: "View <> Controller <> Service <> DAO <> DB / View <> Controller <> Service <> Repository"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, MVC, Repository]

toc: true
toc_sticky: true
 
date: 2022-03-01
last_modified_at: 2022-03-01
---

# MVC, Repository

1. [MVC, Repository](#MVC,-Repository)

```

1. Controller
사용자 요청 받고 Service 처리된 내용을 View에 넘김

2. Model
Controller, Service, DAO, Repository... 데이터를 주고 받을 때 사용하는 객체

3. Service
받은 데이터로 비즈니스 로직 수행

4. DAO
Data Access Object   
DB를 사용해 데이터 조회, 조작 기능 전담 오브젝트

5. Repository
 - 데이터 베이스와 데이터를 주고 받기 위한
 - 인터페이스 JPA에서 Repository 인터페이스 생성 후 JPARepository 상속 시 기본적인 CRUD 자동 생성
 - Entity에 의해 생성된 DB에 접근하는 메서드 들을 사용하기 위한 인터페이스
 - Java Persistence API

6. Cycle
View <> Controller <> Service <> DAO <> DB  
View <> Controller <> Service <> Repository

```

>[Repository와 Dao의 차이점. (bperhaps Tisotry)](https://bperhaps.tistory.com/entry/Repository%EC%99%80-Dao%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)
---

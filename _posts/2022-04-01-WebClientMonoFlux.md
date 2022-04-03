---
layout: single
title: "WebClient(Http Client) / Mono, Flux"
excerpt: "WebClient / Mono / Flux"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, WebClient, Mono, Flux]

toc: trues
toc_sticky: true
 
date: 2022-04-01
last_modified_at: 2022-04-01
---

# WebClient feat.Naver Open Api
1. API 호출 Http Client 모듈
2. RestTemplate은 Blocking방식이고, WebClient는 Non-Blocking방식
 - Blocking : 요청하고 응답 올때까지 기다리는 방식
 - Non-Blocking : 요청 후 응답신호가 오면 그 때 결과 처리
 - 동기/비동기 : Blocking, Non-Blocking 차이
   - 호출되는 함수가 바로 리턴하는지 : 호출되는 함수의 작업 완료 여부를 누가 신경쓰는지
3. 요청자와 제공자 사이의 통신을 좀 더 효율적인 Non-Blocking방식으로 하기 위해서입니다.

4. Flux / Mono
 - Flux : 0 ~ N 개의 데이터를 전달
 - Mono : 0 ~ 1 개의 데이터를 전달
 - 보통 여러 스트림을 하나의 결과는 Mono,   
   각각의 Mono를 합쳐서 하나의 여러 값을 처리할 떄 Flux
 - Mono/Flux는 Publisher 인터페이스를 구현해서 만듦
 - 하나의 결과를 List에 담지 않기에 Mono, Flux 존재

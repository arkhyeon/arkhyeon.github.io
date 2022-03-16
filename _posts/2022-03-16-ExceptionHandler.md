---
layout: single
title: "Spring Exception Handler"
excerpt: "@RestControllerAdvice, @ExceptionHandler"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, Exception Handler]

toc: trues
toc_sticky: true
 
date: 2022-03-16
last_modified_at: 2022-03-16
---

# Exception Handler

1. 에러 시 나오는 문장 수정
 - 400 Bad Request
  \> default message [비어 있을 수 없습니다]]

2. @RestControllerAdvice(Global 설정)
 - 내부에 @ExceptionHandler 설정
 - 예외 캐치 후 핸들링 기능 수행
 - @ResponseBody 통해 객체 리턴
 - @RestControllerAdvice("com.example.demo.login.controller")  
  \> 패키지 단위 핸들링

3. @ExceptionHandler(Rest/Controller 설정)
 - @ExceptionHandler(value = [원하는 Exception Class 설정])
 - Global로 지정 시에도 Controller에 지정한 ExceptionHandler 우선 순위

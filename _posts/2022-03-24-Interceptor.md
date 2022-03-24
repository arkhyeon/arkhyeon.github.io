---
layout: single
title: "Interceptor"
excerpt: "Interceptor(인증) / Filter(로그)와 유사"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, Interceptor, RequiredArgsConstructor]

toc: trues
toc_sticky: true
 
date: 2022-03-24
last_modified_at: 2022-03-24
---

# Interceptor

 - Interceptor(인증) / Filter(로그) 매우 유사
 - Spring Context(Bean 활용 및 추가적인 기능 제공)에 등록
 - AOP와 유사한 기능(로직 기준 핵심적 관점, 부가적 관점으로 나누어 그 관점 기준 각각 모듈화)
 - 선/후 처리 함으로 써 비지니스 로직과 분리한다.
1. @RequiredArgsConstructor(생성자 주입)
    - 초기화 되지않은 final 필드, @NonNull 필드에 생성자 생성(의존성 주입)
    - 순환 참조 방지를 위해 @Autowired(필드 주입) 대신 사용
    - 생정자 주입 : 먼저 빈을 생성하지 않고 주입하려는 빈을 먼저 찾음
2. @Retention 어느 시점까지 어노테이션의 메모리를 가져갈 지 설정  
   @Target 필드, 메소드, 클래스, 파라미터 등 선언할 수 있는 타입을 설정

3. CustomException 작성

    - Interceptor 에 throw new CustomException 작성

    - GlobalExceptionHandler @ControllerAdvice는, @ExceptionHandler(CustomException.class) 작성

4. @ExceptionHandler
    - @Controller, @RestController 적용된 Bean 내 발생 예외를 하나의 메서드에서 처리
5. @ControllerAdvice
    - 전역 발생 예외 처리

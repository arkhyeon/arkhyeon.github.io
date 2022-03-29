---
layout: single
title: "RestTemplate"
excerpt: "get / post / exchange"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, RestTemplate, generic]

toc: trues
toc_sticky: true
 
date: 2022-03-29
last_modified_at: 2022-03-29
---

# RestTemplate 사용
 - Client / Server 통신
 - 스프링에서 제공하는 http 통신에 유용하게 쓸 수 있는 템플릿

1. UriComponentsBuilder  
                .fromUriString("http://localhost:9090")  
                .path("/api/server/hello") 
                .encode()  
                .queryParam("name", "aaaa")  
                .queryParam("age", 99)  
                .build()  
                .toUri();  
                

2. ResponseEntity<UserResponse> result = restTemplate.getForEntity(uri, UserResponse.class);
 - 반환 타입 result = restTemplate.반환 타입
 
 getForObject / GET /    
 주어진 URL 주소로 HTTP GET 메서드로 객체로 결과 반환
 
 getForEntity / GET  
 주어진 URL 주소로 HTTP GET 메서드로 결과는 ResponseEntity 반환
 
 postForLocation / POST
 POST 요청을 보내고 결과로 헤더에 저장된 URI를 결과 반환
 
 postForObject / POST
 POST 요청을 보내고 객체로 결과 반환
 
 postForEntity / POST  
 POST 요청을 보내고 결과로 ResponseEntity 반환
 
 delete / DELETE  
 주어진 URL 주소로 HTTP DELETE 메서드 실행
 
 headForHeaders / HEADER  
 헤더의 모든 정보를 얻을 수 있으면 HTTP HEAD 메서드 사용
 
 put / PUT  
 주어진 URL 주소로 HTTP PUT 메서드 실행
 
 patchForObject / PATCH  
 주어진 URL 주소로 HTTP PATCH 메서드 실행
 
 optionsForAllow / OPTIONS  
 주어진 URL 주소에서 지원하는 HTTP 메서드 조회
 
 exchange / any  
 HTTP 헤더를 새로 만들 수 있고 어떤 HTTP 메서드도 사용 가능
 
 execute / any  
 Request/Response 콜백을 수정 가능

 
 - EXCHANGE
 
 - HTTP 헤더를 새로 만들 수 있고 어떤 HTTP 메서드도 사용 가능
 - 지정된 URI 템플릿에 대해 HTTP 메서드를 실행하여 지정된 요청 엔터티를 요청에 쓰고 응답을 ResponseEntity 반환 
 - URI 템플릿 변수는 주어진 URI 변수가 있는 경우 이를 사용하여 확장
 
 1. Generic Type
  - 데이터 타입 일반화
  - 클래스/메소드에서 사용할 내부 데이터 타입을 컴파일 시 미리 지정
  - 코드 작성 후 코드를 다양한 타입의 객체에 대하여 재사용하는 프로그래밍 기법
  - 클래스에서 사용할 타입을 클래스 외부에서 설정하는 타입
  - 클래스/메소드 내부에서 사용되는 객체의 타입 안정성
  - 반환값에 대한 타입 변환 및 타입 검사에 들어가는 노력을 줄임
  
 2. ParameterizedTypeReference
  - generic 타입으로 응답
  
 3. HttpEntity 이후 response 응답 못받음.
  - 이미 사용했기에

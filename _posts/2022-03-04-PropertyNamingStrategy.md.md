---
layout: single
title: "PropertyNamingStrategy >> PropertyNamingStrategies"
excerpt: "교착상태 발생 버그로 PropertyNamingStrategy 아래 모든 클래스 사용 중지"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, JsonNaming, SnakeCaseStrategy, PropertyNamingStrategies]

toc: true
toc_sticky: true
 
date: 2022-03-04
last_modified_at: 2022-03-04
---

# JsonNaming[버그 수정]

```
 - 응답 받은 객체의 키의 값의 네이밍을 정할 수 있음.  
```

1. @JsonNaming(PropertyNamingStrategy.SnakeCaseStrategy.class)  
   \> @JsonNaming(PropertyNamingStrategies.SnakeCaseStrategy.class)  
    class initialization depends on its subclass, this can lead to class loading deadlock.  

    [[PropertyNamingStrategy Issues] - 2020-05-09](https://github.com/FasterXML/jackson-databind/issues/2715) 

    교착상태 발생 버그로 PropertyNamingStrategy 아래 모든 클래스 사용 중지  
    따라서 PropertyNamingStrategies 인스턴스용 컨테이너 추가(취소선 발생 X)   


    Container for standard PropertyNamingStrategy implementations and singleton instances.
    Added in Jackson 2.12 to resolve issue databind#2715.

    [[PropertyNamingStrategies OverView]](http://fasterxml.github.io/jackson-databind/javadoc/2.13/com/fasterxml/jackson/databind/PropertyNamingStrategies.html)


---
layout: single
title: "String, StringBuffer, StringBuilder"
excerpt: "성능 우선
 StringBuilder  >  StringBuffer  >>>  String 

 1. 단순 조회 : String
 2. Multi Thread : StringBuffer(안전) + 잦은 수정
 3. Single Thread : StringBuilder(빠름) + 잦은 수정"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, String, StringBuffer, StringBuilder]

toc: true
toc_sticky: true
 
date: 2022-03-07
last_modified_at: 2022-03-07
---

# JsonNaming[버그 수정]

```
 성능 우선
 StringBuilder  >  StringBuffer  >>>  String 

 1. 단순 조회 : String
 2. Multi Thread : StringBuffer(안전) + 잦은 수정
 3. Single Thread : StringBuilder(빠름) + 잦은 수정
```

1. String  
 [단점]  
 \-  객체 내부 데이터 수정 불가능으로 새로운 객체를 생성  
 \> 수정을 거듭할수록 객체 수 증가로 인한 성능 저하 야기  
 [장점]  
 \- Buffer, Builder 보다 초기 리소스 적으며 크기 고정으로 단순 조회 연산이 빠르다.  
 \- 불변성을 가지기 때문에 Multi Thread 환경에서 안전(StringBuffer와 동일)
 
2. StringBuffer  
 \- 동기화 지원으로 Multi Thread 환경에서 안전  
 \- ConcurrentModificationException 방지  
 (Multi Thread 환경 다른 Thread가 순회하는 객체를 수정)

3. StringBuilder  
 \- 동기화 미지원으로 Multi Thread 비적합  
 \- 동기화 고려하지 않는 만큼 Single Thread에서의 성능은 StringBuffer보다 좋다

4. Multi Thread / Single Thread  
 \- 나머지는 for문 만번 돌려보자

 ```java

 //Multi Thread 환경
 public class Test{
    StringBuffer b;

    public Test(){
        b = new StringBuffer();
    }

    public String someMethod(){
        b.append("Some Method");
        return(b.toString());
    }
}

 ```


[[StringBuffer and Multithreading] ](https://stackoverflow.com/questions/14556250/stringbuffer-and-multithreading) 

   [[java.lang Class StringBuffer OverView]](https://docs.oracle.com/javase/7/docs/api/java/lang/StringBuffer.html)


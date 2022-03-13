---
layout: single
title: "Object Mapper"
excerpt: "Jackson JsonNode ObjectNode ArrayNode"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, Jackson, JsonNode, ObjectNode, ArrayNode]

toc: trues
toc_sticky: true
 
date: 2022-03-13
last_modified_at: 2022-03-13
---

# Object Mapper

1. Jackson(Java 라이브러리)  
 Json > Java Object 변환  
 Java Object > Json 변환 
 
2. Json Node
 - Key : Value / 값 변경 불가
 - Key 값을 통해 값을 가져옴

3. ObjectNode
 - Key : Value / 값 변경 가능
 
4. ArrayNode
 - [value1, value2, ...] / 값 변경 가능
 
5. Getter
 - 기본
 ```
 String _name = jsonNode.get("name").asText();
 ```
 - List
 ```
 JsonNode cars = jsonNode.get("cars");
           ArrayNode an = (ArrayNode)cars;
   
           List<Car> _cars = om.convertValue(an, new TypeReference<List<Car>>() {});
 ```
           
 6. Setter
 ```
 ObjectNode on = (ObjectNode) jsonNode;
         on.put("name", "steve");
         on.put("age", 20);
 ```
         
 7. Json Data 출력
 ```
 ObjectNode.toPrettyString()
 ```


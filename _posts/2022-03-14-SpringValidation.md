---
layout: single
title: "Spring Validation"
excerpt: "Spring Validation Type"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, Spring Validation]

toc: trues
toc_sticky: true
 
date: 2022-03-14
last_modified_at: 2022-03-14
---

# Spring Validation

- spring-boot-starter-validation

1. Validation
 - @Size                : 문자 길이 측정(int 불가)
 - @NotNull             : null 불가
 - @NotEmpty            : null, 공백 불가
 - @NotBlank            : null, 공백, " "(빈값) 불가
 - @Past                : 과거 날짜
 - @PastOrPresent       : 오늘, 과거
 - @Future              : 미래
 - @FutureOrPresent     : 오늘, 미래
 - @Pattern             : 정규식 검증
 - @Max                 : 최대값
 - @Min                 : 최소값
 - @??(regexp = "정규식", message = "오류 메세지")
 - @AssertTrue / False  : 별도 Logic 적용
 ```
    @AssertTrue(message = "yyyyMM형식에 맞지 않습니다") // return true면 정상 false면 비정상
    public boolean isReqYearMonthValidation() {
        try {
            LocalDate localDate = LocalDate.parse(getReqYearMonth()+"01", DateTimeFormatter.ofPattern("yyyyMMdd"));
        }catch (Exception e){
            return false;
        }


        return  true;
    }
```
 - @Valid               : 해당 Object Validation 실행 정의
    - public Object user(@Valid @RequestBody User user){


- 해당 오류 Return
```
BindingResult 사용 
filed.getFiled 어디서 오류? 
objectError.getDefaultMessage() 오류메세지

public Object user(@Valid @RequestBody User user, BindingResult br){

        if(br.hasErrors()){
            StringBuilder sb = new StringBuilder();
            br.getAllErrors().forEach(objectError -> {
                FieldError field = (FieldError) objectError;
                String msg = objectError.getDefaultMessage();
                System.out.println(field.getField());
                System.out.println(msg);

                sb.append("filed : " + field.getField());
                sb.append("msg : " + msg);

            });

            return ResponseEntity.status(HttpStatus.BAD_REQUEST).body(sb.toString());
        }
}

```

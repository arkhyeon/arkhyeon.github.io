---
layout: single
title: "Maven & Gradle"
excerpt: "빌드 관리 도구 / 사용성, 성능 차이 / Gradle이 Maven보다 나중에 나오며 단점 보완 / Gradle 사용 가능한 환경에서 굳이 Maven 선택할 이유 X"

categories:
  - SpringBoot
tags:
  - [Spring, SpringBoot, Gradle, Maven, Ant, BuildTool]

toc: true
toc_sticky: true
 
date: 2022-02-26
last_modified_at: 2022-02-26
---

# Maven & Gradle
```
1. 빌드 관리 도구
2. 사용성, 성능 차이
3. Gradle이 Maven보다 나중에 나오며 단점 보완
 >>> Gradle 사용 가능한 환경에서 굳이 Maven 선택할 이유 X
```

## 빌드 관리 도구
```
- 프로젝트 내 필요 xml, properties, jar 파일들을 자동 인식 후 빌드해주는 도구
- 소스 코드 컴파일, 테스트 정적 분석 등을 하여 실행 가능한 앱으로 빌드
- 프로젝트 정보 관리, 테스트 빌드, 배포등의 작업 진행
- 외부 라이브러리 참조 자동 다운로드 / 업데이트 관리
```
- 이전에는 수동 다운로드, 버전 관리까지 직접했음

## Maven
```
- 자바의 대표 관리 도구 Ant 대체하기 위해 개발
- 프로젝트의 외부 라이브러리를 쉽게 참조하기 위해 pom.xml 파일로 명시하여 관리
- 참조한 외부 라이브러리에 연관된 다른 라이브러리도 자동 관리

- Ant는 빌드의 기능만 가지고 있으나 메이븐은 자동 라이브러리 관리 기능 추가
- 다운받아 사용하던 라이브러리에 변동 사항이 있으면 자동 업데이트 후 적용
```
## Gradle
```
- Groovy 스크립트 활용 빌드 관리 도구
- 멀티 프로젝트의 빌드에 최적화 설계
- 메이븐에 비해 더 빠른 처리속도('최대' 100배)
- xml 형태 상 열린태그, 닫힌태그, 위상에 대한 정렬이 없기에 간결한 구성
```

## 장점
```
1. Gradle에 비해 Maven의 성능이 떨어짐
2. 대규모 프로젝트에서의 성능이 좋음
 - 빌드단계에서 그래들은 이미 빌드가 되어있고 변경된 사항이 없으면 패스하기에 처리속도가 빠르다.
3. 설치 없이 사용 가능

`이미 설정된 Maven 셋팅을 Gradle로 바꾸기에는 공수가 들기에 아직 실무는 Maven 점유율이 좋다.`
```
#
build.gradle(Gradle)
```
plugins {
    id 'org.springframework.boot' version '2.4.2'
    id 'io.spring.dependency-management' version  '1.0.11.RELEASE'
    id 'java'
}

group 'org.example'
version '1.0-SNAPSHOT'

//라이브러리가 저장된 위치(라이브러리 참조 위해)
repositories {
    //기본 Maven Repository(사내 넥서스 및 url들을 통해 추가 가능)
    //https://mvnrepository.com/
    mavenCentral()
}

//사용하고자 하는 외부 라이브러리 의존성 설정
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-data-rest'
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'

    runtimeOnly 'com.h2database:h2'

    compileOnly 'org.projectlombok:lombok:1.18.22'
    annotationProcessor 'org.projectlombok:lombok:1.18.22'
}

test {
    useJUnitPlatform()
}
```

pom.xml(Maven)
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.kh</groupId>
	<artifactId>im</artifactId>
	<name>im</name>
	<packaging>war</packaging>
	<version>1.0.0-BUILD-SNAPSHOT</version>
	<properties>
		<java-version>1.8</java-version>
		<org.springframework-version>5.1.5.RELEASE</org.springframework-version>
		<org.springframework.security-version>5.1.5.RELEASE</org.springframework.security-version>
		<org.aspectj-version>1.6.10</org.aspectj-version>
		<org.slf4j-version>1.6.6</org.slf4j-version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context</artifactId>
			<version>${org.springframework-version}</version>
			<exclusions>
				<!-- Exclude Commons Logging in favor of SLF4j -->
				<exclusion>
					<groupId>commons-logging</groupId>
					<artifactId>commons-logging</artifactId>
				 </exclusion>
			</exclusions>
		</dependency>
	</dependencies>        
    <build>
        <plugins>
            <plugin>
                <artifactId>maven-eclipse-plugin</artifactId>
                <version>2.9</version>
                <configuration>
                    <additionalProjectnatures>
                        <projectnature>org.springframework.ide.eclipse.core.springnature</projectnature>
                    </additionalProjectnatures>
                    <additionalBuildcommands>
                        <buildcommand>org.springframework.ide.eclipse.core.springbuilder</buildcommand>
                    </additionalBuildcommands>
                    <downloadSources>true</downloadSources>
                    <downloadJavadocs>true</downloadJavadocs>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>

```

[출처] https://www.youtube.com/watch?v=3Jp9kGDb01g


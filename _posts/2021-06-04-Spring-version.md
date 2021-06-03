---
title: "[Spring] Spring Version Update 내용 정리"
date: 2021-06-04 00:52:00 -0500
categories: [Spring]
tags: [Spring]
---

현재 날짜(21.06.04) 기준 Spring 최신 버전 : `5.3.7`  

## 프로젝트에서 Spring version 확인 방법  
* pom.xml에서 확인 가능 (사진의 프로젝트는 `5.2.4` 버전)  
![캡처](https://user-images.githubusercontent.com/50273050/120434572-9ae40b80-c3b7-11eb-95a2-c2fb2884f574.JPG)

### 잠깐! 소프트웨어 버전 규칙  
- 버전 형식 : `X.Y.Z`  
`X` : 주 버전. 기존 버전과 호환되지 않게 API가 바뀐 경우  
`Y` : 부 버전. 기존 버전과 호환되면서 새로운 기능을 추가한 경우  
`Z` : 수 버전. 기존 버전과 호환되면서 버그를 수정한 경우  

## Spring Framework 5.0 Update 내용

자세하고 정확한 사항은 아래 링크에 상세하게 적혀있다.  
https://springframework.guru/what-is-new-with-spring-framework-5/   
아래 링크를 참고해도 좋음.   
https://velog.io/@hygoogi/%EC%8A%A4%ED%94%84%EB%A7%81-%EB%B2%84%EC%A0%84-%EB%B3%84-%ED%8A%B9%EC%A7%95  

### JDK Baseline Update | JDK 기준 업데이트  
- `The entire Spring framework 5.0 codebase runs on Java 8. Therefore, Java 8 is the minimum requirement to work on Spring Framework 5.0`  
 **Java 8이 기본**으로 사용되고, 최소 요구사항. => Generic과 Lambda 사용 가능!
 
### Core Framework Revision | 핵심 프레임워크 개정  
- `Based on Java 8 reflection enhancements, method parameters in Spring Framework 5.0 can be efficiently accessed.`  
 Java 8을 기반으로 Spring Framework 5.0의 메소드 매개 변수에 효율적으로 액세스할 수 있음.  
 
- `Core Spring interfaces now provide selective declarations built on Java 8 default methods.`  
 핵심 스프링 인터페이스들이 Java 8의 기본 메소드 기반의 선택적 정의를 제공함. (?)  
 
- `@Nullable and @NotNull annotations to explicitly mark nullable arguments and return values.`  
 `@Nullable`과 `@NotNull` 어노테이션을 널이 될 변수값이나 반환값에 명시적으로 표기할 수 있음.  
  So, runtime에 NullPointerException을 던지지 않고, **컴파일 시간에 널 값을 다룰 수 있게 됨.**  
  
- `On the logging front, Spring Framework 5.0 comes out of the box with Commons Logging bridge module, named spring-jcl`  
 `spring-jcl`이라는 공통 로깅 브릿지 모듈 추가. (?)
 
### Core Container Updates | 핵심 컨테이너 업데이트  
- 후보 컴포넌트 인덱스 기능 추가(classpath 기반의 component 스캔을 대체할 수 있음)
 
### Fuctional Programming with Kotlin | Kotiln 지원

### Reactive Programming Model | 반응형 프로그래밍 모델   

### Testing Improvements  
- JUnit5의 Jupiter 지원  
- TestContext Framework를 통한 병렬 테스트 실행  
- Reactive Programming Model을 위해 spring-test에 WebTestClient 포함 (Spring WebFlux 지원)  

## Ref  
https://m.blog.naver.com/whdgml1996/222001483936  

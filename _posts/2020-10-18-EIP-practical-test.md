---
title: "2020 정보처리기사 3회 실기시험 문제 가답안"
date: 2020-10-18 01:00:00 -0400
categories: [자격증, 정보처리기사]
tags: [정보처리기사]
--- 

총평 : 충격과 혼돈의 도가니 + 짜증  

## 문제
#### 1. 리팩토링의 목적을 서술하시오.  
작성한 답 : 개발 비용과 시간을 단축하여 효율적인 개발을 하기 위해서이다.  
모범답안 : 코드의 외부 행위는 바꾸지 않고 내부 구조를 개선시켜 소프트웨어를 보다 이해하기 쉽고, 수정하기 쉽도록 만드는 것  


#### 2. C언어 출력 결과를 쓰시오.
```java  
int main() {
	int i, c = 0;
	while (i < 10) {
		i++;
		c *= i;
	}
	printf("%d", c);
}
```
작성한 답 : 0  
**정답! Correct~**  


#### 3. 다음 요구사항에 맞게 SQL 명령어를 작성하시오.
\- 학생 테이블에서 이름(속성명)이 민수인 튜플을 삭제
\- ; 생략 가능
\- 대소문자 구분안함  
작성한 답 : DELETE FROM 학생 WHERE 이름 = '민수';  
**정답! Correct~**  


#### 4. 심리학자 톰 마릴은 컴퓨터가 메시지를 전달하고, 메시지가 제대로 도착했는지 확인하며, 도착하지 않았을 경우 메시지가 재전송하는 일련의 방법을 가리켜 '기술적 은어'라는 뜻으로 ()이라 불렀다.  
작성한 답 : Technical Word (?..찍음)  
모범답안 : 프로토콜  


#### 5. 헝가리안 표기법에 대해 서술하시오.  
작성한 답 : 변수를 명명할 때 변수의 맨 앞에 타입을 알 수 있도록 표기하는 기법이다.  
모범답안 : 컴퓨터 프로그래밍에서 변수 및 함수의 이름 인자 앞에 데이터 타입을 명시하는 코딩 규칙  


#### 6. 다음 설명에 맞는 용어를 쓰시오.  
\- 대표적인 내부 라우팅 프로토콜  
\- 대규모 네트워크에 적합  
\- 링크 상태 라우팅 프로토콜   
작성한 답 : OSPF  
**정답! Correct~**  


#### 7. UI 설계 원칙 중 직관성에 대해 서술하시오.  
작성한 답 : 누구나 쉽고 빠르게 이해할 수 있는 것을 의미한다.  
모범답안 : 누구나 쉽게 이해하고 사용할 수 있어야 한다.  


#### 8. C++에서 생성자의 의미를 서술하시오.  
작성한 답 : 객체를 생성할 때 사용하는 메소드이다.  
모범답안 : 객체 생성 시 초기화 작업을 위한 함수로써, 객체를 생성할 때 반드시 호출되고, 제일 먼저 실행된다.  


#### 9. 형상 통제에 대해 서술하시오.  
작성한 답 : 개발의 전 단계에 걸쳐 변화하는 데이터를 통제하는 것을 의미한다.  
모범답안 : 산출물의 변경 사항을 버전별로 관리하여 목표 시스템의 품질 향상을 지원하는 활동  


#### 10. IP는 오류를 제어하거나 .. 하는 기능이 없다. TCP/IP에서는 이러한 신뢰성 없는 IP를 대신하여 송신측으로 네트워크의 IP 상태 및 에러 메시지를 전달해주는 프로토콜은?  
작성한 답 : EBP (?..찍음)  
모범답안 : ICMP  


#### 11. EAI 구축 유형 중 Message Bus와 Hybrid를 제외한 나머지 두 유형은?  
작성한 답 : (1) Point-to-Point (2) Hub & Spoke  
**정답! Correct~**  (PPP == Point to Point)  
(문제에 답이 나와있었음;)


#### 12. 데이터베이스에서 스키마(Schema)에 대해 서술하시오.  
작성한 답 : 테이블의 이름, 속성 등 데이터베이스의 전반적인 구조를 설계한 것을 의미한다.  
모범답안 : 데이터베이스의 구조와 제약조건에 대한 명세를 기술한 것  


#### 13. 다음 그림을 분기 커버리지 과정으로 테스트 케이스를 작성하시오.
작성한 답 : 
(1) 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7   
(2) 1 -> 2 -> 4-> 5 -> 6 -> 1   
**정답! Correct~**  


#### 14. 두 개의 릴레이션 A와 B가 있을 때 B의 릴레이션의 모든 조건을 만족하는 경우의 튜플들을 릴레이션 A에서 분리해 내어 프로젝션 하는 연산자의 기호를 쓰시오.  
작성한 답 : % (나누기 기호)   
**정답! Correct~**  


#### 15. 다음 요구사항에 맞게 SQL 명령어를 작성하시오.  
\- 성적 테이블에서 과목별 점수의 평균이 90이상인 과목의 최소점수와 최대점수를 구하시오  
\- WHERE 절 사용 금지  
\- GROUP BY, HAVING 절 사용하기  
\- 집계함수 사용하기   
\- AS(alias) 사용하기  
작성한 답 : 
```sql
  SELECT 과목이름, min(과목이름) AS 최소점수, max(과목이름) AS 최대점수
	FROM 성적  
	GROUP BY 과목이름
	HAVING AVG(과목이름) >= 90;
```
(왜.. 점수를 과목이름으로 적었을까....?)  
모범답안 : 
```sql
  SELECT 과목이름, min(점수) AS 최소점수, max(점수) AS 최대점수
	FROM 성적  
	GROUP BY 과목이름
	HAVING AVG(점수) >= 90;
```


#### 16. 동치 분할 테스트, 경계값 분석 테스트 등 내부 구조를 보지 않고 하는 테스트 기법은?
작성한 답 : 블랙박스 테스트 기법  
모범답안 : 블랙박스 테스트   
**정답~ 이겠지?**  


#### 17. C언어 출력 결과를 쓰시오.  
```c
int r1() { return 4; }
int r10() { return 30 + r1(); }
int r100() { return 200 + r10(); }
int main() {
	printf("%d", r100());
	return 0;
}
```
작성한 답 : 234  
**정답! Correct~**  


#### 18. JAVA 출력 결과를 쓰시오.
```java
public class Test{
	public static void main(String[] args) {
		int i = 0;
		int sum = 0;
		do {
			i++;
			if (i % 2 == 1) continue;
			sum += i;
		} while (i < 10)
		System.out.print(sum);
	}
}
```
작성한 답 : 30  
**정답! Correct~**


#### 19. JAVA 출력 결과를 쓰시오.
```java
abstract class Vehicle{
	String name;
	abstract public String getName(String val);
	public String getName() {
		return "Vehicle name: " + name;
	}
}

class Car extends Vehicle {
	public Car(String val) {
		name = super.name = val;
	}
	public String getName(String val) {
		return "Car name: " + val;
	}
	public String getName(byte val[]) {
		return "Car name: " + name;
	}
}

public class Test {	
	public static void main(String[] args) {
		Vehicle obj = new Car("Spark");
		System.out.print(obj.getName());
	}
}
```
작성한 답 : Vehicle name: Spark  
**정답! Correct~**  


#### 20. 다음 요구사항에 맞게 SQL 명령어 빈칸을 채우시오.
- 학생 테이블에 이름은 주소이고 타입은 길이 20의 문자타입으로 속성을 추가    
```sql
(  1  ) TABLE 학생 (  2  ) 주소 VARCHAR(20);  
```
작성한 답 : (1) ALTER (2) ADD  
**정답! Correct~**  

제발 후하게 채점해주시길..  

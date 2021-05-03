---
title: "[코딩테스트] Programmers Level1. 체육복 문제풀이"
date: 2021-05-03 23:00:00 -0400
categories: coding_test
tags: 코딩테스트 코테 programmers 
--- 

https://programmers.co.kr/learn/courses/30/lessons/42862?language=java

## Level1. 체육복  
```
점심시간에 도둑이 들어, 일부 학생이 체육복을 도난당했습니다. 
다행히 여벌 체육복이 있는 학생이 이들에게 체육복을 빌려주려 합니다. 
학생들의 번호는 체격 순으로 매겨져 있어, 바로 앞번호의 학생이나 바로 뒷번호의 학생에게만 체육복을 빌려줄 수 있습니다.
예를 들어, 4번 학생은 3번 학생이나 5번 학생에게만 체육복을 빌려줄 수 있습니다. 
체육복이 없으면 수업을 들을 수 없기 때문에 체육복을 적절히 빌려 최대한 많은 학생이 체육수업을 들어야 합니다.

전체 학생의 수 n, 체육복을 도난당한 학생들의 번호가 담긴 배열 lost, 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열 reserve가 매개변수로 주어질 때, 
체육수업을 들을 수 있는 학생의 최댓값을 return 하도록 solution 함수를 작성해주세요.

* 제한사항
- 전체 학생의 수는 2명 이상 30명 이하입니다.
- 체육복을 도난당한 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌의 체육복을 가져온 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌 체육복이 있는 학생만 다른 학생에게 체육복을 빌려줄 수 있습니다.
- 여벌 체육복을 가져온 학생이 체육복을 도난당했을 수 있습니다. 이때 이 학생은 체육복을 하나만 도난당했다고 가정하며, 남은 체육복이 하나이기에 다른 학생에게는 체육복을 빌려줄 수 없습니다.

```
![image](https://user-images.githubusercontent.com/50273050/116902050-a687c980-ac75-11eb-80cf-e0b873b81cd9.png)  

처음에는 HashMap을 써야겠다 생각함. (안그래도 됨. 과함.)  
지문 내용에 충실해서 체육복 두벌 있는 애들은 2, 한벌은 1, 없으면 0으로 만들어줬다. (뭐가 옳은진 모르겠으나 이렇게 안하면 간략하게 풀이 가능)  
맨 앞, 맨 뒤 학생을 반복문에 포함하기엔 인덱스 문제가 생겨서 따로 빼줬다. (비효율적..)   

## 1차 작성 코드 (겁나 김)  
```java
class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        int answer = 0;
        
        Map<Integer, Integer> student = new HashMap<Integer, Integer>();
		
		// 모든 학생들이 체육복을 갖고 있을 시의 상태
		for (int i = 1; i <= n; i++) {
			student.put(i, 1);
		}
		
		// 체육복을 도난당하고, 여분의 체육복이 추가된 상태 
		for (int stuIdx = 1; stuIdx <= student.size(); stuIdx++) {
			// 도난
			for (int lostIdx = 0; lostIdx < lost.length; lostIdx++) {
				if (stuIdx == lost[lostIdx]) {
					student.put(stuIdx, student.get(stuIdx) - 1);
				}
			}
			// 여분
			for (int reserveIdx = 0; reserveIdx < reserve.length; reserveIdx++) {
				if (stuIdx == reserve[reserveIdx]) {
					student.put(stuIdx, student.get(stuIdx) + 1);
				}
			}
		}
		
		answer = n;
		
		if (student.get(1) == 0) { // 첫번째 학생이 없는 경우
			if (student.get(2) > 1) {
				student.put(2, 1); // 빌려줌
			} else {
				answer--;
			}
		}
		
		for (int i = 2; i < student.size(); i++) {
			if (student.get(i) == 0) { // 체육복 없음
				if (student.get(i - 1) > 1) { // 앞번호 여분 있음
					student.put(i - 1, 1);
				} else if (student.get(i + 1) > 1) { // 뒷번호 여분 있음
					student.put(i + 1, 1);
				} else {
					answer--;
				}
			}
		}
		
		if (student.get(n) == 0) { // 마지막 학생이 없는 경우
			if (student.get(n - 1) > 1) {
				student.put(n - 1, 1); // 빌려줌
			} else {
				answer--;
			}
		}
        
        return answer;
    }
}
```

다른 사람의 풀이를 보니 그냥 배열로 쓰면 됐다.. 학생들의 번호가 순서대로 이기 때문    
또한, 지문 내용 대로 숫자를 안넣고 없으면 -1, 있으면 0, 두 개있으면 1로 설정해줌.    
배열은 new로 선언해줄 때 0으로 자동초기화 된다는 것또한 잊지 말자!  
배열로 위 사항을 참고하여 다시 풀어보았다.  

## 2차 작성 코드 (간결)  
```java
class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        int answer = n;
        int[] student = new int[n + 2]; // 0이 default
		
		for (int l : lost) { // -1
			student[l]--;
		}
		
		for (int r : reserve) { // 1
			student[r]++;
		}
		
		for (int i = 1; i <= n; i++) {
			if (student[i] == -1) { // 체육복 X
				if (student[i - 1] == 1) { // 앞번호 여분
                    student[i - 1]--;
                    student[i]++;
				} else if (student[i + 1] == 1) {
					student[i + 1]--;
                    student[i]++;
				} else {
					answer--;
				}
			}
		}
        return answer;
    }
}
```

배열 크기를 n+2로 설정하여 맨앞과 맨뒤는 비워놓고 하면 다른 사람의 풀이보다 깔끔해진다.  
초반에 잘 생각한 점은, 체육복이 없는 사람을 기준으로 한 것!  

## 다른 사람 풀이
```java
class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        int[] people = new int[n];
        int answer = n;

        for (int l : lost) 
            people[l-1]--;
        for (int r : reserve) 
            people[r-1]++;

        for (int i = 0; i < people.length; i++) {
            if(people[i] == -1) {
                if(i-1>=0 && people[i-1] == 1) {
                    people[i]++;
                    people[i-1]--;
                }else if(i+1< people.length && people[i+1] == 1) {
                    people[i]++;
                    people[i+1]--;
                }else 
                    answer--;
            }
        }
        return answer;
    }
}
```

## Remind  
배열을 new로 선언하면 모두 0으로 초기화된다.  
굳이 지문대로 어렵게 인덱스를 맞출 필요는 없다. 간단하고 깔끔하게 풀 수 있는 방법을 생각하자.  

---
title: "[코딩테스트] Programmers Level1. 완주하지 못한 선수 문제풀이"
date: 2021-04-30 20:00:00 -0400
categories: coding_test
tags: 코딩테스트 코테 programmers 
--- 

https://programmers.co.kr/learn/courses/30/lessons/42576?language=java

## Level1. 완주하지 못한 선수
```
수많은 마라톤 선수들이 마라톤에 참여하였습니다. 
단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 
완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요. 

* 제한사항
- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
- completion의 길이는 participant의 길이보다 1 작습니다.
- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
- 참가자 중에는 동명이인이 있을 수 있습니다.

```

처음에는 for 문을 두 개 써야하나..?(바보) 하고 두 개 썼는데 효율성 부분에서 바로 짤.  
조금 더 생각해보니 정렬을 하고 하나씩 비교하다 틀린거 나오면 반환하면 되는거였음.

## 작성 코드 
```java
import java.util.Arrays;

class Solution {
    public String solution(String[] participant, String[] completion) {
        Arrays.sort(participant);
		Arrays.sort(completion);
        
        for (int i = 0; i < completion.length; i++) {
			if (!participant[i].equals(completion[i])) {
				return participant[i];
			}
		}
        return participant[participant.length - 1];
    }
}
```

다른 사람의 풀이를 보니 HashMap으로 해결이 가능했다.  
HashMap에 참가자의 이름을 key값으로 넣고, value 값을 1씩 추가한다.  
동명이인인 경우가 있으므로 같은 이름이 2번 있을 경우 value가 2가 되는 것!   
이 경우를 위해서 getOrDefault() 메소드를 사용한다.  
completion를 훑으면서 -1씩 해주고 결과적으로 0이 아닌 것(0 이상)이 정답.   

## 다른 사람 풀이
```java
import java.util.HashMap;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        HashMap<String, Integer> hm = new HashMap<>();
        for (String player : participant) hm.put(player, hm.getOrDefault(player, 0) + 1);
        for (String player : completion) hm.put(player, hm.get(player) - 1);

        for (String key : hm.keySet()) {
            if (hm.get(key) != 0){
                answer = key;
            }
        }
        return answer;
    }
}
```

## Remind  
* getOrDefault(Object key, V DefaultValue)  
key : 값을 가져와야 하는 요소의 키입니다.  
defaultValue : 지정된 키로 매핑된 값이 없는 경우 반환되어야 하는 기본값입니다.  
반환 값 : 찾는 key가 존재하면 해당 key에 매핑되어 있는 값을 반환하고, 그렇지 않으면 디폴트 값이 반환됩니다.  


## Ref
https://junghn.tistory.com/entry/JAVA-Map-getOrDefault-이란-사용법-및-예제 [코딩 시그널]

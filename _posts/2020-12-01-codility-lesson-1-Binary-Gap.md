---
title: "[코딩테스트] Codility Lesson 1. Binary Gap 문제풀이"
date: 2020-12-01 21:41:00 -0400
categories: coding_test
tags: 코딩테스트 코테 codility lesson 1
--- 

오랜만에 코딩테스트 공부를 하게 되었다.  
Codility Lesson에 있는 무료 문제들을 풀어볼 예정이다.  
오늘이 그 첫 시작이다. 첫 번째 문제를 보자.  

## Lesson.1 Binary Gap
Find longest sequence of zeros in binary representation of an integer.  
```
A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps. The number 32 has binary representation 100000 and has no binary gaps.

Write a function:

class Solution { public int solution(int N); }

that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.

For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5. Given N = 32 the function should return 0, because N has binary representation '100000' and thus no binary gaps.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..2,147,483,647].
Copyright 2009–2020 by Codility Limited. All Rights Reserved. Unauthorized copying, publication or disclosure prohibited.
```

시작부터 난관이다. 문제가 영어야..? (당황)
너무 당황해서 번역기를 돌렸다. (네이버 파파고야 고마워)  

```
양의 정수 N 내의 2진수 간격은 N의 2진수 표현에서 양쪽 끝의 1로 둘러싸인 연속 0의 최대 시퀀스다.

예를 들어, 숫자 9는 이진 표현 1001을 가지며 길이 2의 이진 갭을 포함한다. 숫자 529는 이진 표현 1000010001을 가지며, 길이 4와 길이 3의 두 개의 이진 갭을 포함한다. 숫자 20은 이진 표현 10100을 가지고 있고 길이 1의 이진 갭을 1개 포함하고 있다. 숫자 15는 이진 표현 1111을 가지며 이진 간격이 없다. 숫자 32는 이진 표현 10,000을 가지고 있고 이진 간격이 없다.

함수 쓰기:

클래스 솔루션 { 공용 int 솔루션(N); }

양의 정수 N이 주어진 경우 가장 긴 이진 간격의 길이를 반환한다. N에 이진 갭이 없으면 함수는 0을 반환해야 한다.

예를 들어, N은 이진 표현 10000010001을 가지며 따라서 가장 긴 이진 간격이 길이 5이기 때문에 N = 1041을 주어진 함수는 5를 반환해야 한다. N은 2진수 '100000'을 가지므로 2진수 간격이 없기 때문에 N = 32를 지정하면 함수는 0을 반환해야 한다.

다음과 같은 가정에 대해 효율적인 알고리즘을 작성하십시오.

N은 [1..2,147,483,647] 범위 내의 정수다.
Codility Limited by Copy 2009-2020. 모든 권한 예약됨. 무단 복사, 게시 또는 공개 금지.
```

결론은 
1. 10진수 숫자를 2진수로 바꿔라.  
2. 1과 1사이마다 0의 갯수를 세라.  
3. 가장 많은 0의 갯수를 반환하라.

이렇게 진행하면 된다는 말씀.  


## 처음 작성한 코드 
최대한 내가 생각한 아이디어로 먼저 작성해보려고 일절 다른 것은 보지 않았다. (그래서 대참사)
```java
// you can also use imports, for example:
// import java.util.*;

// you can write to stdout for debugging purposes, e.g.
// System.out.println("this is a debug message");

class Solution {
    public int solution(int N) {
        // write your code in Java SE 11
        int[] whereOneIs = new int[10]; // 최대 길이 10까지 가능
        int index = 0;

        while (N > 0) {
            int square = 1; // 2의 0승
            int count = 0;
            while (N > square) {
                square *= 2; 
                count++;
            }

            if (square > N) {
                square /= 2;
                count--;
            }

            N -= square;
            whereOneIs[index++] = count;
        }

        int max = 0;
        for (int i = 0; i < index - 1; i++) {
            int diff = whereOneIs[i] - whereOneIs[i + 1] - 1;
            if (max < diff) {
                max = diff;
            } 
        }
                return maxGap;
    }
}
```
10진수를 2진수로 바꾸려고 하는 과정에서 좀 헤맸다.  
제출하고 보니 Correctness는 66%..

나중에 검색해서 보니 Integer 클래스에 10진수를 2진수로 바꾸는 메소드가 있었다.  
아래 코드는 그 메소드(Integer.toBinaryString(int n))를 사용하여 100% 성공한 코드이다.  

## 완성한 코드
```java
// you can also use imports, for example:
// import java.util.*;

// you can write to stdout for debugging purposes, e.g.
// System.out.println("this is a debug message");

class Solution {
    public int solution(int N) {
        // write your code in Java SE 11
        String binary = Integer.toBinaryString(N);
        int[] array = new int[binary.length()];
        int arrIdx = 0;

        for (int i = 0; i < binary.length(); i++) {
            if (binary.charAt(i) == '1') {
                array[arrIdx++] = i;
            }
        }

        int maxGap = 0;
        for (int i = array.length - 1; i > 0; i--) {
            int gap = array[i] - array[i - 1] - 1;
            if (maxGap < gap) {
                maxGap = gap;
            }
        }

        return maxGap;
    }
}
```
코드가 훨씬 간단하고 알아보기 쉬워졌다!  
아래는 Codility 사이트에서 해당 코드의 정확도를 알려주는 페이지 캡쳐.  

![image](https://user-images.githubusercontent.com/50273050/100738957-bfb3f200-3419-11eb-9a2e-7b5ffd479ee3.png)

## 보완  
자 그럼 여기서 10진수를 2진수로 바꿀 때 메소드(Integer.toBinaryString(int n))를 직접 작성해보자.  
처음에는 2진수를 변환하는 방법을 잊고 있어서 혼란스러웠는데 변환하는 방법을 알고나니 코드로 옮기는 건 쉽다.  

1. 해당 수를 나눈 나머지 수를 배열에 저장한다.
2. 1이 남을 때까지 반복한다.  
3. 배열에 저장된 수들을 거꾸로 재배치한다.  

```java
public static String toBinary(int n) {
		String result = "";
		int[] binaryArr = new int[32]; // 최대 32자리까지 가능하다고 가정 
		int idx = 0;
		
		while (n != 1) {
           binaryArr[idx++] = n % 2;
           n /= 2;
        }
		binaryArr[idx] = n;
		
		for (int i = idx; i >= 0; i--) {
			result += binaryArr[i];
		}
		
		return result;
	}
```



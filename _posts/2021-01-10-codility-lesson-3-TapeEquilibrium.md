---
title: "[코딩테스트] Codility Lesson 3. TapeEquilibrium 문제풀이"
date: 2021-01-10 21:16:00 -0400
categories: coding_test
tags: 코딩테스트 코테 codility lesson 3
--- 

네이버 인턴 코테 준비하면서 다급하게 여러 문제 푸느라 정리를 못했다..  

오늘부터 조금이라도 풀면서 문제 정리해볼 예정!  

간단한 문제이다.  


## Lesson.3 TapeEquilibrium  
```
A non-empty array A consisting of N integers is given. Array A represents numbers on a tape.

Any integer P, such that 0 < P < N, splits this tape into two non-empty parts: A[0], A[1], ..., A[P − 1] and A[P], A[P + 1], ..., A[N − 1].

The difference between the two parts is the value of: |(A[0] + A[1] + ... + A[P − 1]) − (A[P] + A[P + 1] + ... + A[N − 1])|

In other words, it is the absolute difference between the sum of the first part and the sum of the second part.

For example, consider array A such that:

  A[0] = 3
  A[1] = 1
  A[2] = 2
  A[3] = 4
  A[4] = 3
We can split this tape in four places:

P = 1, difference = |3 − 10| = 7
P = 2, difference = |4 − 9| = 5
P = 3, difference = |6 − 7| = 1
P = 4, difference = |10 − 3| = 7
Write a function:

class Solution { public int solution(int[] A); }

that, given a non-empty array A of N integers, returns the minimal difference that can be achieved.

For example, given:

  A[0] = 3
  A[1] = 1
  A[2] = 2
  A[3] = 4
  A[4] = 3
the function should return 1, as explained above.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [2..100,000];
each element of array A is an integer within the range [−1,000..1,000].
Copyright 2009–2021 by Codility Limited. All Rights Reserved. Unauthorized copying, publication or disclosure prohibited.
```

실제 시험에서는 문제를 복붙할 수 없으므로 번역기를 돌리는 것은 불가능하다.  

따라서 영어를 빠르게 읽는 연습도 같이 해야한다.  

일단 문제를 간단히 해석해보자.  

```
비어있지 않은 N개의 원소를 가진 배열 A가 주어질 것.  

배열 A의 인덱스를 가리키는 P는 0 < P < N 의 값을 가짐.  

P로 배열 A를 두 개로 쪼갤건데, 0 ~ P - 1 까지 더한 것과, P ~ N - 1 까지 더한 것을 뺀 절댓값이 

가장 작은 값을 리턴해주면 된다. 

```

## 알고리즘    

1. `right` 변수에 배열의 모든 값을 더하여 담는다.  
2. 배열 0부터 (N - 1)까지 반복한다.  
2 - 1. `left`에 한 원소씩 더하고, `right`에 한 원소씩 뺀다.  
2 - 2. 최솟값과 `left`와 `right`를 뺀 절댓값 중 더 작은 것을 최솟값에 저장한다.  
3. 최솟값을 return한다.  


## 작성 코드 
```
// you can also use imports, for example:
// import java.util.*;

// you can write to stdout for debugging purposes, e.g.
// System.out.println("this is a debug message");

class Solution {
    public int solution(int[] A) {
        // write your code in Java SE 8
        int min = Integer.MAX_VALUE;
        int left = 0;
        int right = 0;
        
        for (int val : A) {
        	right += val;
        }
        
        for (int i = 0; i < A.length - 1; i++) {
        	left += A[i];
        	right -= A[i];
        	min = Math.min(min, Math.abs(left - right)); // absolute value -> abs
        }
        return min;
    }
}
```

## 결과 링크  
https://app.codility.com/demo/results/training2U8KXB-2AZ/  


---
title: "[코딩테스트] Codility Lesson 4. PermCheck 문제풀이"
date: 2021-01-12 23:10:00 -0400
categories: coding_test
tags: 코딩테스트 코테 codility lesson 4
--- 

간단간단. Painless.  

## Lesson.4 PermCheck  
```
A non-empty array A consisting of N integers is given.

A permutation is a sequence containing each element from 1 to N once, and only once.

For example, array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
    A[3] = 2
is a permutation, but array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
is not a permutation, because value 2 is missing.

The goal is to check whether array A is a permutation.

Write a function:

class Solution { public int solution(int[] A); }

that, given an array A, returns 1 if array A is a permutation and 0 if it is not.

For example, given array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
    A[3] = 2
the function should return 1.

Given array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
the function should return 0.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [1..1,000,000,000].
Copyright 2009–2021 by Codility Limited. All Rights Reserved. Unauthorized copying, publication or disclosure prohibited.
```

문제를 간단히 해석해보자.  

```
Permution(순열), 즉 순서가 있는 배열(중복 X)인 A가 주어짐.  

숫자가 1부터 N까지 연속적으로 있어야만 한다. (0 < N < 100,000)  

순열이면 1, 아니면 0 반환.  
```

## 알고리즘      
1. 배열을 정렬한다.  
2. 배열의 첫 원소가 1이 아니거나, 마지막 원소가 N이 아닌 경우 return 0.  
3. 0부터 N - 1까지 반복    
3 - 1. A[i + 1] - A[i] 가 1보다 클 경우 return 0.      
4. 모든 조건을 통과했을 시 return 1.    


## 작성 코드 
```java
// you can also use imports, for example:
// import java.util.*;
import java.util.Arrays;
// you can write to stdout for debugging purposes, e.g.
// System.out.println("this is a debug message");

class Solution {
    public int solution(int[] A) {
        // write your code in Java SE 8
        Arrays.sort(A);
        
        int N = A.length;
        if (A[0] != 1 || A[N - 1] != N) {
            return 0;
        }

        for (int i = 0; i < A.length - 1; i++) {
        	if (A[i + 1] - A[i] > 1) {
        		return 0;
        	}
        }
        return 1;
    }
}
```

## Remind  
- 범위를 잘 체크하자. 맨앞 맨뒤 등..  

## 결과 링크  
https://app.codility.com/demo/results/trainingJZCT68-8T7/


---
title: "[코딩테스트] Codility Lesson 4. FrogRiverOne 문제풀이"
date: 2021-01-11 20:10:00 -0400
categories: coding_test
tags: 코딩테스트 코테 codility lesson 4
--- 

이것도 간단했던 문제!

## Lesson.4 FrogRiverOne  
```
A small frog wants to get to the other side of a river. The frog is initially located on one bank of the river (position 0) and wants to get to the opposite bank (position X+1). Leaves fall from a tree onto the surface of the river.

You are given an array A consisting of N integers representing the falling leaves. A[K] represents the position where one leaf falls at time K, measured in seconds.

The goal is to find the earliest time when the frog can jump to the other side of the river. The frog can cross only when leaves appear at every position across the river from 1 to X (that is, we want to find the earliest moment when all the positions from 1 to X are covered by leaves). You may assume that the speed of the current in the river is negligibly small, i.e. the leaves do not change their positions once they fall in the river.

For example, you are given integer X = 5 and array A such that:

  A[0] = 1
  A[1] = 3
  A[2] = 1
  A[3] = 4
  A[4] = 2
  A[5] = 3
  A[6] = 5
  A[7] = 4
In second 6, a leaf falls into position 5. This is the earliest time when leaves appear in every position across the river.

Write a function:

class Solution { public int solution(int X, int[] A); }

that, given a non-empty array A consisting of N integers and integer X, returns the earliest time when the frog can jump to the other side of the river.

If the frog is never able to jump to the other side of the river, the function should return −1.

For example, given X = 5 and array A such that:

  A[0] = 1
  A[1] = 3
  A[2] = 1
  A[3] = 4
  A[4] = 2
  A[5] = 3
  A[6] = 5
  A[7] = 4
the function should return 6, as explained above.

Write an efficient algorithm for the following assumptions:

N and X are integers within the range [1..100,000];
each element of array A is an integer within the range [1..X].
Copyright 2009–2021 by Codility Limited. All Rights Reserved. Unauthorized copying, publication or disclosure prohibited.
```

문제를 간단히 해석해보자.  

```
개구리가 0에서 X + 1로 강을 건너고 싶은데 나무에서 떨어진 잎을 밟아야만 건널 수 있음. (0 < X < 100,000)   

N개의 원소를 가진 배열 A가 주어질 것. (0 < N < 100,000)  

배열 A의 인덱스를 가리키는 K는 잎이 떨어지는 시간을 의미.  

A[K]는 K 시간에 떨어진 잎의 위치를 의미.  

결론적으로 1부터 X까지 모든 곳에 잎이 덮여있는 가장 최소의 K를 리턴해주면 됨.  
```

## 알고리즘    
중복된 숫자가 등장하니 집합을 사용하면 되겠구나!  
1. 배열 0부터 끝까지 반복한다.  
1 - 1. 집합에 A의 원소를 하나씩 추가한다.  
1 - 2. 집합의 크기가 X와 같아지는 순간의 인덱스를 반환한다.    
2. 반환된 인덱스가 없을 시 -1을 반환한다.    


## 작성 코드 
```
// you can also use imports, for example:
// import java.util.*;
import java.util.HashSet;
import java.util.Set;

// you can write to stdout for debugging purposes, e.g.
// System.out.println("this is a debug message");

class Solution {
    public int solution(int X, int[] A) {
        // write your code in Java SE 8
        Set<Integer> set = new HashSet<Integer>();
        
        for (int i = 0; i < A.length; i++) {
        	set.add(A[i]);
        	
        	if (set.size() == X) {
        		return i;
        	}
        }
        return -1;
    }
}
```

## Remind  
- HashSet을 사용하자 add(), size()
```Set<Integer> set = new HashSet<Integer>();```

## 결과 링크  
https://app.codility.com/demo/results/training638GP8-98Y/


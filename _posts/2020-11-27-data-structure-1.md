---
title: "[자료구조] 동적 메모리 할당"
date: 2020-11-27 22:50:00 -0400
categories: [자료구조]
tags: [자료구조, C]
--- 

## 동적 메모리 할당 라이브러리  

* **void \*malloc(int size)**  
size 바이트 만큼 메모리 블록을 할당하고, 새로운 메모리 블록의 시작주소(포인터)를 반환한다.  
메모리 확보가 불가능하면 **NULL**을 함수의 반환 값으로 반환한다.  

* **void free(void \*ptr)**  
동적으로 할당되었던 메모리 블록을 시스템에 반납한다.  
ptr은 할당되었던 메모리 블록을 가리키는 포인터 값이다.  

* **void \*calloc(int num, int size)**  
**배열** 형식의 메모리를 할당한다.  
개수는 num개, 배열 요소의 크기는 size 바이트.   
요소들은 0으로 초기화.  
반환 값은 malloc 함수와 동일하다.   

* **sizeof 연산자**  
변수나 타입의 크기를 숫자로 반환한다. (Byte 단위)  
```c
// sizeof로 배열의 크기 구하기  
int array[] = {1, 2, 3, 4, 5};
size_t sizearr = sizeof(array) / sizeof(array[0]);
```

동적으로 생성된 구조체는 포인터를 통해서만 접근할 수 있음.  

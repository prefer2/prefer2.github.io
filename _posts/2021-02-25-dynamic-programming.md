---
title: "[Algorithm] 다이나믹 프로그래밍"
date: 2021-02-25 22:04:28
categories: algorithm
tags: algorithm c++ 
use_math: true
---
## 다이나믹 프로그래밍(동적 계획법)

- 큰 문제를 작은 문제로 나눠서 푸는 알고리즘
- DP → 중복 O      분할정복(Divid & Conquer) → 중복 X
- 정답을 한 번 구했으면, 정답을 어딘가에 메모해놓는다(memorization)

1. Overlapping Subproblem

    큰 문제와 작은 문제를 같은 방법으로 풀 수 있다

    문제를 작은 문제로 쪼갤 수 있다

2. Optimal Substructure

    문제의 정답을 작은 문제의 정답에서 구할 수 있다

```cpp
int memo[100];
int fibonacci(int n){
	if( n <= 1 ) {
		return n;
	}
	else {
			if(memo[n] > 0){
				return memo[n];
			}
			memo[n] =fibonacci(n-1) + fibonaccai(n-2);
			return memo[n];
	}
}

//시간복잡도: O(N)
//문제 개수 * 문제 1개를 푸는 시간 -> N * O(1)
```

- 구현 방식
    1. Top-down(재귀)
    2. Bottom-up(반복문)<br><br>

## 문제 풀이

- 큰 문제를 단계 하나와 나머지 단계로 나누어 풀면 된다
- 답을 아직 구하지 않았다는 의미로 -1을 사용하면 좋음(특히 min값 구할 때)
- 연속 또는 증가는 2개의 수를 비교하는 식으로 풀어가면 된다(추가했을때 아닐때 비교 등등)

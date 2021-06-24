---
title: "[프로그래머스] 가장 큰 수"
date: 2021-06-24 15:58:28
categories: Programmers
tags: algorithm c++ 
---

## 문제

0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 구해라

## 문제 조건

- numbers의 길이는 1 이상 100,000 이하
- numbers의 원소는 0 이상 1,000 이하
- 정답이 너무 클 수 있으니 문자열로 바꾸어 return 해라

## 풀이

이어붙였을 때 가장 큰 수를 구하라 했음으로 int형으로 주어진 수들을 string형으로 바꾸어 내림차순으로 정렬해주었다(역 사전순으로 정렬된다). 하지만 그냥 내림차순으로 정렬해주면 예시 2번에서 주어진 [3, 30 ,34]의 경우 [34, 30 ,3]으로 정렬된다. 처음에는 [34, 3, 30]으로 정렬시키기 위해서 num_string[0] 자리가 같은 값들은 다시 정렬해 주어야 하나 싶었다. numbers의 원소가 1000까지 나올 수 있으므로 너무 복잡해진다. 생각해보니 그냥 2개의 값을 붙여보고 비교해 본 후 더 큰 것을 return하면 된다.

*11번 케이스는 [0,0]에 "0"이 나오게 하는 케이스인 것 같다. 문제에서 0이 들어갈 수 있다고 했고 따로 중복된 값은 없다는 말이 없으므로 예외 처리를 해주어야 한다.*

## 코드

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

bool cmp (string a, string b){
    return a+b>b+a;
}

string solution(vector<int> numbers) {
    string answer = "";
    vector<string> num_string;
    
    for(int i=0;i<numbers.size();i++){
        num_string.push_back(to_string(numbers[i]));
    }
    
    sort(num_string.begin(), num_string.end(), cmp);
     for(int i=0;i<num_string.size();i++){
        answer+=num_string[i];
    }
    
    if(answer[0]=='0') return "0";
    return answer;
}
```

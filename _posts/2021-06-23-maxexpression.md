---
title: "[프로그래머스] 수식 최대화(카카오 2020 인턴)"
date: 2021-06-23 14:58:28
categories: Programmers
tags: algorithm c++ 
---

## 문제

수식(expression)에 포함된 연산자의 우선순위를 자유롭게 재정의하여 만들 수 있는 수 중 절댓값이 가장 큰 수를 제출하라

## 문제조건

- 3가지의 연산문자(+, -, *) 만으로 이루어져있다
- 2개 이상의 연산자가 동일한 순위를 가지도록 연산자 우선순위를 정의할 수는 없다
- expression은 길이가 3 이상 100 이하인 문자열
- expression의 피연산자(operand)는 0 이상 999 이하의 숫자
- expression은 항상 올바른 중위 표현식으로 주어진다
- expression의 중간 계산값과 최종 결괏값은 절댓값이 263 - 1 이하가 되도록 입력이 주어진다.
- 같은 연산자끼리는 앞에 있는 것의 우선순위가 더 높다

## 풀이

문제를 처음 접했을때는 stack에 괄호를 넣는 식으로 풀어야 하나 고민했다. 풀다보니 중위 표현식이라 숫자와 연산자만 잘 구별하면 사람이 생각하는 순서대로(괄호 값을 계산한 순서대로) 넣으면 된다는 것을 알 수 있었다.

처음에는 순열을 사용할 생각을 못하고 경우의 수가 6개밖에 없으니 그냥 모든 조합을 만들어서 풀었다([tmp='+' , '-', '*'],  tmp2=['+', '*', '-' ...]) 풀고보니 다른 사람들은 `next_permutation`을 사용하는 것을 알 수 있었다. 연산자들의 순서 조합을 구하기 위해서 오랫만에 next_permutation을 사용하였다. 

### next_permutaion

`bool next_permutation (BidirectionalIterator first, BidirectionalIterator last);`

algorithm 헤더에 있는 함수

- 오름차순으로 정렬된 값을 가진 컨테이너로만 사용가능하다
- default로 operator < 를 사용해 순열을 생성합니다. 즉 **오름차순으로 순열을 생성한다**
- 중복이 있을 시 **중복을 제외한 결과 값**을 return한다

`long long으로 풀지 않아서 30분을 허비했다. 문제를 잘 읽어보자`

```cpp
#include <string>
#include <vector>
#include <iostream>
#include <algorithm>

using namespace std;

long long cal(long long a, long long b, char c){
    if(c=='+'){
        return a+b;
    }
    else if(c=='-'){
        return a-b;
    }
    else{
        return a*b;
    }
}

long long solution(string expression) {
   
    vector <long long> oldnum;
    vector <char> oldd; 
    string s="";
    vector <char> tmp={'*', '+', '-'};
    
    for(int i=0;i<expression.length();i++){
       if(expression[i]=='+'||expression[i]=='-'||expression[i]=='*'){
           oldnum.push_back(stoi(s));
           oldd.push_back(expression[i]);
           s="";
           
       }
        else{
            s+=expression[i];
        }
    }
    oldnum.push_back(stoi(s));
    
    long long mymax=0;
    
    do{
        vector <long long> num = oldnum;
        vector <char> d = oldd;
        for(int i=0;i<3;i++){
            for(int j=0;j<d.size();j++){
                if(d[j]==tmp[i]){
                    num[j]=cal(num[j], num[j+1], tmp[i]);
                    num.erase(num.begin()+j+1);
                    d.erase(d.begin()+j);
                    j--;
                }
            }
        }
        
        if(abs(num[0])>mymax) mymax=abs(num[0]);
    }
    while(next_permutation(tmp.begin(), tmp.end()));
    
   
    long long answer = mymax;
    return answer;
}
```

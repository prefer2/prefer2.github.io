---
title: "[Swift] 기본 문법2"
date: 2021-02-16 21:26:28
tags: ios swift
categories: swift
---
<p align="center"><img src="https://user-images.githubusercontent.com/67692759/107920618-9afaff80-6fb0-11eb-92b6-04db3e92c64b.png"  width="400" height="400"></p>

<br>

## 흐름 제어(Control Flow)

스위프트의 흐름 제어 구문에서는 대부분 소괄호(( ))를 생략할 수 있다

### For-In 문

>**for** 상수 **in** 시퀀스아이템 { 코드 }

```swift
let names = ["Anna", "Alex", "Brian", "Jack"]
for name in names {
    print("Hello, \(name)!")
}
// Hello, Anna!
// Hello, Alex!
// Hello, Brian!
// Hello, Jack!
```

딕셔너리에서는 넘겨받는 값이 튜플로 지정되어 넘어온다

스위프트에서는 for-in 구문보다는 map, filter, flatMap등을 더 많이 사용한다

### While 문

기존 다른 언어들의 while 구문과 유사

repeat-while문: 기존 다른 언어들의 do-while문과 같음

### If 문

다른 언어들과는 달리 스위프트의 if문은 조건의 값이 꼭 Bool 타입이어야 한다
```swift
var temperatureInFahrenheit = 30
if temperatureInFahrenheit <= 32 {
    print("It's very cold. Consider wearing a scarf.")
}
// Prints "It's very cold. Consider wearing a scarf."

```

### Switch 문

>**switch** some value to consider {  
**case** value 1:  
    respond to value 1  
**case** value 2,  
     value 3:  
    respond to value 2 or 3  
**default:**  
    otherwise, do something else  
}

스위프트에서는 case의 비교 값에 범위 연산자를 사용할 수 있다. case 값에 튜플도 사용이 가능하다

```swift
let approximateCount = 62
let countedThings = "moons orbiting Saturn"
let naturalCount: String
switch approximateCount {
case 0:
    naturalCount = "no"
case 1..<5:
    naturalCount = "a few"
case 5..<12:
    naturalCount = "several"
case 12..<100:
    naturalCount = "dozens of"
case 100..<1000:
    naturalCount = "hundreds of"
default:
    naturalCount = "many"
}
print("There are \(naturalCount) \(countedThings).")
// Prints "There are dozens of moons orbiting Saturn."
```

`where` switch문에서 조건을 추가 확인하기 위해 사용

```swift
let yetAnotherPoint = (1, -1)
switch yetAnotherPoint {
case let (x, y) where x == y:
    print("(\(x), \(y)) is on the line x == y")
case let (x, y) where x == -y:
    print("(\(x), \(y)) is on the line x == -y")
case let (x, y):
    print("(\(x), \(y)) is just some arbitrary point")
}
// Prints "(1, -1) is on the line x == -y"
```

`fallthrough` switch 구문의 case를 연속 실행하기 위한 키워드. 

스위프트에서는 한 case를 만족하면 남은 case를 확인하지 않음. 따라서 C언어와 다르게 break 키워드가 필요하지 않다. 한 case를 만족했음에도 다른 case들을 확인하고 싶을때 fallthrough 키워드를 사용하면 된다

### 구문 이름표

**label name**: while condition {
    statements
}

반복문들을 중첩으로 사용할 때 제어 키워드(break, continue 등)이 어떤 범위에 적용되어야 하는지 애매할 때가 있음. 제어 키워드와 구문 이름을 함께 써서 지정된 구문을 제어할 수 있다

## 함수

함수와 메서드는 기본적으로 같다. 구조체, 클래스 등 특정 타입에 연관되어 사용하는 함수를 **메서드**, 전체에서 전역적으로 사용할 수 있는 함수를 그냥 **함수**라고 부른다. 위치하거나 사용되는 범위에 따라 호칭이 달라질 뿐, 함수라는 것 자체에는 변함이 없다

조건문이나 반복문과는 달리 함수에서는 소괄호(( ))를 생략할 수 없다

### 함수의 정의

>**func** 함수이름(매개변수...) → 반환타입 {  
    실행 구문  
    return 반환값  
    }

매개변수

```swift
func greetAgain(person: String) -> String {
    return "Hello again, " + person + "!"
}
print(greetAgain(person: "Anna"))
// Prints "Hello again, Anna!"
```

`매개변수 이름 : 매개변수 타입` 의 형태로 매개변수를 전달한다

매개변수가 여러 개일 때는 쉼표(,)로 매개변수를 구분한다  <br><br>

전달인자 레이블

함수의 외부에서 매개변수의 역할을 좀 더 명확히 할 수 있다. 전달인자 레이블만 다르게 써주면 함수 오버로드로 동작할 수 있다. 전달인자 레이블을 사용하고 싶지 않다면 와일드카드 식별자(_)를 사용하면 된다

**func** 함수이름(`전달인자 레이블` `매개변수 이름: 매개변수 타입` ) → 반환타입 {
    실행 구문
    return 반환값
    }

```swift
func greeting(for person: String) -> String {
    "Hello, " + person + "!"
}
print(greeting(for: "Dave"))
// Prints "Hello, Dave!"
```

### 함수 종류

return 값이 있는 함수

```swift
func addTwoInts(_ a: Int, _ b: Int) -> Int {
    return a + b
}
func multiplyTwoInts(_ a: Int, _ b: Int) -> Int {
    return a * b
}
```

return 값이 없는 함수

```swift
func printHelloWorld() {
    print("hello, world")
}
```

## 옵셔널(Optional)

옵셔널은 단어 뜻 그대로 있을수도 없을 수도 있음을 나타내는 표현

nil은 옵셔널로 선언된 곳에서만 사용될 수 있음. 옵셔널 변수 또는 상수 등은 데이터 타입 뒤에 물음표(?)를 붙여서 표현해준다

## 참조

[Control Flow - The Swift Programming Language (Swift 5.3)](https://docs.swift.org/swift-book/LanguageGuide/ControlFlow.html)

[Functions - The Swift Programming Language (Swift 5.3)](https://docs.swift.org/swift-book/LanguageGuide/Functions.html)

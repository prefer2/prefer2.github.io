---
title: "[Swift] 기본 문법"
date: 2021-02-15 17:26:28
tags: swift ios
categories: swift
---
<p align="center"><img src="https://user-images.githubusercontent.com/67692759/107920618-9afaff80-6fb0-11eb-92b6-04db3e92c64b.png"  width="400" height="400"></p>

<br>

## 변수와 상수

### 변수

`var 변수명 : 데이터타입 = 값` 의 형태 (데이터 타입 생략 가능)

### 상수

`let 상수명 : 데이터타입 = 값` 의 형태 (데이터 타입 생략 가능)  

### 데이터 타입

Swift의 데이터 타입 이름은 첫 글자가 대문자로 시작하는 대문자 카멜케이스를 사용한다

(Int, Unt, Bool, Character, String...)

`Any` : Swift의 모든 데이터 타입을 사용할 수 있다는 뜻. 어떤 종류의 데이터 타입이든지 할당 가능

`AnyObject` : 클래스의 인스턴스만 할당 가능

`nil` : **없음**을 나타내는 키워드(null)


## Collection Types

### 튜플(Tuple)

`지정된 데이터들의 묶음`  타입의 이름이 따로 지정되어 있지 않은, 프로그래머 마음대로 만드는 타입

```swift
//String, Int, Double 타입을 갖는 튜플
var person: (String, Int, Double) = ("prefer", 100, 200.5)

print("이름: \(person.0), 나이: \(person.1), 키: \(person.2)")

//튜플 요소 이름 설정
var person: (name: String, age: Int, height: Double) = ("prefer", 100, 200.5)

print("이름: \(person.name), 나이: \(person.age), 키: \(person.height)")
//기존과 동일하게 인덱스 값으로도 사용 가능
```

### 배열(Array)

같은 타입의 데이터를 일렬로 저장하는 형태

```swift
//빈 배열 만들기
var someInts = [Int]()
print("someInts is of type [Int] with \(someInts.count) items.")
// Prints "someInts is of type [Int] with 0 items."

someInts = [1, 2]
someInts.append(3)
someInts.append(4)
// someInts now contains 4 value of type Int
```

`append` 배열의 맨 뒤에 요소 추가

```swift
someInts.insert(0, at:0)
//someInts now contains 5 items
// 4 is now the first item in the list
```

`insert` 배열 중간에 요소를 삽입

```swift
let num = someInts.remove(at:1)
// the item that was at index 1 has just been removed
```

`remove` 요소를 삭제. 해당 요소가 삭제된 후 반환됨

```swift
for item in someInts {
    print(item)
}
//0
//2
//3
//4

someInts = []
// someInts is now an empty array, but is still of type [Int]
```

`count` 배열의 item 개수

`isEmpty` 배열이 비었는지 boolen형식으로 알려줌

같은 데이터 타입의 배열은 +를 통해 d붙이기가 가능하다

### 세트(Sets)

같은 타입의 데이터를 순서 없이 하나의 묶음으로 저장. 세트 내의 값은 모두 유일한 값, 즉 중복된 값이 존재하지 않음. 세트의 요소로는 해시 가능한 값이 들어와야 함

```swift
//빈 세트 만들기
var letters = Set<Character>()
print("letters is of type Set<Character> with \(letters.count) items.")
// Prints "letters is of type Set<Character> with 0 items."
```

```swift
var favoriteGenres: Set = ["Rock", "Classical", "Hip hop"]

print("I have \(favoriteGenres.count) favorite music genres.")
// Prints "I have 3 favorite music genres."

favoriteGenres.insert("Jazz")
// favoriteGenres now contains 4 items

if let removedGenre = favoriteGenres.remove("Rock") {
    print("\(removedGenre)? I'm over it.")
} else {
    print("I never much cared for that.")
}
// Prints "Rock? I'm over it."

if favoriteGenres.contains("Funk") {
    print("I get up on the good foot.")
} else {
    print("It's too funky in here.")
}
// Prints "It's too funky in here."
```

- Fundamental Set Operations

```swift
let oddDigits: Set = [1, 3, 5, 7, 9]
let evenDigits: Set = [0, 2, 4, 6, 8]
let singleDigitPrimeNumbers: Set = [2, 3, 5, 7]

oddDigits.union(evenDigits).sorted()
// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
oddDigits.intersection(evenDigits).sorted()
// []
oddDigits.subtracting(singleDigitPrimeNumbers).sorted()
// [1, 9]
oddDigits.symmetricDifference(singleDigitPrimeNumbers).sorted()
// [1, 2, 9]
```

- Set Membership and Equality

```swift
let houseAnimals: Set = ["🐶", "🐱"]
let farmAnimals: Set = ["🐮", "🐔", "🐑", "🐶", "🐱"]
let cityAnimals: Set = ["🐦", "🐭"]

houseAnimals.isSubset(of: farmAnimals)
// true
farmAnimals.isSuperset(of: houseAnimals)
// true
farmAnimals.isDisjoint(with: cityAnimals)
// true
```

### 딕셔너리(Dictionary)

요소들이 순서 없이 키와 값의 쌍으로 구성됨. 하나의 딕셔너리 안의 키는 값은 이름을 중복해서 사용할 수 없음

```swift
var airports: [String: String] = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]
//var airports = ["YYZ": "Toronto Pearson", "DUB": "Dublin"] 형식으로도 사용 가능

airports["LHR"] = "London"
// the airports dictionary now contains 3 items

print(airports[DUB])
//Dublin
```

## Reference
https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html
https://docs.swift.org/swift-book/LanguageGuide/CollectionTypes.html

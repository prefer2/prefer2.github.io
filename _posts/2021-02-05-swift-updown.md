---
title: "[Swfit]UpDownGame"
date: 2021-02-05 10:56:28
categories: swift ios
---

[이강의](https://www.youtube.com/watch?v=aVpSUBlZPxU&list=PLz8NH7YHUj_ZF2oja5rP4Sow5KK1zf2yk)를 기반으로 작성된 문서입니다

## Asset

아이폰, 아이패드 등 디바이스마다 사이즈가 다르므로 이에 사용되는 리소스들을 효율적으로 관리하기 위해 사용

**asset catalog**: a tool to manage assets like images that are used by your app as part of its user interface. Simplifiy access to app resources by mapping between named assets and one or more files targeted for different device attributes

- app icon
- color set
- data set (sounds, docs, videos...)
- image set
- launch image 등등

## Auto Layout

제약에 기반한 layout engine. 화면의 비율에 맞게 조정되도록(다양한 기기와 환경에 맞게)

## Variables & Constants

### declare

```swift
var randomVaule: Int = 0 //뛰어쓰기를 맞게 해야함
let hitValue: Int = 0
```

`@IBOutlet` `@IBAction`  stroyboard와의 연결고리

`@IBOutlet` StoryBoard 상에 선언한 View 객체를 Interface Builder(IB) 가 알아볼 수 있게 만드는 것

`@IBAction` StoryBoard 상에 선언한 View 객체가 특정 이벤트가 발생했을 경우 호출되는 함수

### range operators

`randomValue = Int.random(in: 0...30)`

- closed range operator

    A...B

- half-open operator

    A..<B

- one-sided ranges

    A...    ...A    ..<A

### 문자열 보관법

문자열을 다른 값과 합성 

`tryCountLabel.text = "\(tryCount) /5"` tryCount는 int형→tryCount값을 알아서 치환해줌



<img width="748" alt="스크린샷 2021-02-05 오전 12 39 56" src="https://user-images.githubusercontent.com/67692759/106978415-94de7500-679f-11eb-8212-796c6c3ea579.png">
별거는 아니지만 내 핸드폰에서 작동되니 재미나다

책도 빌려서 더 공부해봐야지 홀홀


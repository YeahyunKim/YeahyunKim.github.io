---
title: replacingOccurrences (1) - 문자열 치환
author: yeahyun
date: 2024-02-14
categories:
  - Swift
  - StringMethods
tags:
  - swift
  - methods
  - SwiftStringMethods
image: https://ifh.cc/g/wvbwro.png
description:
  - 파라미터를 통해 받은 문자열을 다른 문자열로 대체하고 새 문자열을 반환한다.
---
## replacingOccurrences(of:with:) 

---
>#### 메소드 설명

>Returns a new string in which all occurrences of a target. string in the receiver are replaced by another given string.
>**파라미터를 통해 받은 문자열을 다른 문자열로 대체하고 새 문자열을 반환한다.**
>[애플 공식 문서](https://developer.apple.com/documentation/foundation/nsstring/1412937-replacingoccurrences)
{: .command-text}


```swift
func replacingOccurrences(
    of target: String,
    with replacement: String
) -> String
```


<BR>
#### 사용 예시
###### 예시 1 : `String 을 바꿀때`

```swift
import Foundation 

var text = "helloMath"

// hello 가 happy로 바뀜
var newText = text.replacingOccurrences(of: "hello", with: "happy")

// bye 가 존재하지 않음으로 기존 text 값을 반환함
var newText2 = string.replacingOccurrences(of: "bye", with: "happy")

print(newText) // "happyMath"
print(newText2) // "helloMath"
```
<br>
###### 예시 2 : `Character를 바꿀때`

```swift
import Foundation 

var text = "helloSwift-"

//기존 변수 값을 변환
text = text.replacingOccurrences(of: "-", with: "!")

//새로운 변수에 값을 할당
var newText = string.replacingOccurrences(of: "-", with: "!")

print(text) // "helloSwift!"
print(newText) // "helloSwift!"
```
<br>

#### 주의사항

> 새 문자열을 반환하기 때문에, 새 문자열의 반환값을 받을 변수 및 함수의 return 에 사용할 수 있다. 
{: .prompt-tip}

<br>

[애플 공식 문서](https://developer.apple.com/documentation/foundation/nsstring/1412937-replacingoccurrences)
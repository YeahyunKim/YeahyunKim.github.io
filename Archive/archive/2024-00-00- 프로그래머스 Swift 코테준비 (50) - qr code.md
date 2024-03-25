---
title: 프로그래머스 Swift 코테준비 (50) - qr code
author: yeahyun
date: 2024-02-14
categories:
  - Programmers
  - 기초
tags:
  - Algorithm
  - Programmers
image: https://ifh.cc/g/wvbwro.png
---
## 01 문제 : qr code

---
#### 문제 설명

>두 정수 `q`, `r`과 문자열 `code`가 주어질 때, `code`의 각 인덱스를 `q`로 나누었을 때 나머지가 `r`인 위치의 문자를 앞에서부터 순서대로 이어 붙인 문자열을 return 하는 solution 함수를 작성해 주세요.
{: .command-text}

<BR>
#### 제한사항

>• 0 ≤ `r` < `q` ≤ 20
>• `r` < `code`의 길이 ≤ 1,000
>• `code`는 영소문자로만 이루어져 있습니다.
>• 1 ≤ `c` ≤ `m`
{: .command-text}
<BR>

#### 입출력 예

|q|r|code|result|
|---|---|---|---|
|3|1|"qjnwezgrpirldywt"|"jerry"|
|1|0|"programmers"|"programmers"|

<BR>

#### 입출력 예 설명

###### 입출력 예 #1

>• 예제 1번의 `q`와 `r`은 각각 3, 1이고 인덱스와 그 값을 `q`로 나눈 나머지가 잘 보이도록 표로 만들면 다음과 같습니다.
{: .command-text}

|`code`|q|j|n|w|e|z|g|r|p|i|r|l|d|y|w|t|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|index|0|1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|
|`q`로 나눈 나머지|0|1|2|0|1|2|0|1|2|0|1|2|0|1|2|0|


###### 입출력 예 #2

>• 예제 2번의 `q`와 `r`은 각각 1, 0이고 인덱스와 그 값을 `q`로 나눈 나머지가 잘 보이도록 표로 만들면 다음과 같습니다.
{: .command-text}

|`code`|p|r|o|g|r|a|m|m|e|r|s|
|---|---|---|---|---|---|---|---|---|---|---|---|
|index|0|1|2|3|4|5|6|7|8|9|10|
|`q`로 나눈 나머지|0|0|0|0|0|0|0|0|0|0|0|
<br>

<br>
#### 제시 코드

```swift
import Foundation

func solution(_ q:Int, _ r:Int, _ code:String) -> String {
    
    return ""
    
}
```

<br>
<br>

## 02 풀이 
---

#### solution 1 : map, indices, filter 다같이 사용하기

먼저 코드의 문자 개수만큼 반복문(`map`)을 돌려야하고, 해당 문자의 인덱스 값을 `q`로 나눈 나머지 값을 구해야하니, `filter` 를 사용한다.

```swift
var characterArray = code.map{$0}

characterArray.indices.filter{ $0 % q == r }
```

<br>
이후 `filter` 의 조건문으로 걸러진 요소들을 하나의 문자열로 합쳐야하므로, `joined()`를 활용하여 문제를 마무리 했다.

```swift
var characterArray = code.map{$0}

characterArray.indices.filter{ $0 % q == r }.map{ String(characterArray[$0]) }.joined()
```

<br>
<br>
## 💡Answer 01
---

```swift
import Foundation

func solution(_ q:Int, _ r:Int, _ code:String) -> String {
    
    var characterArray = code.map{$0}
    
    return characterArray.indices.filter{ $0 % q == r }.map{ String(characterArray[$0]) }.joined()
}
```

<br>
<br>

[해당문제 풀러가보기](https://school.programmers.co.kr/learn/courses/30/lessons/181903)
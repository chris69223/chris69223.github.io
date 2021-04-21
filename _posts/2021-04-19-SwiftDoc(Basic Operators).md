---
layout: post
title:  "Swift 공식문서 뿌시기 Basic Operator"
excerpt: "기초 연산자들에 대해 알아봅시다!"
date:   2021-04-19 
categories: swiftDoc5.4
---

# 2장 Basic Operators

- operator(연산자)는 값들을 확인하거나, 바꾸거나 조합하기 위해 사용하는 특수한 기호나 구절이다.
- 예로 우리가 이미 알고 있는 + - * / 등과 같은 연산자와 논리 연산자인 &&들이 포함된다.
- swift는 일반적인 언어가 지원하는 연산자를 지원할 뿐만 아니라 코딩 에러를 없애기 위해 몇가지를 개선하였다.
- 할당  연산자(=)는 같음 연산자(==)를 의도한 곳에서 실수로 사용되는 것을 막기 위해, 값을 반환하지 않는다.
- swift는 c와 달리 사칙연산의 값의 오버플로우를 허락하지 않고 이것을 허용하고 싶으면 Overflow Operator를 사용하면 된다.

### Overflow 연산자

- swift에서 사칙연산의 오버플로우를 허락하기 위한 연산자

```swift
var potentialOverflow = Int16.max
// potentialOverflow equals 32767, which is the maximum value an Int16 can hold
potentialOverflow += 1
// this causes an error
```

Int16이 저장하고 있는 값보다 클 경우 오버플로우가 발생하면서 에러가 발생하는데 3가지 오버플로우 연산자를 

사용하여 오류를 제어할 수 있다. 

1. 오버플로우 추가 (&+)
2. 오버플로우 빼기 (&-)
3. 오버플로우 곱셈(&*)

```swift
var maxOverflow = Int16.max
// maxOverflow equals 32767, which is the maximum value an Int16 can hold
print(maxOverflow) // 32767
print(maxOverflow &+ 1) // -32768
var minOverflow = Int16.min //-32768
print(minOverflow &- 1) //32767
print(minOverflow &* 2 ) // 0 ??
```

## Terminology(용어)

- 연산자는 단항, 이항, 삼항 연산자가 있다.
- 단항 연산자는 -a, !b , c!와 같이 하나의 대상에 앞뒤에 붙여서 사용하는 연산자이다.
- 이항 연산자는 2 + 3 와 같이 두 대상 사이에 사용하는 연산자이다
- swift에서 삼항 연산자는 a ? b : c 와 같은 형태인 조건 연산자만 존재한다.

    (아래 태그에서 자세히 설명)

## Assignment Operator(할당 연산자 =)

- 할당 연산자는 우리가 알고 있는 a = b ,  a에 값에 b값을 대입하거나 a = 5와 같이 값을 초기화 해주는 용도로 사용한다.
- 할당 연산자는 값이 여러 값을 가진 튜플에서도 사용 가능하다.

```swift
let (a, b) = (1, 2)
// a 는 1, b는 2로 초기화 됨
```

- swift에서 할당 연산자(=)는  값 반환 x  - 같음 연산자를(==)를 의도하여 실수로 사용되는 것을 막기 위해

```swift
if x = y{
    print("x와 y는 같다 ")
}
else {
    print("다르다")
}
//error: BasicOperators.playground:25:6: error: use of '=' in a boolean context, did you mean '=='?
//if x = y{
//   ~ ^ ~
//     ==
```

## Arithmetic Operators(+, - , *, )

- 산술 연산자는 +, -, *, /
- 더하기 연산자는 String 타입에도 연결된다

```swift
print("Young" + "Sang") 
// YoungSang
```

- 값의 오버플로우를 허용하지 않는다. 오버플로우 연산자를 사용하여 동작을 선택 가능하다.

### Remainder Operator(나머지 연산자 %)

```swift
print(8 % 3) // 2
print(8 % -3) // 2
print(-8 % 3) // -2
print(-8 % -3) // -2
//a % b 와 a % -b는 항상 같다. 
```

### Unary (Minus + Plus) Operator(단항 음수 연산자와  양수 연산자)

- (-) 연산자는 값의 부호를 반대로 바꿔주지만 (+) 연산자는 값의 부호에 영향 x

```swift
let num = 3
let minusNum = -num
let plustNum = -minusNum
print(minusNum, plustNum) // -3 3
print(+minusNum,plustNum) // -3 -3 
```

## Compound Assignment Operators(복합 할당 연산자)

- swift는 +=와 같은 복합 할당 연산자를 제공함

```swift
var a = 1
a += 2 // a = a+2 와 같은 표현 
```

연산자 종류는 아래 링크에서 알아볼 수 있다. 

[Apple Developer Documentation](https://developer.apple.com/documentation/swift/swift_standard_library/operator_declarations)


![이미지1](./Users/user/chris69223.github.io/assets/SwiftDoc/02/01.png)

위 사진의 연산자들이 처음보는 연산자들이여서 검색해본 결과 

SIMD라는 protocol은 크기가 다른 고정 너비 숫자 유형의 고정 너비 벡터로 작업한다는데?... swift5에서 처음 도입 됐고 벡터값을 비교할때 쓰이고 bool 타입으로 결과값 반환해준다. 

```swift
import simd

let x = SIMD4<Int>(1,2,3,4)
let y = SIMD4<Int>(3,2,1,0)
print(x .== y) //SIMDMask<SIMD4<Int>>(false, true, false, false)
print(x .!= y) //SIMDMask<SIMD4<Int>>(true, false, true, true)
print(x .<= y) //SIMDMask<SIMD4<Int>>(true, true, false, false)

```

## Comparison Operators(비교 연산자)

- 같다 (a == b)
- 같지않다 (a != b)
- 크다 (a > b)
- 작다 (a < b)
- 크거나 같다 (a >= b)
- 작거나 같다 (a <= b)
- 객체 비교를 위한 식별 연잔자 (===, !==)

```swift
// 객체 비교
class Study{
    var name: String
    var age: Int
    
    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
}

var stu : Study = Study(name: "hyo", age: 21)
var stu2 : Study = Study(name: "sang", age: 20)

if stu === stu2{
    print("같은 객체입니다")
}else{
    print("다른 객체입니다")
}
//다른 객체입니다
if stu !== stu2{
    print("다른 객체입니다")
}else{
    print("같은 객체입니다")
}
// 다른 객체입니다
```

[{233쪽 - Point 객체 비교하기} 스위프트(Swift) 무료 동영상](https://m.post.naver.com/viewer/postView.nhn?volumeNo=16743673&memberNo=40680985)

- 유형이 같고 값 수가 같으면 두 튜플도 비교할 수 있다.
- 동일한 타입, 동일한 개수를 가진 튜플 형식을 비교할 수도 있는데 튜플을 비교할 땐 왼쪽에서 오른쪽으로 한 값씩 비교하게 된다. 어떤 값이라도 바로 비교가 되면 그 결과가 비교 결과가 된다.

```swift
print((1, "zebra") < (2, "apple"))   // true
print((3, "apple") < (3, "bird"))    // true
print(("dog", "cat") == (4, 4))      // error
```

## Ternary Conditional Operator(삼항 조건부 연산자)

- 삼항연산자 a ? b : c  == a조건 ? : 결과 b : 결과 c
- if문 보다 코드가 짧아서 가독성을 높여주지만 너무 많은 사용은 자제

```swift
let sangAge: Int  = 29
sangAge > 30 ? print("상은 30대입니다") : print("상은 20대입니다!")
// 출력 : 상은 20대입니다! 

//if문의 긴 코드를 삼항연산자를 사용하면 한줄로 줄일 수 있음
let sangAge: Int = 29
if sangAge > 30{
    print("상은 30대입니다.")
}else{
    print("상은 20대입니다!")
}
```

## *Nil-Coalescing Operator(Nil 병합 연산자)

- a ?? b 형태를 갖는 연산자이다. 옵셔널a를 unwrap해서 만약 a가 nil일 경우 b를 반환해준다.

```swift
a ?? b  //같은표현 a != nil ? a! : b 
//a가 nil아니면 a를 unwrap하고 아니면 b를 반환! 

let stuName = "sang"
var stuDefinedName: String?

var sieveName = stuDefinedName ?? stuName // sieveName이nil 이 아니면 오류뜸
print(sieveName)
```

## Range Operators(범위 연산자)

- a...b(a부터 b까지)
- a..<b(a부터 b-1까지) - 코테 준비하면서 배열 출력할 때 많이 씀

```swift
let stuNames = ["Sang", "Hosu", "Sieve", "Hyo"]
for i in 0...stuNames.count{
    print("\(stuNames[i])")
}//Fatal error: Index out of range
for i in 0..<stuNames/count //
```

- 단방향 범위 연산자 [a...](a인덱스부터 배열의 끝까지 모든 요소 포함),
- [...b](배열의 첫 인덱스부터 b인덱스까지 모든 요소 포함)

```swift
for i in [1...]{
    print("\(students[i])")
}
//["Hosu", "Sieve", "Hyo"]
for i in [...2]{
    print("\(students[i])")
}
//["Sang", "Hosu", "Sieve"]
for i in [..<2]{
    print("\(students[i])")
}
//["Sang", "Hosu"]
```

- **One-sided ranges는 반복이 어디에서 시작해야 하는지 혹은 끝나는지에 대한 부분이 명확하지 않기 때문에 명시적인 종료 조건을 추가해야 한다.**

```swift
let range = ...5
print(range.contains(3)) //true
print(range.contains(7)) //false
```

## Logical Operators(논리 연산자)

- 논리 연산자는 Bool 타입 반환
- swift는 세 개의 논리연산자만 반환

### 1. Logical Not (!a)

- !a로 쓰이면 Bool 값을 반대로 바꾸어 준다

```swift
let allowedEntry = false
if !allowedEntry {
    print("ACCESS DENIED")
}else{
    print("ACCESS UNDENIED")
} // ACCESS DENIED 
//allowedEntry 값이 false였는데 !연산자로 true로 변환되면서 ACCESS DENIED가 출력됐다
```

### 2. Logical AND (a && b)

- a와 b값 중 하나라도 false이면 전체식도 false

```swift
let a = true
let b = false
if a && b {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// ACCESS DENIED
```

### 3. Logical OR (a || b)

- a와 b 중 하나만 참이여도 전체식 true

```swift
let a = false
let b = true
if a || b {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Welcome!
```

### 4. 논리 연산자 결합

![이미지2](./Users/user/chris69223.github.io/assets/SwiftDoc/02/02.png)

연산자 우선순위 한번씩 보고 가면 좋을 것 같다.

```swift
	//&&가 ||보다 우선순위가 높아서 괄호를 안해줘도 값은 성립한다. but 아래와 같이 괄호를 해주면 의도를 
//의도를 더 쉽게 알게 해준다. 
if a && b || c || d {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Welcome!
//의도를 더 쉽게 하기 위해서 괄호를 포함하는 것이 유용하다.
if (a && b)|| c || d {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
```



# 3장 Strings and Characters

- swift에서 문자열과 문자 타입은 유니코드 호환 방법으로 제공하고 있다.
- 문자열의 연결은 + 연산자를 사용하여 사용 가능하다. print("hellp" + "sang")
- 문자열 보간을 통해 어떠한 문자열에서 다른 문자열을 불러올 수 있다.
- swift의 문자열은 유니코드 문자로 구성된다.

```swift
let nameString = "sang"
```

### Multiline String Literals

- """ """를 사용하면 여러 줄의 문자열을 사용할 수 있다.

```swift
let sangIntro = """
hello! my name is sang nice to meet you! 
yo!
""" 
let sangIntro = """
hello! my name is sang nice to meet you! \
yo!
"""
```

\를 사용해주면 hello! my name is sang nice to meet you! yo! 줄바꿈 없이 출력해줄 수 있다. 

### Special Characters in String Literals

- swift의 문자열은 다음과 같은 특수문자들을 포함할 수 있다.
- \0(널 문자), \\(백 슬래시), \t(가로 탭)
- \n(줄 바꿈), \r(캐리지 리턴)  이둘의 차이는 뭘까?

 \n \r 둘다 출력은 똑같이 줄바꿈 해주는데 \r은 캐럿이 그 줄 맨 앞으로 간다는데? 이게 뭔소리지? 

암튼 검색해보니깐 예전에 유닉스 계열에서 쓰던 특수문자인데 swift는 그냥 \n쓰면 된다고 합니다! 

혹시 이거에 대해 아시면 이따 말씀 부탁드립니다!

- \u{n}, n은 1-8자리 십진수 형태로 구성된 유니코드

![Swift%205%204%20Basic%20Operators%2072b12078b827434bbc3912afd5fa8aca/_2021-04-14__11.42.50.png](Swift%205%204%20Basic%20Operators%2072b12078b827434bbc3912afd5fa8aca/_2021-04-14__11.42.50.png)

- \"(큰 따옴표) 및 \'(작은 따옴표)
- 아래는 그림과 코드는 제가 백준에서 문자열 관련해서 푼 문제인데 위의 내용과 비슷해서 가져와봤습니다!

![Swift%205%204%20Basic%20Operators%2072b12078b827434bbc3912afd5fa8aca/_2021-04-14__10.41.38.png](Swift%205%204%20Basic%20Operators%2072b12078b827434bbc3912afd5fa8aca/_2021-04-14__10.41.38.png)

```swift
// 일단 \를 출력하려면 \을 하나 더 써줘야함 ex \\\를 출력하고싶다? print("\\\\\\")
// 나머지는  """ 이 사이에 써주면 ㄱㅊ """
import Foundation

print("""
\\     /\\
 )   ( ')
(   /  )
 \\(___)|
""")
```

### Extended String Delimiters(확장된 문자열 경계기호)

- 문자열 사이에 #을 넣어주면 \을 사용하지 않고도 특수문자를 출력할 수 있다.
- 아래 코드는 위 문제와 똑같은 예시인데 훨씬 더 간단하다.

```swift
let cat = #"""
\    /\
 )  ( ')
(  /  )
 \(__)|
"""#

print(cat)
```

## Initializing an Empty String(빈 문자열 초기화)

- 빈 문자열을 만드는 두가지 방법
- isEmpty라는 프로퍼티를 통해서 문자열이 비어있는지 boolean값으로 확인할 수 있다.

```swift
var emptyString = "" // 1. 빈 문자열 리터럴
var anotherEmptyString = String() // 2. 초기화 문법
// 위의 두 문자열은 모두 비어있다.

if emptyString.isEmpty {
    print("Nothing to see here")
}
```

## String Mutability(문자열 가변성)

- 문자열도 var 타입으로 선언됐다면 수정 가능
- let으로 선언 됐으면 에러발생

```swift
var stuName = "YoungSang"
stuName += "Go"
// YoungsangGo

let stuName2 = "YoungSang"
stuName2 += "Go"
print(stuName2) // error
```

## Strings Are Value Types

- swift에서 String 타입은 값 타입이다.
- 새로운 String 값을 생성하는 경우 String값은 함수 또는 메서드에 전달되거나 복사

## Working with Characters

- 반복문을 사용하여 문자열의 개별 요소를 출력할 수 있다. + swift는 이모티콘도 출력 가능

```swift
for character in "Dog!🐶" {
    print(character)
}
// D
// o
// g
// !
// 🐶
```

- String 값은 Character 배열로도 만들 수 있다.

```swift
let dogCharacters: [Character] = ["D", "o", "g", "!", "🐶"]
let dogString = String(dogCharacters)
print(dogString)
// Prints "Dog!🐶"
```

## Concatenating Strings and Characters(문자열 연결 )

- 문자열은 위에서도 말했지만 + 연산자를 사용하여 두 문자열을 연결할 수 있다.
- 또한 배열에서 쓰이는 append 연산자를 사용하여 문자열을 추가할 수 있다.

```swift
var stuName = "YoungSangGo"
stuName.append("!!@#")
print(stuName) // YoungSangGo!!@#
```

- 여러 줄 String을 합칠 때에는 마지막 줄에서 개행이 일어나지 않으므로 처음 부분에서 공백을 해줘야 개행이 일어난다

```swift
let badStart = """
one
two
"""
let end = """
three
"""
print(badStart + end)
// Prints two lines:
// one
// twothree

let goodStart = """
one
two

"""
print(goodStart + end)
// Prints three lines:
// one
// two
// three
```

## String Interpolation(문자열 보간 )

- 문자열 보간은 String에 상수, 변수, 리터럴, 연산 등의 값을 넣는 것을 말한다.

```swift
var sangAge = 15
var stuName = "YoungSang age is \(sangAge)"
print(stuName) // YoungSang age is 15

//#을 사용하면 문자열 보간x
var stuName = #"YoungSang age is \(sangAge)"#
//YoungSang age is \(sangAge)
//하지만 보간하는곳 바로 앞에다가 # 붙여주면 가능
var stuName = #"YoungSang age is \#(sangAge)"#
```

## Unicode

- 유니코드는 텍스트를 인코딩하고 표현하기 위한 국제 표준이다.
- 어떠한 문자와 언어들도 표준화된 형식으로 읽고 쓸 수 있다.

### Unicode Scalar Values

- swift의 기본 String 타입은 유니코드 스칼라 값이다.
- 고유한 21비트 숫자이다
- 모든 21비트 유니코드 스칼라 값이 문자에 할당되는 것은 아니고 향후에 추가가 되거나 UTF-16 인코딩에 사용되도록 예약되어 있다
- 간단하게 예를 들어 보면 U+0061은("a")나타내며 U+1F42`5`는("🐥")를 나타낸다.

### Extended Grapheme Clusters

- 스위프트 문자 타입의 모든 인스턴스는 하나의 확장된 문자소 클러스터를 대표한다.
- 확장된 문자소 클러스터는 읽을 수 있는 단일 문자를 제공하는 하나 또는 그 이상의 유니코드 스칼라의 시퀀스다.
- 확장된 문자소 클러스터는 복잡하게 구성되어 있는 단일 문자 값을 유연하게 표현할 수 있게 해준다.

```swift
let precomposed: Character = "\u{D55C}"                  // 한
let decomposed: Character = "\u{1112}\u{1161}\u{11AB}"   // ᄒ, ᅡ, ᆫ
// precomposed is 한, decomposed is 한
```

## Counting Characters

- 문자열의 개수를 검색하려면 count 속성을 이용

```swift
var stuName = "YoungSang"
print(stuName.count) // 9 
```

## Accessing and Modifying a String

- 각 String값에는 문자열에서 각 위치에 해당하는 인덱스가 있다. String.IndexCharacter
- 각각의 문자가 다른 양의 메로리를 가질 수 있기 때ㅜㄴ에 swift 문자열은 정수 값으로 index 생성 불가능
- startIndex는 String의 첫 Charater에 접근하고 endIndex는 마지막에 접근한다.
- String의 index(before:), index(after:)을 사용해서 인덱스에 접근할 수 있다.
- index(_:offsetBy:)메소드를 이용해서 여러 문자를 한 번에 뛰어넘을 수 도 있다.

```swift
var stuName = "YoungSang"
print(stuName[stuName.startIndex]) // Y
//print(stuName[stuName.endIndex]) // error
print(stuName[stuName.index(after: stuName.startIndex)]) // o
swift의 endIndex startIndex는 시작과 끝의 접근만 가능한데
index(_:offsetBy:)를 사용하여 중간에 있는 문자에 접근할 수 있다.
    - 시작 지점부터 떨어진 정수 값만큼을 더한 위치를 반환한다.
```

endIndex를 사용했을 때 에러가 나는 이유는 위의 "YoungSang"에서 Y -0부터 시작해서  g- 8까지 인덱스가 정해져 있는데 endIndex는 9를 반환한다. 따라서 올바르게 사용하려면 

```swift
print(stuName[stuName.index(before: stuName.endIndex)])// 이렇게 해주면 g 값을 출력 가능 
// 으 복잡하다 복잡해

print(stuName[stuName.index(stuName.startIndex, offsetBy: 3)])// n
//offsetBy를 사용하여 원하는 인덱스의 문자 출력
```

swift의 endIndex startIndex는 시작과 끝의 접근만 가능한데
index(_:offsetBy:)를 사용하여 중간에 있는 문자에 접근할 수 있다.
- 시작 지점부터 떨어진 정수 값만큼을 더한 위치를 반환한다.

- indices속성을 사용하여 개별 문자열 출력 가능

```swift
for index in stuName.indices {
    print("\(stuName[index]) ", terminator: "")
} // Y o u n g S a n g
```

- 삽입 및 제거는 배열의 원소를 삭제와 삽입과 같다고 생각하면 된다.

```swift
var stuName = "YoungSang"
stuName.insert("!", at: stuName.endIndex)
print(stuName) // YoungSang!
//remove
stuName.remove(at: stuName.index(before: stuName.endIndex)) // YoungSang
```

## Substrings

- String에서 prefix(_:)의 결과를 가져오면 SubString의 인스턴스가 된다.
- swift에서 String과 SubString은 비슷하기 때문에 동일하게 사용 가능
- but, 문자열과 달리 문자열에 대한 작업을 수행하는 동안 짧은 시간 동안 만 하위 문자열을 사용
- 더 길게 사용하고 싶으면 새로운 String으로 변환 필요

```swift
var stuName = "Young, Sang"
let index = stuName.firstIndex(of: ",") ?? stuName.endIndex
let beginning = stuName[..<index] //Young
// Convert the result to a String for long-term storage.
let newString = String(beginning)
```

String과 Substring의 차이점은? 

substring도 자체적으로 메모리를 가지긴 하지만 String의 메모리를 재사용하고  subString을 사용하는 동안에는 기존의 String을 메모리에 보관해야 하기 때문에 substring을 오래 지속하기엔 적합 x 

![Swift%205%204%20Basic%20Operators%2072b12078b827434bbc3912afd5fa8aca/Untitled.png](Swift%205%204%20Basic%20Operators%2072b12078b827434bbc3912afd5fa8aca/Untitled.png)

## Comparing Strings

- swift에서는 텍스트를 비교하기 이해 세가지 방법을 제공

### 1. String and Character Equality

- 비교연산자를 사용하여 두 문자가 같은지 다른지 판별(==) (!=)

```swift
let quotation = "We're a lot alike, you and I."
let sameQuotation = "We're a lot alike, you and I."
if quotation == sameQuotation {
    print("These two strings are considered equal")
}
// Prints "These two strings are considered equal"
```

### 2. **Prefix and 3. Suffix Equality**

- 문자열에 특정 접두사, 접미사가 있는지 확인하려면 hasPrefix(*:) , hasSuffix(*:)메소드를 사용하면 된다.
- 접두사는 고, 김 이런거 찾을 때 접미사는 영상 호수 효성 찾을 때

```swift
let studyName = ["고영상","김호수", "신영상", "서영상", "김효성", "고효성" ]
var sCount = 0
for item in studyName{
    if item.hasprefix("김"){
        print(item)  // 김호수 김효성
        sCount += 1  //2
    }
}
let studyName = ["고영상","김호수", "신영상", "서영상", "김효성", "고효성" ]
var sCount = 0
for item in studyName{
    if item.hasSuffix("효성"){
        print(item)  // 김효성 고효성
        sCount += 1  //2
    }
}

let studyName = ["고영상","김호수", "신영상", "서영상", "김효성", "고효성" ]
var sCount = 0
for item in studyName{
    if item.contains("영상"){
        print(item) // 고영상 신영상 서영상 
        *sCount += 1*
    }
}
차이점을 다시 알기 
```

## Unicode Representations of Strings

- 유니코드 문자열이 텍스트 파일이나 다른 저장소에 저장될 때 문자열의 유니코드 스칼라 값은 여러 가지 Unicode-defined encoding forms에 의해 인코딩 된다.
- swift에서는 세가지 유니코드 표현 방법이 있다.

```swift
let pigString = "Pig!!🐷"
```

1. UTF-8 Representation

```swift
let pigString = "!!🐷"
for codeUnit in pigString.utf8 {
    print("\(codeUnit) ", terminator: "")
}
**// 80 105 103 33 33 240 159 144 183**
```

 

 2. UTF-16 Representation

```swift
let pigString = "Pig!!🐷"
for codeUnit in pigString.utf16 {
    print("\(codeUnit) ", terminator: "")
} //80 105 103 33 33 55357 56375
```

 3. Unicode Scalar Representation

- String의 유니코드 Scalar접근 방법은 unicodeScalars 프로퍼티를 통해서 가능하다. 이 프로퍼티는 UnicodeScalarView 타입이고, UnicodeScalar타입의 값의 collection이다.
- 각 UnicodeScalar는 value 프로퍼티를 통해 21-bit 값을 리턴하고 이 프로퍼티는 Uint32 타입이다.

```swift
let pigString = "Pig!!🐷"
for scalar in pigString.unicodeScalars {
    print("\(scalar.value) ", terminator: "")
}//80 105 103 33 33 128055
```

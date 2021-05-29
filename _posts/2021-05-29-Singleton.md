---
layout: post
title:  "[iOS]Singleton Pattern이란?"
excerpt: "싱글톤 완벽정리!"
date:   2021-05-29 
categories: iOS
---


# iOS 싱글톤 패턴(Singleton Pattern)

안녕하세요! 쌍이에요! 

오늘은 **싱글톤 패턴**이 무엇이고 어떻게 사용하는지 알아보겠습니다!

(사실 저번 면접에서 자세히 설명 못해서 다시 정리하는 건 안 비밀!)

### 싱글톤 패턴은?   - 클래스가 여러 차레 호출되어도 딱 한 객체만 생성되도록 하는 디자인 패턴

1. 특정 용도로 객체를 하나만 생성하여 공용으로 사용하고 싶을 때 사용하는 디자인 유형
2. 환경설정, 로그인 정보 등을 특정용도로 생성해둔 객체에 넣어두고 여러 객체에서 접근 가능하도록 하여 데이터를 사용하는 것
3. 임의로 메모리에서 해제해주지 않는 이상 프로그램이 실행되고 끝날 때까지 메모리에 유지된다. 
4. Thread-safe 하게 작성하여 멀티스레드에서 사용해도 문제가 없어야 한다.

### iOS에선 Singleton을 언제 쓰는거야? - 솔로들만 씁니다;;;

```swift
let screen = UIScreen.main
let userDefault = UserDefaults.standard
let application = UIApplication.shared
let fileManager = FileManager.default
let notification = NotificationCenter.default
```

이런 경우에 쓴다고 합니다. 아직 감이 안잡히시죠? 자세하게 예를 들어서 설명해볼게요! 

**Sang**이라는 유저가 있고 로그인을 했습니다. 

**ViewController1**에서는 Sang의 이름이 필요하고 

**ViewController2**에서는 Sang의 나이가 필요하다면 

각각의 **ViewController**마다 Sang 이라는 유저의 객체를 생성해 이름과 나이를 불러와야 하기 때문에 

총 2개의 객체가 생성되어야 합니다. 이러면 사용되는 곳이 많을수록 메모리 낭비가 심해질겁니다! 

이 때 싱글톤 패턴을 사용해서 **한 곳에 Sang의 정보를 담아두고 하나의 객체만 생성한 후** 

**원할 때  각각의 ViewController에서 정보들을 빼서 사용**하면 됩니다! 

예제로 다시 보겠습니다! 

CurrentUser 클래스를 이용하여 로그인 했을 때 이름과 나이를 정해주고 

```swift

class CurrentUser{
    static let shared = CurrentUser()
    var name:String?
    var age:Int?
    private init(){
        
    }
}
```

```swift
class LoginViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        
        let currentUser = CurrentUser.shared
        currentUser.name = "Sang"
        currentUser.age = 26
        
    }
}
```

앞에서 정해준 이름은 ViewController1에서 사용하고 

```swift
class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        
        let curretUser = CurrentUser.shared
        print(curretUser.name ?? "")
    }
}
```

나이는 ViewController2에서 자유롭게 사용할 수 있습니다! 

```swift
class ViewController2: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        
        let currentUser = CurrentUser.shared
        print(currentUser.age ?? 0)
        
    }
}
```

### 위와 같이 싱글톤 패턴으로 만들어주면 하나의 객체만 사용하기 때문에 메모리를 아껴 사용할 수 있고

### 정해진 값을 여러 곳에서 공유하여 사용할 수 있습니다!

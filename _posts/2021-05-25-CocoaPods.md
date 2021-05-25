---
layout: post
title:  "[iOS]CocoaPods 설치 및 사용방법"
excerpt: "코코아팟 완벽정리!"
date:   2021-05-25 
categories: iOS
---

# [iOS]CocoaPods 설치 및 사용방법

안녕하세요! 오늘은 CocoaPods은 무엇이고 어떻게 실행하는지 알아보도록 하겠습니다. 

# 먼저 CocoaPods이란?

- iOS 및 macOS, tvOS 등 애플 플랫폼에서 개발을 할 때, 외부 라이브러리를 관리하기 쉽도록 도와주는 의존성 관리 도구의 일종입니다.
- 즉, 라이브러리 관리를 도와주는 중요한 도구입니다.

## 1. Cocoapods 설치

- 아래 명령어 하나만 입력하시면 됩니다!

```swift
sudo gem install cocoapods 
```

## 2. Pod 설치

CocoaPods을 통해 가져올 수 있는 라이브러리를 Pod라고 합니다. 

내가 진행하고 있는 파일 경로에서 Podfile을 생성해줍니다. 

```swift
pod install 
```
![01.png](/assets/images/posts/ios/cocoapods/01.png)

## 3. Podfile에 수정

저는 nano 편집기를 사용하여 Podfile을 열어줬습니다. vi편집기를 사용해도 상관 없습니다. 

  저는 Podfile에 alamofire라는 네트워킹 라이브러리를 의존성을 추가해줬습니다.

![02.png](/assets/images/posts/ios/cocoapods/02.png)

```swift
 'Alamofire', '~> 5.2'
```

![03.png](/assets/images/posts/ios/cocoapods/03.png)

## 4. 터미널에서 pod install 실행

pod install 까지 실행하셨다면 디렉터리에 새로운 프로젝트가 생겨났는데 

여기서부터 주의하셔야 할 점은 앞으로 .xcworkspace라는 확장자 파일을 실행하여 프로젝트를 진행하셔야 합니다. 

![04.png](/assets/images/posts/ios/cocoapods/04.png)

흰색 프로젝트 파일을 실행하면  Alamofire import가 잘 적용되는 것을 확인할 수 있습니다!

![05.png](/assets/images/posts/ios/cocoapods/05.png)

![06.png](/assets/images/posts/ios/cocoapods/06.png)

앞으로 다른 라이브러리들도 사용하고 싶으시면 podfile에 위와같은 방법으로 추가해주시면 됩니다!  
그럼 오늘은 여기까지 cocoapod 설치 및 실행법에 대해 알아봤습니다!! 

추가로 틀린 부분 있으면 언제든지 댓글 달아주세요!

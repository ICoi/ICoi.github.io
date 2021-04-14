---
layout: post
title: "Swift Package Manager 활용 (1) 외부 라이브러리 의존성 관리"
author: "Daun Joung"
tags: ["SwiftPackageManager","SPM","iOS","Xcode"]
---

# Swift Package Manager 활용 (1) 외부 라이브러리 의존성 관리

## Swift Package Manager(이하, SPM) 란?
Swift로 작성된 코드의 Package의 배포, 적용 및 의존성을 관리하는 Manager로 활용되는 기능으로 설명하자면 아래와 같다.
1. CocoaPods을 대체하는 기능을 제공
2. Swift로 작성된 코드들의 프로젝트를 대신함 (Xcode Project를 대신함)

해당 글에선 언급된 기능 중 1번 CcoaPods을 대체하는 의존성 관리 측면에서 활용한 내용에 대해 작성하며, 2번에 해당하는 프로젝트 대신하는 기능은 언젠가 작성할 예정입니다.


## 과거의 외부 라이브러리 의존성 관리는?
외부 라이브러리를 다운받고, 해당 라이브러리 적용에 필요한 설정들을 자동으로 적용하고, 외부 라이브러리 버전 업데이트 하는 모든 복잡한 과정을 CocoaPods을 활용하여 관리를 하는 것이 일반적이었다. 
과거 수동으로 진행하던 것에 비하면 CocoaPods를 사용하는 것은 확실히 편리하긴 했지만 굳이 단점이라면 pod install과 같은 명령어를 프로젝트 외부에서 수행해야한다는 것과, XCodeProject 가 아닌 xcworkspace 확장자를 가지는 워크스페이스를 사용해야만 한다는 점... Apple에서 정식으로 제공되는 프로그램이 아니다보니 어쩔 수 없이 Xcode 외부에 별도의 설치 및 수행 과정을 거치는 아주 소소한 번거로움이 있다.

##  SPM 도입 이유?
이번 친구들과 개발하는 프로젝트에는 CocoaPods 대신 SPM을 활용하기로 했다.  그 이유는 거창한 무엇도 아닌 외부 프로그램 설치를 안해도 되고, XCode 내에서 할 수 있다는 점. ~~그리고 회사에서는 못해볼거 같아서..?~~

## SPM 활용 방법
SPM 활용 방법은 매우매우매우 쉽다.
1. 외부 라이브러리의 저장소 URL을 확인합니다.
ex) Alamofire의 경우 github 주소인 https://github.com/Alamofire/Alamofire
2. Xcode 메뉴에서 File -> Swift Packages -> Ad Package Dependency...  메뉴 선택
<img src="https://github.com/ICoi/ICoi.github.io/blob/master/images/202010328_SPM_1.png?raw=true" width="100%">
3-1. 가져올 라이브러리의 저장소 URL을 입력 후 Next
<img src="https://github.com/ICoi/ICoi.github.io/blob/master/images/202010328_SPM_2png?raw=true" width="100%">
3-2. 적용할 외부 라이브러리의 버전, 브랜치 명 혹은 커밋 해쉬값을 입력 후 Next
<img src="https://github.com/ICoi/ICoi.github.io/blob/master/images/202010328_SPM_3png?raw=true" width="100%">
3-3. 실제 프로젝트에서 필요한 라이브러리만 선택 한 뒤 Next
<img src="https://github.com/ICoi/ICoi.github.io/blob/master/images/202010328_SPM_4png?raw=true" width="100%">

혹시 추가한 라이브러리들을 제거 하거나 버전 편집이 필요하면 Project 타겟 선택 후 info 의 Package 항목에서 편집 및 삭제가 가능하다.
<img src="https://github.com/ICoi/ICoi.github.io/blob/master/images/202010328_SPM_5png?raw=true" width="100%">

## SPM 사용 후기
SPM 을 활용하는 것은 걱정 이상으로 너무 쉽고 간편했다. 평소 프로그램 설치시마다 남들은 겪지 않는 온갖 문제를 겪어 오는지라 무언가 설치 하는 것에 두려움이 있는데, 항상 사용하던 XCode 내에서 쉽고 편하게 할 수 있으니... 앞으로 다시는 CocoaPods으로 되돌아가지 않을것 같다는..

## 다음 과제
라이브러리를 제작하여 SPM을 통해 배포해보기.

# Carthage (카르타고)



## Carthage?

카르타고는 swift 디펜던시 매니저입니다.

코코아팟과 동일한 목적으로 개발되었습니다만, 차이점은 컴파일 타이밍이 다릅니다.

마치 코코아팟은 컴파일 할 때 불편할래, 카르타고는 처음에 한번 불편하고 빨리 할래..?



프로젝트에 코드를 추가해서 컴파일 하는 방법이 아닌 바이너리 파일을 등록해서 사용하는 방법을 취하고 있습니다.

- [공식 Github](https://github.com/Carthage/Carthage)

# 설치

- **Installer:**  `Carthage.pkg`  [release](https://github.com/Carthage/Carthage/releases) 패키지 파일을 바로 받는 방법

- **Homebrew:**  [Homebrew](http://brew.sh/) 를 설치한 뒤 `carthage` 을 설치하는 방법

  ```
  $ brew update
  $ brew install carthage
  ```



## 사용법

Cocoa pod 의 Podfile 처럼 Cartfile 이라는 것을 만들어서 활용할 라이브러리를 추가합니다.

```

```



## 업데이트

Cartfile 이 만들어지면 

```
$ carthage update
```

를 하면 디펜던시 파일을 받아온다.



특정 플랫폼이나 라이브러리를 한정해서 사용할 수 있다.

```
$ carthage update --platform iOS
$ carthage update LibraryName
```



## 프로젝트에 적용

`/Carthage/Build/iOS/` 내부에 있는 `framework` 파일을 이용한다.

- 프로젝트를 열고 Build Parse로 간다.
- Link Binary With Libraries 에 `.framwork` 파일을 추가한다.
- Run Script 에 `/usr/local/bin/carthage copy-frameworks` 를 입력하고
- Input Files `$(SRCROOT)/Carthage/Build/iOS/LibraryName.framework` 을 모두 추가한다.





## 라이브러리 배포하기

- 라이브러리에 걸려있는 종속성을 Cartfile 에 만들어줍니다.
- *중요!* 코코아팟과 관련된 것을 모두 지워줍니다.
  - 코코아팟이 없어져도 코코아팟은 코드 자체를 배포하는 것이므로 코코아팟 배포에는 아무런 문제가 없습니다.
  - 코코아팟으로 불러오고 있는 종속성을 카르타고로 변경하세요.
  - Pod 과 관련된 것을 삭제하세요. Build Pharse 에도 은근 run script 가 남아있을 수 있습니다.
- 준비가 되었다면 다음 명령어를 입력합니다.

```
$ carthage build --no-skip-current
```

- 빌드가 정상적으로 완료되었다면 Git 에 업로드합니다.
- 라이브러리를 사용할 프로젝트로 돌아와서 Cartfile 에 추가합니다.

```
github "woowabros/applog" "carthage"
```



- 위와 같이 특정 브랜치를 참조할 수도 있습니다.
- `carthage update applog`  로 업데이트 합니다.


- 문제가 있다면 log 파일을 참조합니다.
- Pod 관련 문제가 있다면 Pod 이 제거되지 않은 부분을 찾아서 다시 시도합니다.
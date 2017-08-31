# MVVM

- 예제 앱 : [킥스타터](https://github.com/kickstarter/ios-oss/tree/master/Kickstarter-iOS) 오픈소스 앱

  ​

  ![MVVM 패턴](https://i-msdn.sec.s-msft.com/dynimg/IC564167.png)

- Model - View - ViewModel

- 사용자 인터페이스 컨트롤과 해당 로직 간의 명확한 분리를 제공하는 것이 목적

- MVC 는 가장 널리 사용된 코딩 패턴이자 iOS 개발에서도 자주 쓰이는 패턴이다. Model 과 View를 완전히 분리시켜 재사용성을 높이고, 각각의 역할을 분명히 하여 스파게티 코드를 방지하는 것이지만, Model 에 넣기도 애매하고 View에 넣기도 애매한 것들이 Controller 에 들어가면서 Controller 가 비대해지는 단점이 있다. 이를 해결하기 위해 MVVM 이 대안으로 제시되고 있음



### MVVM 이란?

- Controller 는 더 이상 Model 에 말을 걸 수 없다. View Model 을 통해서 전달한다.
- Model 과 ViewModel이 하나의 짝을 이루고, View와 Controller가 짝을 이룬다.
- View Model은 Presentaion Logic 을 다루지만 UI는 다루지 않는다. (UIKit Import 금지)



### RxSwift 를 이용한 MVVM

- 일반적으로 iOS에서 객체 간 소통하는 방법은 Callback, Delegate, Notification 3가지 방법이 있는데, Async한 환경에서 객체가 업데이트된 상황을 객체 간 전달할 수 있다.
- RxSwift 는 Observable 한 패턴을 사용하기 때문에 더 간결하고 강력한 기능을 제공할 수 있다.
- 따라서 MVVM 과 RxSwift 는 쿵짝이 잘 맞는다.









### 참고자료

(영문) [MVVM 과 Swift](http://artsy.github.io/blog/2015/09/24/mvvm-in-swift/)
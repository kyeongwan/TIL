# NSUserDefaults



- Android 의 SharedPreference 처럼 간단한 정보를 저장하는 곳이다.
- Swift 부터는 UserDefaults 로 네이밍이 변경되었다. [링크](https://developer.apple.com/documentation/foundation/userdefaults)



```objective-c
// swift3
UserDefaults.standard.set(true, forKey: key) // save
UserDefaults.standard.bool(forKey: key) // load

// obj-c
NSUserDefaults *userDefaults = [NSUserDefaults standardUserDefaults];
id val = [userDefaults objectForKey:key]; // load
[userDefaults setObject:val forKey: key]; // save
```





## 이슈

- 9.3 에 간혈적으로 데이터가 사라지는 버그가 있다. ([포럼](https://forums.developer.apple.com/thread/44264))
- 애플은 iOS 11 에서 이 문제를 해결했다는 리포트를 내놨다. ([리포트](https://developer.apple.com/library/content/releasenotes/Foundation/RN-Foundation/index.html))

```
NSUserDefaults Data Loss Fix

Starting in iOS 9.3, and in subsequent releases of iOS and macOS, NSUserDefaults could fail to load data if more than roughly 250 separate apps (including separate reinstalls of the same app) had been launched since the last reboot. This has been corrected.
```



## 해결책

- 용량이 크면 날라갈 가능성이 있다.
- 간혈적으로 증발할 수 있다.
- 가급적 중요한 데이터는 이 곳에 저장하지 말자...
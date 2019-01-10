# KeychainWrapper

iOS Keychain Wrapper

* 기본적으로 디바이스를 잠그면(Lock) Keychain 역시 잠기고 디바이스를 풀면(Unlock) Keychain 역시 풀린다. 이렇게 Keychain이 잠긴 상태에서는 Item들에 접근할 수도 복호화할 수도 없고 또한 풀린 상태에서도 해당 Item을 생성하고 저장한 어플리케이션에서만 접근이 가능
* UserDefaults는 단순 데이터 저장하는데는 문제 없지만 해킹을 통해서 UserDefaults값을 얻을 수 있기 때문에 민감한 정보(비밀번호, 인증서)드을 저장하기에는 안전하지 못하다
* App uninstall시에 keychain은 정보가 남지만 UserDefaults는 삭제된다.

* Reference Site</br>
https://www.raywenderlich.com/9240-keychain-services-api-tutorial-for-passwords-in-swift?utm_campaign=rw-weekly-issue-199&utm_medium=email&utm_source=rw-weekly

```swift
do {
    try secureStoreWithGenericPwd.setValue("pwd_1234", for: "genericPassword")
    let password = try secureStoreWithGenericPwd.getValue(for: "genericPassword")
    XCTAssertEqual("pwd_1234", password)
} catch (let e) {
    XCTFail("Reading generic password failed with \(e.localizedDescription).")
}
```

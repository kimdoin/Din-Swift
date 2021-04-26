#  Data Type(자료형)

### 1. Int
* `Int` Signed정수형: 음수와 양수  범위 모두 저장 가능(정수형의 기본 자료형)
* `UInt` Unsinged정수형: 0과 양수만 저장 가능

### 2. Float, Double
* 실수를 저장할 땐 지수와 가수를 나눠서 저장하기 때문에, 동일한 메모리 크기에서 정수에 비해 더 넓은 범위를 표현할 수 있다.
* 부동 소수점 오차로 인해 100% 정확하게 저장할 수 없다.
* `Float` 크기는 32bit(4byte)이며, 소수점 6자리까지 정확하게 저장할 수 있는 타입
* `Double` 크기는 64bit(8byte)이며, 소수점 15~16자리까지 정확하게 저장할 수 있는 타입
```swift
let a: Float = 1.234567890123456 // 1.234568
let b: Double = 1.2345678901234567890 // 1.234567890123457
```
### 3. Bool
* `Bool`은 true/false 두 가지 종류의 값만 가질 수 있는 자료형을서 주로 논리값을 저장하기 위해서 사용하는 타입
* 보통 조건문의 결과를 표현하는데 많이 사용
```swift
let success: Bool = true
let fail: Bool = false
```

### 4. String
* `String`타입은 문자열을 저장할 때 사용하는 타입
* `String`은 `Int`와 더불어서 프로그래밍에서 가장 많이 사용되는 자료형이기도 함.
* `String` 타입 데이터의 값을 표현할 때는 `""(큰따옴표)`를 사용해서 표현
```swift
let str: String = "Hello"
let language = "Swift"
let name = ""
```

### 5. Character
* `Character` 한 개의 문자를 저장할 수 있는 단일 자료형
* `String`타입과 마찬가지로 `""(큰따옴표)`를 사용해서 값을 표현
* `Character`을 사용할 때는 반드시 `character`타입의 자료형을 선언해줘야 함.
```swift
let a: Character = "H"
let b: Character = " "
```


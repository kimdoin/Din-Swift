# 1. Function
> `Function`은 프로그램의 실행 과정 중에서 독립적으로 처리될 수 있는 부분을 분리하여 구조화한 객체를 의미한다.
* Function은 특정 기능을 수행하는 코드 조각이다.
* 자주 사용하는 기능을 Function로 만들어두면, 언제든지 다시 사용할 수 있다.
* Parameter와 return 값을 생략할 수 있다.
* Function의 parameter는 하나도 없을 수도 있고, 하나 이상일 수도 있다.
* 코드를 변경해야 할 때 함수 내부만 수정하면 되므로 유지 보수가 용이하다.
* Function를 만들 때 함수 이름은 lowerCamelCase로 만들고, 직관적인 이름을 사용하는 것이 좋다.

```swift
func name(parameters) -> ReturnType { // function Head
    statement // function body
}
name(parameterts) // 함수 호출
```
### < 매겨변수와 리턴값이 없는 함수 >
```swift
func printHello() {
    print("안녕하세요")
}
printHello() // 안녕하세요
```

# 2. Return Value
* Function에 return Type이 선언되어 있다면 return 다음 표현식을 평가 후 그 결과를 return한다.
* Return Type이 지정되면 반드시 그 타입에 맞는 값을 return해야 한다.
* nil을 return하려면 Function의 return Type이 반드시 Optional Type으로 정의되어 있어야 한다.
* Function 호출식이 표현식이고, Function가 리턴하는 값은 표현식의 결과가 된다.

```swift
func add() -> Int {
    return 10 + 20
}
add() // 30

func sayHello() -> String {
    return "반가워요"
}
sayHello() // 반가워요

func doSomething() {
    let r = Int.random(in: 0...100) // 1~100까지의 랜덤 숫자 생성
    
    if !r.isMultiple(of: 2) {
        return // r이 홀수이면 함수의 실행을 중지
    }
   
    print(r)
}
doSomething()
```

# 3. Parameter
* 함수로 전달하는 값을 Parameter라고 한다.
* Parameter는 함수 Body에서 사용할 수 있는 **임시 상수**다.
* Parameter는 함수가 실행될 때 실행되고, 실행이 완료되면 자동으로 삭제된다.
* Parameter에 기본값을 지정할 수 있고, 기본값을 가지고 있다면 생략이 가능하다.
* Parameter의 스코프는 함수 Body로 제한된다.
```swift
func name(매개변수: 자료형...) {
    statement
}

func add(a: Int, b: Int) -> Int {
    // ex) a = 10 파라미터는 함수 바디에서 사용할 수 있는 임시 상수입니다. 값 변경 불가!
    return a + b
}
add(a: 10, b: 20) // 30

func echo(message: String, newline: Bool = true) { // 기본값 저장 
    if newline == true {
        print(message, true)
    } else {
        print(message, false)
    }
}
```

# 4. Argument Label
* Parameter의 가독성을 높이기 위해서 사용한다.
* `_`를 사용해서 생략할 수 있다.
* Argument Label은 함수를 호출하기 위해 사용하는 이름이기 때문에, 함수 안에서 parameter에 접근하기 위해 사용할 수 없다.
```swift
func printHello(name: String, msg: String) {
    print("\(name)님, \(msg)")
}
printHello(name: "동구", msg: "안녕하세요") // 동구님, 안녕하세요

func printHello(to name: String, welcome msg: String) {
    print("\(name)님, \(msg)")
}
printHello(to: "동구", welcome: "안녕하세요") // 동구님, 안녕하세요

func sayHello(_ name: String) { //Argument를 와일드카드 패턴으로 생략.
    print("Hello, \(name)")
}
sayHello("Swift") // Hello, Swift
```

# 5. Variadic parameter
* Variadic parameter에서는 하나 이상의 argument를 전달할 수 있다.
* Argument는 배열 형태로 전달된다.
* Variadic parameter는 개별 함수마다 하나씩만 선언할 수 있다.
* Variadic parameter 기본값을 가질 수 없다.

```swift
func sum(_ nums: Int...) {
    var sum = 0
    for num in nums {
        sum += num
    }
    print(sum)
}
sum(1, 2, 3, 4, 5) // 15 Argument 5개
```
# 6. In-Out Parameters
* inout 키워드를 통해 argument로 전달된 변수의 값을 직접 바꿀 수 있다.
* 기본값을 사용할 수 없고, Variadic Parameters를 사용할 수 없다.
```swift
func update(value: inout Int) {
    value = value * 2
    print(value)
}
  
var a = 100
update(value: &a) // 200
```

# 7. First-class citizen
* 함수는 First-class citizen으로 활용할 수 있다.
* 변수나 상수에 저장할 땐 argument값을 전달하지 않도록 조심해야 한다. 
* 변수나 상수에 저장된 함수를 호출할 땐, argument Label을 생략한다.

```swift
func add(num1: Int, num2: Int) -> Int {
    return num1 + num2
}

var a: (Int, Int) -> Int = add(num1:num2:)
a(1, 2)

// Returns: 3
// 변수나 상수에 저장된 함수를 호출할 땐, argument Label을 생략한다.
```

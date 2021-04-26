# 1. Closures
* `Closure`는 비교적 짧고 독립적인 코드 조각이다.
* `Closure`에는 Function, Nested Function, Anonymous Function이 있다.
* Named Closures에는 Function과 Nested Function이 있다.
* Anonymous Function를 Unnamed Closure, 익명함수라고 한다.
* 자료형(Type)을 표현하는 방법은 함수와 완전히 동일하다. Function과 Closure는 서로 호환된다.
* Global Scope에서 단독으로 작성할 수 없기 때문에 상수나 변수에 저장해 사용해야 한다.
* **Closure를 호출할 땐 Argument Label을 사용하지 않는다.**
```swift
{ (parameters) -> ReturnType in
    statements
} 

{ statements } // 가장 단순한 클로저 표현식

let a = { print("Hello, blog") }
a() // Hello, blog

// 파라미터와 리턴형이 있는 클로저
let a2 = { (str: String) -> String in
    return "Hello, \(str)" // str은 파라미터 이름입니다.
}
let call = a2("blog")
print(call) // Hello, blog

// 클로저를 파라미터로 전달
typealias strClosure = (String) -> (String)
func printHello(closure: strClosure) {
    print(closure("iOS"))
}

printHello { (str: String) -> (String) in
    return "Hi, \(str)"
} // Hi, iOS
```


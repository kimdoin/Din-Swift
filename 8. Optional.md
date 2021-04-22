## **Index**

# 1. Optional

##**< Optional Type >**
* 옵셔널은 값을 가지지 않아도 되는 형식입니다.
* Non-optional Type 뒤에 `?`를 붙여준다.
* `nil`은 값이 없다는 것을 나타내는 특별한 키워드입니다.
* `nil`은 추론할 수 있는 형식이 없기 때문에, 꼭 Type annotation으로 타입을 지정해주어야 한다.

```swift
name: Type? // 타입 뒤에 물음표(?)를 붙여주면 옵셔널 타입이 됨.

var optionalNum: Int? // nil, 옵셔널 Int라고 읽는다.
var str: String = "iOS" // Non-optional Type은 항상 값을 가져한다.
```

# 2. **< Unwrapping >**
* Optional에 저장된 값을 추출하는 과정을 Unwrapping이라고 한다. Unwrapping하면 Non-optional Type으로 결과가 return된다.
* Optional Type에 저장된 값을 사용하려면 반드시 Unwrapping해야 한다.
* Optional 해제 방식은 `명시적 해제(강제 해제)`와 `묵시적 해제(비강제적인 해제)`로 나누어집니다.

#### < Forced Unwrapping >
* Optional Expression 뒤에 `!`문자를 사용해서 강제추출한다.
* **nil(값이 없음)이 저장되어있을 때 강제추출하면 Crash가 발생**한다.
* 강제 추출을 사용할 때는 Optional 값이 `nil`인지 아닌지 확인해야 합니다.
```swift
var num: Int? = 10
print("옵셔널 자체의 값 : \(num)") // 옵셔널 자체의 값 : Optional(10)
print("강제 추출한 값 : \(num!)") // 강제 추출한 값 : 10


var nilNum: Int?
print("옵셔널 값 : \(nilNum)") // nil
print(nilNum!) // 에러!
```
# 3. < Optional Binding >
* Optional Binding을 사용하면 안전하고 직관적으로 Unwrapping할 수 있습니다.
* Optional Binding은 조건문 내에서 일반 상수에 Optional 값을 대입하는 방식으로 이루어집니다.
* Optional Binding은 표현식을 평가한 후 값이 반환되면 Unwrapping하여 변수나 상수에 저장합니다.
* Optional Expression에서 nil(값이 없음)이 반환되면 Binding이 실패하고 다음 문장으로 제어를 전달합니다.
* if문, while문, guard문에서 사용할 수 있습니다.

```swift
if let name: Type = OptionalExpression { // let name: Type = OptionalExpression 이 부분을 바인딩이라고 부른다.
    statement
}
while let name: Type = OptionalExpression {
    statement
}
guard let name: Type = OptionalExpression else {
    statement
}
```

```swift
var str: String? = "Hello"

guard let str = str else { // 여기서 바인딩된 상수는 else블록 다음에서 사용할 수 있습니다.
    fatalError()
}  // 값을 리턴하는 경우에만 Unwrapping하기 때문에 강제추출과 같은 에러는 발생하지 않습니다.
str // Hello

var num: Int? = nil

if let num = num {
    print(num)
} else {
    print("fail")
} // fail
```

# 4. < Implicitly Unwrapped Optional(IUO)>
* `IUO`는 자료형 이름 뒤에 `!`를 붙여준다.
* Type Annotation으로 타입을 직접 정해 준 경우 값이 자동으로 추출된다.
* nil이 저장되어 있는 상태에서 강제로 추출하면 에러가 발생한다.
* 변수의 값이 nil이 될 가능성이 있다면 IUO를 사용하지 않아야 한다.
* IBOutlet에서 사용하는 이유는, 연결되지 않은 Outlet을 컴파일 시점에서 미리 발견하기 위해서 사용한다.
```swift
var str: String! = "Swift"
str

var num: Int! = 12
num
```

# 5. Nil-Coalescing Operator
* `Nil-Coalescing Operator`를 사용하면 값이 저장되어 있는지 확인하는 코드와 값을 추출하는 코드를 직접 작성할 필요가 없다.
* 이항 연사자, 단락평가로 처리하기 때문에, 오른쪽 피연산자에는 Side Effect가 발생하는 코드가 오면 안된다.
* Optional Binding을 한 줄로 줄이고 싶을때 사용한다.
* A ?? B -> OptionalExpression ?? Expression
* 단락 평가를 실시, 값이 있다면 좌측 값, 값이 없다면 우측 값을 반환.
* 왼쪽에 있는 피연산자에 값이 저장되어 있는지 확인하고 값을 반환한다면 값을 Unwrapping 한 다음 연산의 결과를 반환.

```swift
var str: String! = nil

var result = "확인결과" + (str ?? "nil")
print(result) // 확인결과 nil
// -------
var name: String? = "Din"
let non = "Whatever."

print("Hello, " + (name ?? non))
// prints : Hello, Din.

name = nil

print("Hello, " + (name ?? non))
// prints: Hello, Whatever.
```

# 6. Optional Chaining
* Optional Chaining의 결과는 항상 Optional이다.
* Optional에 값이 저장되어 있다면, 이어지는 속성에 접근한다.
* Optional Chaining에 포함된 식이 nil을 return한다면 이어지는 표현식을 평가하지 않고 nil을 리턴한다.
* Optional Chaining의 타입은 마지막 표현식의 타입으로 결정되고, 항상 Optional로 return된다.
* Optional 표현식을 통해서 속성에 접근하거나 메소드를 호출할때는 반드시 표현식 뒤에 `?`를 사용한다.
* 딕셔너리가 Optional이고 Key를 통해 값을 얻어야 할 땐, `[]`앞에 ?를 사용하고, 서브스크립트가 리턴하는 값을 통해서 속성에 접근하거나 메소드를 호출해야 할 땐, `[]`뒤에 ?를 사용해준다.

```swift
let dictionary: [Int: String]? = [1: "One", 2: "Two"]

dictionary?[1]
// "One"(Key 1의 Value = "One"): Key를 통해 값 "One"에 접근해야 할 때

dictionary?[1]?.count
// 3(문자열 One의 count = 3): 서브스크립트를 통해 속성에 접근해야 할 때
```


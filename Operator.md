# 1. 연산자
* **연산자 기초 이론**
  - `a + b` 연산에 사용되는 + 문자를 연산자(영어로는 Operator)라고 하고, 계산에 사용되는 값(a와 b)를 피연산자(Operand)라고 한다. 프로그래밍    언어에선 문자열을 더할 수도 있고, 직접 만든 자료형에서 연산을 구현할 수 있다.
  - `Unary Operator(단항 연산자)` 하나의 피연산자 앞뒤에 사용하는 연산자.
  ```swift
  +a // 올바른 문법
  + a // 잘못된 문법
  // 단항연산자를 사용할 경우 연산자와 피연산자 사이에 공백이 없어야 한다.
  ```
  - `Binary Operator(이항 연산자)` 두 피연산자 사이에 위차하는 연산자.
  ```swift
  a+b
  // 1. 애매한 문법
  a + b
  // 2. 올바른 문법
  a+ b
  // 3. 잘몬된 문법
  // 이항연산자를 사용할 경우 연산자와 피연산자 사이에 공백이 같아야 한다.
  // 사이 공백을 주지 않아도 되지만, 가끔 오류가 날 수 있으므로 2번째 예시가 권장.
  ```
  - `Ternary Operator` 피연산자가 세 개인 연산자.
  ```swift
  a ? b : C

  // 양쪽에 공백을 한 칸씩 주어야 한다.
  ```
  - `Precedence(우선순위)` 연산자마다 우선 순위를 가지고 있다. 먼저 계산하고 싶은 식에 `() Parentheses`를 사용해서 우선 순위를 줄수 있다.
  - `Associativity(결합규칙)` 우선 순위가 없을 경우 좌결합성(왼쪽에서 오른쪽으로 계산)
  - 오른쪽 -> 왼쪽 (우결합성)이라 한다.
  - 연산자 위치에 따라 연산자가 앞에 있다면 전치 연산자(prefix), 뒤에 있다면 후치 연산자(postfix), 안쪽에 있다면 중위 연산자(infix)라고 부른다.

# 2. Arithmetic Operator
* +, - , / , *, % 계산을 수행하는 연산자입니다.
* 연산자를 사용할 땐 공백이 중요.
* 나머지 연산자는 실수를 지원하지 않는다.
* 나머지 연산자에서 실수를 계산할 때는 truncatingRemainder 메소드를 사용해야 한다.
* 나누기 연산자는 정수와 실수를 둘 다 지원한다.

```swift
let a = 10
let b = 20

a + b // 30
a - b // -10
a * b // 200
a / b // 0
a % b // 10

a + b // o
a+b // o
a+ b // x 앞 뒤 공백을 일치시켜야 합니다.

let c = 12.5
let d = 20.7

c.truncatingRemainder(dividingBy: d)
```
### <**Overflow**>
* Overflow는 자료형에 저장할 수 있는 값의 범위를 초과하는 것을 말한다.
* Swift는 기본적으로 Overflow를 허용하지 않지만, 특정 패턴을 구현하기 위해 Overflow 연산자를 사용한다.
* 연산자 앞에 &를 붙여 사용
* &+, &-, &*
```swift
let a: Int8 = Int8.max  // 127
let b: Int8 = a &+ 1  // -128
```

# 3. Comparsion Operator
* 비교 연산자는 이항 연산자이고, 결과는 항상 Bool(true/false)이다.
* 피연산자의 자료형을 일치시켜야 한다.
![](https://images.velog.io/images/din0121/post/bbf09b7e-f42a-4328-aa57-fe1da72b0f71/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-04-20%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%201.09.46.png)

# 4. Logical Operator
* 참과 거짓을 구분하는 연산자이고, 피연산자는 항상 Boolean 표현식이어야 한다. 연산의 결과는 항상 Bool이다.
* `!` Logical Not Operators (논리 부정 연산자)로 참을 거짓으로, 거짓을 참으로 바꿔준다. 전치 연산자로만 사용.
* `&&` Logical And Operators로 모든 피연산자가 true일때만 true가 리턴이 되고 나머지 경우에는 모두 false로 리턴이 된다.
* `||` Logical OR Operators로 하나의 피연산자가 true여도 true가 리턴이 된다.
* `Short-circuit Evaluation` 단락평가, 결과 도출에 필요한 최소한의 논리식만 평가하는 방식 ✨
* `Side Effect` 코드의 실행 결과로 인해, 값 또는 상태가 변경되는 것. 논리식에 Side Effect를 발생시킬 수 있는 코드가 포함되어 있는 경우, 논리적인 오류가 발생할 수 있기 때문에 조심해야 한다.

 ```swift
 && 연산자 
true && true // true
true && false // false
false && true // false
false && false // false

|| 연산자
true || true // true
true || false // true
false || true // true
false || false // false
 ```
# 5. Ternary Conditional Operator
* 삼항 연산자는 어떤 조건을 기준으로 두 개의 값 중에 하나를 선택할 때 사용합니다.
* 삼항 연산자는 Condition? expr1: expr2로 구성되어 있다.
* 조건에서 true가 리턴되면 expr1의 값이 도출
* 조건에서 false가 리턴되면 expr2의 값이 도출
* 두 번째 피연산자와 세 번째 피연산자의 자료형이 같아야 한다.
```swift
let weight = 70

weight > 80 ? "overweight" : "underweight"
```

# 6. Assignment Operator
* 할당 연산자는 값의 초기화, 변경 등 값을 할당할 때 사용하는 연산자
* 할당 연산자는 값을 리턴하지 않는다.
* 할당연산자를 기준으로 lvalue와 rvalue(대부분 literal)로 나뉜다.
* lvalue = 메모리 공간을 나타내는 값
* rvalue = 저장할 값을 나타내는 표현식

### **< 복합 할당 연산자 >**
```swift
a = a + b // a += b
a = a - b // a -= b
a = a * b // a *= b
a = a / b // a /= b
a = a % b // a %= b
```
# 7. Range Operator
* 값의 범위를 표현할때 사용하는 연산자.
* 닫힌 범위 연산자와 반 닫힌 범위 연산자 두 가지 종류가 있다.

### < 닫힌 범위 연산자 >
* lowerBound ... UpperBound , lowerBound와 UpperBound를 포함. 기본적으로 오름차순으로 표현.
```swift
1 ... 5 
1...5

5 ... 1 // 에러!
(1 ... 5).reversed() // 내림차순으로 변경
```
### < 반 닫힌 범위 연산자 >
* UpperBound가 포함되지 않습니다.

```swift
1 ..< 5
1 >..5 // 에러!!


let a = 1
let b = 10

for num in a...b {
    print(num)
}

for num in a..<b {
    print(num)
}
```



# 1. 반복문
* **for-in 반복문**
* **while 반복문**
* **제어전달문**

-------------

## 1. for-in 반복문

* 일정 횟수만큼 특정 구문을 반복하고자 할 때 `for-in` 반복문을 사용합니다.
* for-in 반복문 내부에서 반복 상수를 사용하지 않을 경우, _ 문자로 생략할 수 있다. 이런 패턴을 wildcard pattern이라고 한다.

```swift
for loopConstant in Range {
statements
}
/*
loopConstant는 반복 상수라고 하고, 반복 상수는 값을 변경할 수 없다. 
*/

for _ in 1...5 {
	print("hello")
}

// for in 반복문 내부에서 반복상수를 사용하지 않아, _ 문자로 생략했다.
```

### <구구단 출력> 
```swift
for i in 2...9 {
    print("")
    print("\(i)단")
   
    for j in 1...9 {
        print("\(i) * \(j) = \(i * j)")
    }
}
```

### <합 구하기>
```swift
var sum = 0

for num in 1...100 {
    sum += num
}
print(sum) // 5050

sum = 0
for num in 1...100 {
    if num.isMultiple(of: 5) {
        sum += num
    }
}
print(sum) // 1050

sum = 0
for num in stride(from: 0, to: 101, by: 5) {
    sum += num
}
print(sum) // 1050

for num in stride(from: 5, to: 0, by: -1) {
    print(num)
} // 5,4,3,2,1
```

## 2. while 반복문
* 조건에 따라서 반복 여부를 결정한다. 조건이 true일 경우 코드를 반복.
* 조건에 따라서 반복 여부를 결정하기 때문에, 무한루프에 빠지지 않도록 조심해야 한다. 만약 condition이 계속 true일 경우 계속 반복하기 때문에, 특정 시점에서는 반드시 false로 바뀌어야 한다.

```swift
while condition {
    statement
}
```

```swift
var n = 2
while n < 1000 {
    n = n * 2
}
n // 1024

while true {
    print("무한루프")
} // 실행x, 무한루프입니다!
```

### < repeat- while >
* repeat-while while 반복문과 다르게 코드를 먼저 실행한 다음, 조건을 판단한다.
* 실행 블록의 수행을 최소 한 번은 실행합니다.
* condition이 true로 평가되면 다시 블록을 실행하고, false 이면 반복문을 종료합니다.

```swift
repeat { // 문법
  statement
} while condition 
```

```swift
// while문과 repeat-while문의 차이

var num = 100

while num < 100 {
  num += 1
}

print(num) // 100

/*
while문의 condition이 false로 평가되어 코드블록이 실행되지 않고 while문이 바로 종료된다.
이어지는 print함수가 호출된다.
*/

var num = 100

repeat {
  num += 1
} while num < 100

print(num) // 101

/* 일단 condition에 관계 없이 repeat코드블록을 실행한다. 그 다음, 조건을 평가한다.
```

## 3. 제어전달문
> 제어전달문은 영어로 Control Transfer Statement라고 부르고 ''흐름 제어 구문''이라고 부르기도 한다. 제어전달문은 조건문과 반복문에서 일반적인 코드의 흐름을 바꾸기 위해서 사용한다.

### **< break >**
* 현재 실행중인 문장을 종료하고, 이어지는 다음 문장으로 제어를 전달한다. (문장이 중첩되어 있을 경우 가장 인접한 문장만 종료한다.)
* 반복문과 switch문에서 사용한다.
```swift
for hello in "안녕하세요" {
    if hello == "세" {
        break
    }
    print(hello)
}
// 안,녕,하 
```

### **< continue >**

* 현재 실행중인 반복을 중지하고 다음 반복으로 제어를 전달(다음 반복을 시작)한다. 반복문에서만 사용한다. 가장 인접한 문장에만 영향을 준다.
* 블록 마지막에 있으면 의미가 없다.

```swift
for num in 0...5 {
    if num.isMultiple(of: 2) {
    continue
  }
  print(num)
} 
// 1, 3, 5

/*
짝수인 경우 continue를 사용했기 때문에 홀수만 출력된다.
for in 반복문은 지정한 대로 0부터 5까지 6번 반복되었다.
*/
```

### **< fallthrough >**
* 해당 코드블럭에 있는 바로 다음 코드를 무조건 실행한 다음 종료한다.

### **< Labeled Statement > **

* 문장에 이름을 붙이는 것.
* break, continue와 함께 사용되며 반복문, if문, switch문에서 주로 사용됨.
* Label을 전달하면 가장 인접한 문장을 제어하는 게 아니라, 동일한 Label을 가진 문장을 제어한다.
```swift
outer: for i in 1...3 {
	print("OUTER LOOP", i)
	
	for j in 1...3 {
		print("		inner loop", j)
		
		break outer
	}
}

// OUTER LOOP 1
// 		inner loop 1
// for i in 반복문에 outer라는 label을 달아, 해당 문장을 직접 제어할 수 있다.
```

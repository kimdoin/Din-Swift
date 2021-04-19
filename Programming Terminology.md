# 1. 프로그래밍 기본 용어

### Token, Expression, Statement


  * Token(토큰) 더 이상 쪼갤 수 없는 프로그래밍 요소(Identifier, Keywords, Literals, 연산자 등)
  * Expression(표현식) 변수나 상수, 연산자, 함수 등이 모여서 하나의 값이 도출되게 하는 식
  * Statement(문, 문장) 하나 이상의 Expression이 모여 특정 작업을 실행하는 코드블록(반복문, 할당문, 흐름제어문, 반복문 등)
  
  
### Literal, Identifier, Keyword
* Literal(리터럴) 코드 내에서 의미가 변하지 않고 그대로 사용되는 값
* Identifier(식별자) 코드에 포함된 요소를 구별하기 위해 사용되는 이름
* Keyword(키워드) 특정 기능을 사용하기 위해 프로그래밍 언어가 미리 사용하고 있는 예약어

### Compile, Link
* Compile(컴파일) 우리가 입력한 코드를 컴퓨터가 이해할 수 있게 바이너리코드로 변환하는 것
* Link(링크) 이미 만들어져 있는 기능(라이브러리 등)을 우리가 만든 코드와 연결하는 것

### First Class Citizen
* 변수와 상수에 저장할 수 있다.
* 파라미터로 전달할 수 있다.
* 함수에서 리턴할 수 있다.

---------------------------

### Swift 데이터 저장 규칙

#### Naming Convention(이름 정의 규칙)
식별자의 이름을 정의할 때 따라야 하는 CamelCase라고 불리는 규칙.
* UpperCamelCase: 규칙 자체의 이름에서 보이듯이 식별자의 첫 단어는 대분자'U'로 지정되어 있고, 그 뒤에 CamelCase 같이 서로 상이한 단어들을 구분 짓기 위해서 각 단어의 시작을 대문자로 하고, 나머지 문자는 모두 소문자로 지정 
  * 클래스, 구조체, 열거형, 익스텐션, 프로토콜 이름
* lowerCamelCase: 항상 식별자의 첫 번째 문자는 소문자로 표기해야 하며, 나머지는 UpperCamelCase와 동일
  * 변수, 상수, 함수, 속성, 메소드, 파라미터 이름


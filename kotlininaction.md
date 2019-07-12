#Kotlin in action
1. 코틀린이란 무엇이며, 왜 필요한가?
2. 코틀린 기초
3. 함수 정의와 호출
4. 클래스, 객체, 인터페이스
5. 람다로 프로그래밍
6. 코틀린 타입 시스템
7. 연산자 오버로딩과 기타 관례

 9.  제네릭

## 1장 코틀린이란 무엇이며, 왜 필요한가?

코틀린은 자바 플랫폼에서 돌아가는 새로운 프로그래밍

간결하고 실용적이고, 자바 코드와의 **상호운용성**을 중시

현재 자바가 사용 중인 곳이라면 거의 대부분 코틀린을 활용할 수 있음. → 서버개발, 안드로이드 앱 개발

코틀린은 기존 자바 라이브러리나 프레임워크와 함께 잘 작동하며 성능도 자바와 같은 수준

- 코틀린의 주요 특성

    1. 대상 플랫폼 : 서버, 안드로이드 등 자바가 실행되는 모든 곳

    2. 정적 타입 지정 언어

    3. **함수형 프로그래밍**과 객체지향 프로그래밍

    4. 무료 오픈 소스

- 코틀린의 철학

    1. 실용성

    2. 간결성

    3. 안전성

    4. 상호운용성

- 요약

     코틀린은 타입 추론을 지원하는 **정적 타입 지정 언어(컴파일 시점)**

     → 소스 코드의 정확성과 성능을 보장하면서도 소스코드를 간결하게 유지할 수 있음. 

    - 코틀린은 객체지향과 함수형 프로그래밍 모두 지원→ 일급 시민 함수를 사용해 수준 높은 추상화가 가능하고, 불변 값 지원을 통해 다중 스레드 애플리케이션 개발과 테스트를 쉽게 할 수 있음.

    - 코틀린을 서버 애플리케이션 개발에 잘 활용 할 수 있음. → 기존 자바 프레임워크를 완벽하게 지원하는 한편,HTML 생성기나 영속화 등의 일반적인 작업을 위한 새로운 도구를 제공

    - 코틀린을 안드로이드에도 활용할 수 있음. 코틀린의 런타임 라이브러리는 크기가 작고, 코틀린 컴파일러는 안드로이드 API를 특별히 지원함.→ 코틀린의 다양한 라이브러리는 안드로이드에서 흔히 하는 작업에 사용할 수 있으면서 코틀린과 잘 통합될 수 있는 함수를 제공

    - 무료며 오픈소스, 주요 IDE와 빌드 시스템을 완전히 지원

    - 실용적이며 안전하고, 간결하며 상호운용성이 좋음 → 코틀린을 설계하면서 일반적인 작업에 대해 이미 잘 알려진 해법을 채택하고 NPE와 같이 흔히 발생하는 오류를 방지하며, 읽기 쉽고 간결한 코드를 지원하면서 자바와 아무런 제약 없이 통합될 수 있는 언어를 만드는데 초점

    ## 2장 코틀린 기초

    - 함수, 변수, 클래스 , enum, 프로퍼티를 선언하는 방법
    - 제어 구조
    - 스마트 캐스트
    - 예외 던지기와 예외 잡기
    - 함수

            fun max(a : Int, b:Int) : Int {
                return if(a>b) a else b // 블록이 본문
            }
             
             
            fun max2( a: Int, b:Int) : Int = if( a > b ) a else b // 식이 본문
            fun max3( a: Int, b:Int) = if(a>b) a else b // 식이 본문이면 리턴 타입 생략가능(타입추론)

        - 함수 선언은 fun 키워드로 시작- fun 다음에 함수 이름이 위치- 함수 이름 뒤에 괄호 안에 파라미터 목록 (파라미터 이름과 타입은 클론으로 구분하고, 각 파라미터는 콤마로 구분)- 본문 → 블록이 본문인 함수 : 중괄호로 본문을 둘러쌈 / 식이 본문인 함수 : 중괄호 대신 등호와 식

    - 변수

        **변수 선언의 예**

            // 타입 생략, 컴파일러가 초기화 식을 이용해서 유추
            val question = "코틀린"
            //30이 Int 타입이므로 answer1 타입을 Int로 유추
            val answer1 = 30
            // 타입 지정
            val answer2 : Int = 42
            // 초기화 식이 없으면 반드시 타입을 명시
            val answer3 : Int
            answer3 = 42

    - 변경 가능한 변수와 변경 불가능한 변수- val : 변경 불가능한 참조를 저장하는 변수 → 블록을 실행할 때 정확히 한번만 초기화돼야 함.- var: 변경 가능한 참조 → 자바의 일반 변수에 해당기본적으로는 모든 변수를 val키워드를 사용해 불변 변수로 선언하고, 나중에 꼭 필요할 때만 var로 변경하는 것이 좋음.

        **val 참조자체는 불변이지만, 그 참조가 가리키는 객체의 내부값은 변경될 수 있음**

        **var키워드 사용시 변수의 값을 변경할 수 있지만 변수의 타입은 고정돼 바뀌지 않음.**

            val languages = arrayListOf("Java") // 불변 참조를 선언
            languages.add("Kotlin") // 참조가 가리키는 객체 내부를 변경

    - 문자열 템플릿

        **문자열 템플릿 사용**

            // "Bob"을 인자로 넘기면 "Hello, Bob"을 출력하고 아무 인자도 없다면 Kotlin!을 출력
            fun main(args:Array<String>){
                val name = if(args.size>0) args[0] else "Kotlin"
                println("Hello, $name!")
            }

    - 클래스

        **[코틀린](http://wiki.i-screamedu.com/pages/viewpage.action?pageId=9245003) Person 클래스**

            // 코틀린의 기본 가시성은 public (생략가능)
            class Person(val name:String)

    - 프로퍼티자바에서는 필드와 접근자를 한데 묶어 프로퍼티라고 부르며, 코틀린은 프로퍼티를 언어 기본 기능으로 제공한다. val로 선언한 프로퍼티는 읽기 전용, var로 선언한 프로퍼티는 변경 가능

        **클래스 안에서 변경 가능한 프로퍼티 선언하기**

            class Person(
                // 읽기 전용 프로퍼티로, 비공개 필드와 필드를 읽는 단순한 게터를 만듬
                val name: String,
                // 쓸 수 있는 프로퍼티, 비공개 필드, 공개 게터, 공개 세터를 만들어 냄
                var isMarried : Boolean
            )

        **코틀린에서 Person 클래스 사용하기**

            //new 키워드를 사용하지 않고 생성자를 호출
            >>> val person = Person("Bob", true)
            // 프로퍼티 이름을 직접 사용해도 코틀린이 자동으로 게터를 호출
            >>> println(person.name)
            Bob
            >>>println(person.isMarried)
            true

    - 커스텀 접근자프로퍼티의 접근자를 직접 작성하는 방법

        **직사각형 클래스**

            class Rectangle(val height: Int, val width : Int){
                val isSquare:Boolean
                    get(){ // 프로퍼티 게터 선언
                        return height == width
                    }
            }

    - 선택 표현과 처리 : enum과 when when은 자바의 switch를 대치하되 훨씬 더 강력하다.단순히 값만 열거하는 존재가 아니고 enum 클래스 안에도 프로퍼티나 메소드를 정의할 수 있음.

        **간단한 enum 클래스 정의하기**

            enum class Color{
                RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET
            }

        when으로 enum 클래스 다루기

        **when을 사용해 올바른 enum 값 찾기**

            fun getMnemonic(color : Color) =
                //함수의 반환값으로 when 식을 직접 사용
                when(color){
                    // 색이 특정 enum 상수와 같을 때, 그 상수와 대응하는 문자열을 돌려줌.
                    Color.RED -> "Richard"
                    Color.ORANGE -> "Of"
                    Color.YELLOW -> "York"
                    Color.GREEN -> "Gave"
                    Color.BLUE -> "Battle"
                    Color.INIDIGO -> "In"
                    Color.VIOLET -> "Vain"
                }
             
             
            >>> println(getMnemonic(Color.BLUE))
            Battle

        → 자바와 달리 각 분기의 끝에 break를 넣지 않아도 되고, 성공적으로 매치되는 분기를 찾으면 switch는 그 분기를 실행

        → 한 분기 안에서 여러 값을 매치 패턴으로 사용할 수 있음 (그럴 때에는 값 사이를 콤마로 분리 )

    - when과 임의의 객체를 함께 사용 enum 상수나 숫자 리터럴만 사용할 수 있는 자바 switch와 달리 코틀린 when 의 분기조건은 **임의의 객체를 허용함.**

        **when의 분기 조건에 여러 다른 객체 사용하기**

            fun mix(c1: Color, c2 : Color) =
                //when의 인자로 아무 객체나 사용할 수 있다. 인자로 받은 객체가 각 분기 조건에 있는 객체와 같은지 테스트 함
                when(setOf(c1, c2)){
                    setOf(RED, YELLOW) -> ORANGE
                    setOf(YELLOW, BLUE) -> GREEN
                    setOf(BLUE, VIOLET) -> INDIGO
                    //매치되는 분기 조건이 없으면 이 문장을 실행
                    else -> throw Exception("Dirty color")      
            }

        **인자가 없는 when**

            fun mixOptimized(c1: Color, c2 : Color) =
                when { //when에 아무 인자도 없다.
                    (c1 == RED && c2 == YELLOW) ||
                    (c1==YELLOW && c2 == RED) ->
                        ORANGE
                    ...
                }

    - 스마트 캐스트 : 타입 검사와 타입 캐스트를 조합
    - 대상을 이터레이션 : while과 for 루프 코틀린 while 루프는 자바와 동일코틀린의 for은 for<아이템> in <원소들> 형태를 취함.
    - 맵에 대한 이터레이션

        **맵을 초기화하고 이터레이션 하기**

            val binaryReps = TreeMap<Char, String>() //키에 대해 정렬하기 위해 treemap을 사용
             
             
            for(c in 'A'..'F'){ //A부터 F까지 문자의 범위를 사용해 이터레이션함.
                val binary = Integer.toBinaryString(c.toInt()) //아스키코드를 2진 표현으로 바꿈
                binaryReps[c] = binary //c를 키로 c의 2진 표현을 맵에 넣음
            }
             
             
            for((letter,binary) in binaryReps){
                println("$letter = $binary") // 맵에 대해 이터레이션 함. 맵의 키와 값을 두변수에 각각 대입
            }

        → .. 연산자는 숫자 타입의 값 뿐만 아니라 문자 타입의 값에도 적용할 수 있음.

    - in 으로 컬렉션이나 범위의 원소의 검사in 연산자를 사용해 어떤 값이 범위에 속하는지 검사할 수 있음. ↔ 반대로 !in을 사용하면 어떤 값이 범위에 속하지 않는지 검사할 수 있음. → when 식에서도 사용할 수 있음.

        **in을 사용해 값이 범위에 속하는지 검사하기**

            fun isLetter(c:Char) = c in 'a'..'z' || c in 'A'..'Z'
            fun isNotDigit(c:Char) = c !in '0'..'9'
             
             
            >>>println(isLetter('q'))
            true
            >>>println(isNotDigit('x'))
            true

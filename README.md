## Kotlin in action
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

        ## 3장 함수 정의와 호출

        모든 프로그램에서 핵심이라 할 수 있는 함수 정의와 호출 기능을 코틀린이 어떻게 개선했는지에 관한 내용

        - 코틀린에서 컬렉션 만들기

                val set = hashSetOf(1, 7, 53)
                val list = arrayListOf(1, 7, 53)
                val map = hashMapOf(1 to "one", 7 to "seven", 53 to "fifty-three")

            코틀린은 자신만의 컬렉션 기능을 제공하지 않는다. → 자체 컬렉션을 제공하지 않는 이유는 표준 자바 컬렉션을 활용하면 자바 코드와 상호작용하기가 쉽기 때문.자바에서 코틀린 함수를 호출하거나 코틀린에서 자바 함수를 호출할 때, 자바와 코틀린 컬렉션을 서로 변환할 필요가 없음.

        - 함수를 호출하기 쉽게 만들기

                >>> val list = listOf(1,2,3)
                >>> println(list)
                [1,2,3]

            인자가 많을 때, 헷갈릴 수 있으므로 코틀린에서는 작성한 함수를 호출할 때 함수에 전달하는 인자 중 일부 또는 전부의 이름을 명시할 수 있음.

            자바 컬렉션에는 디폴트 toString 구현이 들어있는데, 디폴트 toString의 출력 형식은 고정되어있고, 이것이 필요한 형식이 아닐때가 있다.

            → 디폴트 구현과 달리 (1;2;3) 처럼 원소 사이를 세미 콜론으로 구분하고 괄호로 리스트를 둘러싸고 싶다면 함수를 구현할 수 있다.

                fun <T> joinToString(
                	collection : Collection<T>,
                	separator : String, 
                	prefix : String,
                	postfix : String
                ) : String{
                	val result = StringBuilder(prefix)
                
                
                	for((index, element) in collection.withIndex()){
                		// 첫 원소 앞에는 구분자를 붙이면 안 된다. 
                		if(index > 0) result.append(seperator)
                		result.append(element)
                	}
                
                
                	result.append(postfix)
                	return result.toString()
                
                
                }

            → 이 함수는 제네릭하기때문에, 어떤 타입의 값을 원소로 하는 컬렉션이든 처리할 수 있음.

            - 인자가 많을 때, 헷갈릴 수 있으므로 코틀린에서는 작성한 함수를 호출할 때 함수에 전달하는 인자 중 일부 또는 전부의 이름을 명시할 수 있음.

                joinToString(collection, separator = "", prefix = "", postfix=".")

        - 디폴트 파라미터 값

        자바에서는 일부 클래스에서 오버로딩한 메소드가 너무 많아진다는 문제가 있음.

        → 코틀린에서는 함수 선언에서 파라미터의 디폴트 값을 지정할 수 있으므로 이런 오버로드 중 상당수를 피할 수 있음.

            fun<T> joinToString(
            	//디폴트 값이 지정된 파라미터들
            	collection : Collection<T>,
            	separator : String = ", ",
            	prefix : String = "",
            	postfix : String = "" 
            ) : String
            
            
            // 이렇게 디폴트 파라미터 값을 정해두면, 인자 중 일부를 생략해도 기본값으로 전달된 것으로 만들어서 반환 
            >>> joinToString(list)
            1, 2, 3

        - 메소드를 다른 클래스에 추가 : 확장 함수와 확장 프로퍼티

            기존코드와 코틀린 코드를 자연스럽게 통합하는 것은 코틀린의 핵심 목표 중 하나 

            확장함수

            기존 자바 API를 재작성하지 않고도 코틀린이 제공하는 여러 편리한 기능을 사용할 수 있는 역할을 해줌.확장 함수는 어떤 클래스의 멤버 메소드인 것처럼 호출할 수 있지만 **그 클래스의 밖에 선언된 함수**

                fun String.lastChar() : Char = this.get(this.length-1)
                // fun 뒤의 string은 수신객체의 타입, this는 수신 객체 
                >>> println("Kotlin".lastChar())
                n
                
                
                // 원래 객체에 확장을 해서 바로 호출해서 사용할 수 있음. ****** 중요
                
                // 수신 객체 타입 : 확장이 정의될 클래스의 타입
                // 수신 객체 : 그 클래스에 속한 인스턴스 객체

            클래스 안에서 정의된 메소드와 달리 확장함수 안에서는 클래스 내부에서만 사용할 수 있는 비공개 멤버나 보호된 멤버를 사용할 수 없음.

        - 컬렉션 처리 : 가변 길이 인자, 중위 함수 호출, 라이브러리 지원

            - **vararg키워드**를 사용하면 **호출 시 인자 개수가 달라질 수 있는 함수**를 정의할 수 있음. 

            -**중위 함수 호출 구문**을 사용하면 **인자가 하나뿐인 메소드**를 간편하게 호출할 수 있음. 

                1.to("one")  // "to" 메소드를 일반적인 방식으로 호출함
                1 to "one"   // "to" 메소드를 중위 호출 방식으로 호출함

            → 수신 객체와 유일한 메소드 인자 사이에 메소드 이름을 넣음 (객체, 메소드 이름, 유일한 인자 사이에는 공백이 들어가야 함. )

            -**구조 분해 선언**을 사용하면 복합적인 값을 분해해서 여러 변수에 나눠 담을 수 있음.

        - 문자열과 정규식 다루기- 여러 줄 3중 따옴표 문자열 문자열 이스케이프를 피하기 위해서만 사용하지 않고, 아무 문자열이나 그대로 들어간다. → 줄 바꿈이 들어 있는 프로그램 텍스트를 쉽게 문자열로 만들 수 있음.
        - 코드 다듬기 : 로컬 함수와 확장코틀린에서는 함수에서 추출한 함수를 원 함수 내부에 중첩시킬 수 있음. → 문법적인 부가 비용을 들이지 않고 깔끔하게 코드를 조직할 수 있음.
        - 요약

        - 코틀린은 자체 컬렉션 클래스를 정의하지는 않지만 자바 클래스를 확장해서 더 풍부한 API를 제공- 함수 파라미터의 디폴트 값을 정의하면 오버로딩한 함수를 정의할 필요성이 줄어듬. 

        → 이름 붙인 인자를 사용하면 함수의 인자가 많을 때 함수 호출의 가독성을 더 향상시킬 수 있음.

        - 코틀린 파일에서 클래스 멤버가 아닌 최상위 함수와 프로퍼티를 직접 선언할 수 있음. 

        → 코드 구조를 더 유연하게 만들 수 있음.- 확장 함수와 프로퍼티를 사용하면 외부 라이브러리에 정의된 클래스를 포함해 모든 클래스의 API를 그 클래스의 소스코드를 바꿀필요없이 확장할 수 있음.

        - 중위 호출을 통해 이나가 하나 밖에 없는 메소드나 확장 함수를 더 깔끔한 구문으로 호출할 수 있음.

        - 로컬함수를 써서 코드를 더 깔끔하게 유지하면서 중복을 제거할 수 있음.

        ## 4장 클래스, 객체, 인터페이스

        4장 클래스, 객체, 인터페이스 + object 키워드 (클래스와 인스턴스를 동시에 선언하면서 만들 때 쓰는)

        - 클래스와 인터페이스
        - 뻔하지 않은 생성자와 프로퍼티
        - 데이터 클래스
        - 클래스 위임
        - object 키워드 사용 (싱글턴 클래스, 동반 객체, 객체 식을 표현할 때 사용)

            1. 클래스와 인터페이스

            자바와 달리 코틀린의 기본선언은 final이며 public이다.

            코틀린 컴파일러는 번잡스러움을 피하기 위해 유용한 메소드를 자동으로 만들어줌.

            클래스를 data로 선언하면 컴파일러가 일부 표준 메소드를 생성

            - 코틀린 인터페이스

            코틀린 인터페이스는 안에 추상메소드뿐 아니라 구현이 있는 메소드도 정의 가능 → 다만 인터페이스에는 아무런 상태도 들어갈 수 없음.

                interface Clickable{
                    fun click()
                }

            → click 이라는 추상 메소드가 있는 인터페이스를 정의 . 이 인터페이스를 구현하는 모든 비추상 클래스는 click에 대한 구현을 제공해야 한다.

                class Button : Clickable{
                    override fun click() = println("i was clicked")
                }
                >>> Button().click()
                i was clicked

            ---

            자바에서는 extends와 implements 키워드를 사용하지만, 코틀린에서는 **클래스 이름 뒤에 콜론을 붙이고** 인터페이스와 클래스 이름을 적는 것으로 클래스 확장과 인터페이스 구현을 모두 처리

        - override 변경자 : 인터페이스에 있는 프로퍼티나 메소드를 오버라이드한다는 표시

            자바와 달리 코틀린에서는 **override 변경자**를 꼭 사용해야 함.  

                interface Clickable{
                    fun click() // 일반 메소드 선언
                    fun showOff() = println("i'm clickable") // 디폴트 구현이 있는 메소드
                }

            만약, 어떤 클래스가 두개의 인터페이스를 상속받는데, 두개의 인터페이스에 동일한 이름을 가진 메소드가 있다면 하위 클래스에서는 명시적으로 새로운 구현을 제공해야함.

            상위 타입의 이름을 꺽쇠 괄호 사이에 넣어서 "super"를 지정하면, 어떤 상위 타입의 멤버 메소드를 호출할지 지정할 수 있음예) super<Clickable>.showOff()

        - open, final, abstract 변경자 : 기본적으로 final

            자바에서의 final : 명시적으로 상속을 금지하지 않는 모든 클래스를 다른 클래스가 상속할 수 있음. 

            → 기본적으로 상속이 가능하면 편리한 경우도 있지만, 문제가 생기는 경우도 많음

            → 취약한 기반 클래스 : 하위 클래스가 기반 클래스에 대해 가졌던 가정이 기반 클래스를 변경함으로써 깨져버린 경우 자바의 클래스와 메소드는 기본적으로 상속에 대해 열려있지만 **코틀린의 클래스와 메소드는 기본적으로 final 어떤 클래스의 상속을 허용하려면 클래스 앞에 open 변경자를 붙여야 함.** 

            **+ 오버라이드를 허용하고 싶은 메소드나 프로퍼티와 앞에도 open 변경자를 붙여야 함**

                open class RichButton : Clickable { // 이 클래스는 열려 있음. -> 다른 클래스가 이 클래스를 상속할 수 있음.
                    fun disable(){} // 이 함수는 파이널이기 때문에 하위 클래스가 이 메소드를 오버라이드 할 수 없음.
                    open fun animate(){} // 열려있는 함수. 하위 클래스에서 이 메소드를 오버라이드해도 됨.
                    override fun click(){} // 상위클래스에서 선언된 열려 있는 메소드를 오바라이드 함. 오버라이드한 메소드는 기분적으로 열려 있음.
                }

            * 오버라이하는 메소드의 구현을 하위 클래스에서 오버라이드하지 못하게 금지하려면 오버라이드하는 메소드 앞에 final을 명시해야 함.

            abstract으로 선언한 추상 클래스는 인스턴스화 할 수 없음.

            추상클래스에는 추상 멤버가 있어서 상속할 수 없고 하위 클래스에서 그 추상 멤버를 오버라이드해야만 하는게 보통 

            → 추상 멤버는 항상 열려 있음. 따라서 추상 멤버 앞에 open 변경자를 명시할 필요가 없음.

            [코틀린의 가시성 변경자](https://www.notion.so/ba5ae5534b324c0ba5736b7d12bede06)

        - 가시성 변경자 : 기본적으로 공개코틀린에는 자바와 다르게 아무 변경자도 없는 경우 선언은 **모두 공개**로 된다.

            자바의 기본 가시성인 패키지 전용은 코틀린에는 없음.

            패키지 전용 가시성에 대한 대안으로 코틀린에는 **internal**이라는 새로운 가시성 변경자를 도입

            → internal : 모듈 내부에서만 볼 수 있음 (모듈 : 한꺼번에 컴파일되는 코틀린 파일들)모듈 내부 가시성은 모듈의 구현에 대해 진정한 캡슐화를 제공한다는 장점이 있음.코틀린의 가시성 변경자

            [Untitled](https://www.notion.so/5db9a6019d364c718436bbf091b77e07)

        - 내부 클래스와 중첩 클래스 : 기본적으로 중첩 클래스

            자바처럼 코틀린 안에서도 클래스 안에 다른 클래스를 선언할 수 있음.

            클래스 안에 다른 클래스를 선언하면 도우미 클래스를 캡슐화하거나 코드 정의를 그 코드를 사용하는 곳에 가까이에 두고 싶을 때 유용

            → 코틀린의 중첩 클래스는 명시적으로 요청하지 않는 한 바깥 쪽 클래스 인스턴스에 대한 접근 권한이 없다는 점

        - 봉인된 클래스 : 클래스 계층 정의 시 계층 확장 제한

            sealed 클래스 : 상위 클래스에 sealed 변경자를 붙이면 그 상위 클래스를 상속한 하위 클래스 정의를 제한할 수있음.

            sealed 클래스의 하위 클래스를 정의할 때는 반드시 상위 클래스 안에 중첩시켜야 함.

        - 뻔하지 않은 생성자와 프로퍼티를 갖는 클래스 선언

            자바에서는 생성자를 하나 이상 선언할 수 있음코틀린도 비슷하지만, 주 생성자와 부생성자를 구분하여 사용하고, 초기화 블록을 통해 초기화 로직을 추가할 수 있음.

                // 주생성자의 목적: 생성자 파라미터 지정, 생성자 파라미터에 의해 초기화되는 프로퍼티를 정의하는 두 가지 목적에 쓰임.
                class User(val nickname : String) // 클래스 이름 뒤에 오는 괄호로 둘러싸인 코드 -> 주생성자

                class User constructor(_nickname : String){ // 파라미터가 하나만 있는 주 생성자
                    val nickname : String
                    //초기화 블록
                    init {
                        nickname = _nickname
                }
                }

            - 초기화 블록 : 클래스의 객체가 만들어질 때 실행될 초기화 코드가 들어감 + 주생성자와 함께 사용

            - 생성자 파라미터 _nickname에서 맨 앞의 밑줄 _ 은 프로퍼티와 생성자 파라미터를 구분 

            - 클래스의 인스턴스를 만들려면 new키워드 없이 생성자를 직접 호출

            >>> val hyun = User("현석")

            >>> println(hyun.isSubsribed)

        - 부 생성자 : 상위 클래스를 다른 방식으로 초기화인자에 대한 디폴트 값을 제공하기 위해 부 생성자를 여럿 만들지 않는 것이 좋음.

            대신 파라미터의 디폴트 값을 생성자 시그니처에 직접 명시

        - 인터페이스에 선언된 프로퍼티 구현

                interface User{
                    val nickname: String
                }

            user 인터페이스를 구현하는 클래스가 nickname의 값을 얻을 수 있는 방법을 제공해야 함.

        - 게터와 세터에서 뒷받침하는 필드에 접근

            어떤 값을 저장하되 그 값을 변경하거나 읽을 때마다 정해진 로직을 실행하는 유형의 프로퍼티를 만드는 방법값을 저장하는 동시에 로직을 실행할 수 있게 하기 위해서는 접근자 안에서 프로퍼티를 뒷밤침하는 필드에 접근할 수 있어야 함.

        - 접근자의 가시성 변경

            접근자의 가시성은 기본적으로는 포로퍼티의 가시성과 같음. 

            하지만 원한다면 get이나 set 앞에 가시성 변경자를 추가해서 접근자의 가시성을 변경할 수 있음.

        - 컴파일러가 생성한 메소드 : 데이터 클래스와 클래스 위임자바 플랫폼에서는 클래스가 equal, hashCode, toString 등의 메소드를 구현해야함.

            자바와 마찬가지로 모든 코틀린 클래스는 toString, equals, hashCode 등을 오버라이드해야함.

            client 클래스의 초기 정의 (고객 이름과 우편번호를 저장하는 client클래스)

                class Client(val name : String, val postalCode : Int)

            - 문자열 표현 toString()

                    class Client(val name : String, val postalCode : Int){
                        override fun toString() = "Client(name=$name, postalCode =$postalCode)"
                    }

                기본 제공되는 객체의 문자열 표현은 Client@5e9f23b4 같은 방식. 기본 구현을 바꾸려면 toString 메소드를 오버라이드

                >>> val client1 = Client("오현셕", 4122)

                >>> println(client1)Client(name=오현석, postalCode=4122)

            - 객체의 동등성 equals()
            - 클래스가 단순할지라도 동작에 대한 몇가지 요구사항이 있을 수있는데, 예를 들어 서로 다른 두 객체가 내부에 동일한 데이터를 포함하는 경우 그 둘을 동등한 객체로 간주해야할 수 도 있음.

                >>> val client1 = Client("오현석", 4122)

                >>> val client2 =Client("오현석", 4122)

                >>>println(client == client2)

                false 

                → 코틀린에서 == 연산자는 참조 동일성을 검사하지 않고 객체의 동등성을 검사. 

                따라서 == 연산은 equals를 호출하는 식으로 컴파일 됨 

                - 동등성 연산에 ==를 사용하는 것

                    자바에서는 ==를 원시타입과 참조타입을 비교할 때 사용

                    원시 타입의 경우 == 는 두 피연산자의 값이 같은지 비교

                    참조 타입의 경우 ==는 두 피연산자의 주소가 같은지 비교 

                    → 자바에서는 두 객체의 동등성을 알려면 equals를 호출

                    → **코틀린에서는 == 연산자가 두 객체를 비교하는 기본적인 방법.** 

                    **==는 내부적으로 equals를 호출해서 객체를 비교** **any → java.lang.object에 대응하는 클래스. 코틀린의 모든 클래스의 최상위 클래스 / any? 는 널이 될 수 있는 타입이므로 other은 Null일 수 있음.**

                        class Client(val name : String, val postalCode: Int){
                            override fun equals(other: Any?):Boolean{
                                if(other==null || other !is Client)
                            return false
                                return name == other.name && postalCode == other.postalCode
                        }
                         
                         
                            override fun toString()="Client(name=$name, postalCode = $postalCode)"
                        }

            - **해시 컨테이너 : hashCode()  → 모든 프로퍼티의 해시 값을 바탕으로 계산한 해시값을 반환**자바에서는 equals를 오버라이드할 때 반드시 hashcode도 함께 오버라이드해야 함.

                원소가 "현석"이라는 고객 하나분인 집합을 만들었을 때, 그 후 새로운 원래의 "현석"과 똑같은 프로퍼티를 포함하는 새로운 client 인스턴스를 만들어서 그 인스턴스가 집합 안에 들어있는지 검사

                프로퍼티가 모두 일치하므로 새 인스턴스와 집합에 있는 기존 인스턴스는 동등.

                 따라서 새 인스턴스가 집합에 속해있는지 여부를 검사하면 true가 반환될 것이라 예상할 수 있지만 실제로는 false가 반환

                >>> val processed = hashSetOf(Client("오현석", 4122))

                >>> println(processed.contains(Client("오현석", 4122)))

                false

                → client클래스가 hashcode 메소드를 정의하지 않았기 때문에 false값이 반환

                jvm언어에서는 hashcode가 지켜야 하는 equals가 true를 반환하는 두 객체는 반드시 같은 hashcode를 반환해야 한다는 제약이 있는데 client는 이를 어기고 있음.

            - 데이터 클래스 : 모든 클래스가 정의해야 하는 메소드 자동 생성data라는 변경자를 클래스 앞에 붙이면 필요한 메소드를 컴파일러가 자동으로 만들어줌.

                data변경자가 붙은 클래스를 데이터 클래스라고 부름

                    data class Client(val name: String, val postalCode: Int)

            - 데이터 클래스와 불변성 : copy() 메소드

                데이터 클래스 인스턴스를 불변 객체로 더 쉽게 활용할 수 있게 코틀린 컴파일러는 한가지 편의 메소드를 제공

                그 메소드는 복사하면서 일부 프로퍼티를 바꿀 수 있게 해주는 copy 메소드.

                객체를 메모리상에서 직접 바꾸는 대신 복사본을 만드는 편이 더 나음.복사본은 원본과 다른 생명주기를 가지며, 복사를 하면서 일부 프로퍼티 값을 바꾸거나 복사본을 제거해도 프로그램에서 원본을 참조하는 다른 부분에 전혀 영향을 끼치지 않음.

            - 클래스 위임 : by 키워드 사용

                하위 클래스가 상위 클래스의 메소드 중 일부를 오바라이드하면 하위클래스는 상위 클래스의 세부 구현 사항에 의존하게 됨.

                시스템이 변함에 따라 상위 클래스의 구현이 바뀌거나 상위 클래스에 새로운 메소드가 추가 됨. → 그 과정에서 하위 클래스가 상위 클래스에 갖고 있던 가정이 깨져서 코드가 정상적으로 작동하지 못하는 경우가 생길 수 있음.

                종종 상속을 허용하지 않는 클래스에 새로운 동작을 추가해야할 때 **데코레이터 패턴**을 사용

            - object 키워드 : 클래스 선언과 인스턴스 생성모든 경우 클래스를 정의하면서 동시에 인스턴스(객체)를 생성함

            - 객체 선언은 싱글턴을 정의하는 방법 중 하나 

            - 동반 객체는 인스턴스 메소드는 아니지만 어떤 클래스와 관련 있는 메소드와 팩토리 메소드를 담을 때 사용 

            → 동반 객체 메소드에 접근할 때는 동반 객체가 포함된 클래스의 이름을 사용할 수 있음.

            - 객체 식은 자바의 무명 내부 클래스 대신 쓰임

            → 객체 선언 : 싱글턴을 쉽게 만들기객체선언 = 클래스 선언 + 그 클래스에 속한 단일 인스턴스의 선언을 합친 선언

            → 동반객체 : 클래스 안에 정의된 일반 객체. 동반 객체에 이름을 붙이거나 동반 객체가 인터페이스를 상속하거나, 동반 객체 안에 확장 함수와 프로퍼티를 정의할 수 있음.

             코틀린 동반 객체와 정적 멤버클래스의 동반 객체는 일반 객체와 비슷한 방식으로, 클래스에 정의된 인스턴스를 가리키는 정적 필드로 컴파일동반 객체에 이름을 붙이지 않았다면, 자바 쪽에서 companion이라는 이름으로 그 참조에 접근할 수 있음.

            → 동반 객체 확장 싱글톤 : 싱글톤 패턴은 하나의 프로그램 내에서 하나의 인스턴스만을 사용해야하는 상황에 주로 사용됨. 

            환경 설정 관리 클래스나 커넥션 풀과 같이 pool 형태로 관리되는 클래스 주로 공통 클래스에 사용되는 것이 일반적

            → 사용자 정보를 처음에만 로딩해주는 usermanager가 있다고 칠 때, 매번 이 인스턴스를 생성하는 것은 자원 낭비 또는 인스턴스가 꼬이는 일이 생길 수 있음.

        - 4장 요약

            - 코틀린의 인터페이스는 자바 인터페이스와 비슷하지만 디폴트 구현을 포함할 수 있고 프로퍼티도 포함할 수 있음 (자바에서는 불가능)

            - 모든 코틀린 선언은 기본적으로 final이며, public임.- 선언이 final이 되지 않게 만들려면 앞에 open을 붙여야 함.- internal 선언은 같은 모듈 안에서만 볼 수 있음.

            - 중첩 클래스는 기본적으로 내부 클래스가 아님.

            - sealed 클래스를 상속하는 클래스를 정의하려면 반드시 부모 클래스 정의 안에 중첩 클래스로 정의해야 함.

            - 초기화 블록과 부 생성자를 활용해 클래스 인스턴스를 더 유연하게 초기화할 수 있음

            -field 식별자를 통해 프로퍼티 접근자안에서 프로퍼티의 데이터를 저장하는데 쓰이는 뒷받침하는 필드를 참조할 수 있음

            - 데이터 클래스를 사용하면 컴파일러가 equals, hashCode, toString, copy 등의 메소드를 자동으로 생성해줌.

        ## 5장 람다로 프로그래밍

        5장 람다로 프로그래밍

        - 람다 식과 멤버 참조
        - 함수형 스타일로 컬렉션 다루기
        - 시퀀스 : 지연 컬렉션 연산
        - 자바 함수형 인터페이스를 코틀린에서 사용
        - 수신 객체 지정 람다 사용

        > 람다식 또는 람다는 기본적으로 다른 함수에 넘길 수 있는 작은 코드 조각을 뜻함.람다를 사용하면 쉽게 공통 코드 구조를 라이브러리 함수로 뽑아 낼 수 있음.람다를 자주 사용하는 경우 → 컬렉션 처리

        람다 식과 멤버 참조

        - 코드 블록을 함수 인자로 넘기기

            이벤트가 발생하면 이 핸들러를 실행하자 or 데이터 구조의 모든 원소에 이 연산을 적용하자 와 같은 생각을 표현하기 위해 일련의 동작을 변수에 저장하거나 다른 함수에 넘겨야 하는 경우가 있음.

            → 함수형 프로그래밍 : 함수를 값처럼 다루는 접근 방법을 택함으로써 이 문제를 해결 / 함수를 직접 다른 함수에 전달 

            → 람다식을 사용하면 코드가 더욱 더 간결해짐 (함수를 선언할 필요가 없고 코드 블록을 직접 함수의 인자로 전달할 수 있음.)

            - 무명 내부 클래스로 리스너 구현하기

                /*자바*/
                button.setOnClickListener(new OnClickListener(){
                    @override
                    public void onClick(View view){
                        //클릭 시 수행할 동작
                    }
                }

            - 람다로 리스너 구현하기

                button.setOnClickListener{//클릭 시 수행할 동작}

        - 람다와 컬렉션

            코드에서 중복을 제거하는 것은 프로그래밍 스타일을 개선하는 중요한 방법 중 하나

            컬렉션을 다룰 때 수행하는 대부분의 작업은 몇가지 일반적인 패턴에 속함

            → 이런 패턴은 라이브러리 안에 있어야 함.

            - 람다를 사용해 컬렉션 검색하기

                >>> val people = listOf(Person("Alice", 29), Person("Bob", 31))
                >>> println(people.maxBy{it.age}) //나이 프로퍼티를 비교해서 값이 가장 큰 원소 찾기
                person(name=Bob, age= 31)

            * maxBy : 가장 큰 원소를 찾기 위해 비교에 사용할 값을 돌려주는 함수를 인자로 받음. 이 코드는 컬렉션의 원소를 인자로 받아서 비교에 사용할 값을 반환

        - 람다 식의 문법

            여기 저기 전달할 수 있는 동작의 모음 / 람다를 따로 선언해서 변수에 저장할 수도 있음.

            { x : Int, y : Int → x + y}→ 항상 중괄호 사이에 위치함

            → (화살표)가 인자 목록과 람다 본문을 구분해줌. 

            it을 사용하는 관습은 코드를 아주 간단하게 만들어 줌.

            람다 안에 람다가 중첩되는 경우에는 람다의 파라미터를 명시하는 편이 나음.

            문맥에서 람다 파라미터의 의미나 파라미터의 타입을 쉽게 알 수 없는 경우에도 파라미터를 명시적으로 선언하면 도움이 됨.

        - 현재 영역에 있는 변수에 접근

            자바 메소드 안에서 무명 내부 클래스를 정의할 때, 메소드의 로컬 변수를 무명 내부 클래스에서 사용할 수 있음.

            람다를 함수 안에서 정의하면 함수의 파라미터뿐 아니라 람다 정의의 앞에 선언된 로컬 변수까지 람다에서 모두 사용할 수 있음. 

            forEach 함수가장 기본적인 컬렉션 조작함수 중 하나 컬렉션의 모든 원소에 대해 람다를 호출해줌.

        - 멤버 참조

            :: 을 사용하는 식을 멤버참조라고 부르는데, 멤버 참조는 프로퍼티나 메소드를 단 하나만 호출하는 함수 값을 만들어 줌.

            ::는 클래스 이름과 참조하려는 멤버 이름 사이에 위치함.

            Person :: age = val getAge = {person: Person → person.age}

        - 필수적인 함수 : filter 와 mapfilter와 map은 컬렉션을 활용할 때 기반이 되는 함수.

            filter 함수

                >>>val list = listOf(1,2,3,4)
                >>>println(list.filter{it%2==0}) // 짝수만 남는다.
                [2,4]

            컬렉션에서 원치 않는 원소를 제거. 하지만 filter는 원소를 변환할 수 는 없음.  원소를 변환하려면 map 함수를 이용

        - map 함수

                >>> val people = listOf(Person("Alice", 20), Person("Bob", 31))
                >>> println(people.filter{it.age > 30})
                [Person(name=Bob, age= 31)]

            주어진 람다를 컬렉션의 각 원소에 적용한 결과를 모아서 새 컬렉션을 만듬.

        - all, any, count, find : 컬렉션에 술어 적용

            컬렉션에 대해 자주 수행하는 연산으로 컬렉션의 모든 원소가 어떤 조건을 만족하는지 판단하는 연산이 있음.

            → all, any 연산

            count 함수 : 조건을 만족하는 원소의 갯수를 반환

            find 함수 : 조건을 만족하는 첫번째 원소를 반환

        - group by : 리스트를 여러 그룹으로 이뤄진 맵으로 변경컬렉션의 모든 원소를 어떤 특성에 따라 여러 그룹으로 나누고 싶을 때, 사람을 나이에 따라 분류한다고 할 때, 특성을 파라미터로 전달하면 컬렉션을 자동으로 구분해주는 함수가 있으면 편리할 것.

            → group by 함수의 역할

                >>> val people = listOf(Person("Alice", 31)),
                ...Person("Bob", 29), Person("Carol", 31))
                >> println(people.groupBy { it.age})

        - flatMap과 flatten : 중첩된 컬렉션 안의 원소 처리먼저 인자로 주어진 람다를 컬렉션의 모든 객체에 적용하고 (또는 매핑) 람다를 적용한 결과 얻어지는 여러 리스트를 한 리스트로 한데 모음.
        - 지연 계산 컬렉션 연산

            map이나 filter 같은 몇가지 컬렉션 함수는 결과 컬렉션을 **즉시** 생성함. 

            → 컬렉션 함수를 연쇄하면 매 단계마다 계산 중간 결과를 새로운 컬렉션에 임시로 담는다는 말시퀀스를 사용하면 중간 임시 컬렉션을 사용하지 않고도 컬렉션 연산을 연쇄할 수 있음. 

            - 시퀀스 연산 실행 : 중간 연산과 최종 연산시퀀스에 대한 연산은 중간 연산과 최종 연산으로 나뉨. 중간 연산은 다른 시퀀스를 반환

            - 시퀀스 만들기generateSequence() 함수를 사용하여 시퀀스를 만들 수 있음.

        - 자바 함수형 인터페이스 활용

            자바와 달리 코트린에는 제대로 된 함수 타입이 존재함. 

            코틀린에서 함수를 인자로 받을 필요가 있는 함수는 함수형 인터페이스가 아니라 함수 타입을 인자 타입으로 사용해야 함. 

            코틀린 함수를 사용할 때는 코틀린 컴파일러가 코틀린 람다를 함수형 인터페이스로 변환해주지 않음.

        - 자바 메소드에 람다를 인자로 전달

            함수형 인터페이스를 인자로 원하는 자바 메소드에 코틀린 람다를 전달할 수 있음.

            * Runnable 인스턴스 : 실제로는 Runnable을 구현한 무명 클래스의 인스턴스라는 뜻. 컴파일러는 자동으로 그런 무명 클래스와 인스턴스를 만들어 줌.

        - SAM 생성자 : 람다를 함수형 인터페이스로 명시적으로 변경

            sam 생성자는 람다를 함수형 인터페이스의 인스턴스로 변환할 수 있게 컴파일러가 자동으로 생성한 함수 컴파일러가 자동으로 람다를 함수형 인터페이스 무명 클래스로 바꾸지 못하는 경우에 사용 안드로이드라면, Activity.onCreate() 메소드 안에 다음과 같은 코드가 들어갈 수 있음. 여러 버튼에 같은 리스너를 적용하고 싶을 때, 다음 리스트 처럼 SAM 생성자를 통해 람다를 함수형 인터페이스 인스턴스로 만들어서 변수에 저장해 활용할 수 있음.

            - **SAM 생성자를 사용해 listener 인스턴스 재사용하기**

                val listener = OnClickListener{ view ->
                    val text = when(view.id){ // view.id를 사용해 어떤 버튼이 클릭됐는지 판단
                        R.id.button1 -> "First button"
                        R.id.button2 -> "Second button"
                        else -> "Unknown button"
                    }
                    toast(text) // "text"의 값을 사용자에게 보여줌
                }
                 
                 
                button1.setOnClickListener(listener)
                button2.setOnClickListener(listener)

            이벤트 리스너가 이벤트를 처리하다가 자기 자신의 리스너를 등록을 해제해야 한다면, 람다를 사용할 수 없음.→ 그런 경우 람다 대신 무명 객체를 사용해 리스너를 구현 

            (무명 객체 안에서는 this가 그 무명객체 인스턴스 자신을 가리킴. 따라서 리스너를 해제하는 API함수에게 this를 넘길 수 있음.)

        - 수신 객체 지정 람다 : with 와 apply수신 객체를 명시하지 않고 람다의 본문 안에서 다른 객체의 메소드를 호출할 수 있게 하는 것 → 그런 람다를 "수신 객체 지정 람다" 라고 함

            **1) with 함수**어떤 객체의 이름을 반복하지 않고도 그 객체에 대해 다양한 연산을 수행할 수 있게 도와주는 라이브러리 함수 

                //알파벳 만들기
                fun alphabet() : String {
                    val result = StringBuilder()
                    for ( letter in 'A'..'Z'){
                        result.append(letter)
                    }
                    result.append("\nNow I know the alpahbet!")
                    return result.toString()
                }
                 
                 
                >>> println(alphabet())
                ABCDEFGHIJKLMNOPPQRSTUVWXYZ
                Now I know the alphabet!

            → result 에 대해 다른 여러 메소드를 호출하면서 매번 result를 반복사용함. → 나쁘진 않지만, result를 더 자주사용해야하거나 코드가 더 길어지면 ?

            - **with를 사용해 알파벳 만들기**

                fun alphabet() : String{
                    val stringBuilder = StringBuilder()
                    return with(stringBuilder){ // 메소드를 호출하려는 수신 객체를 지정
                        for(letter in 'A'..'Z'){
                            this.append(letter) // "this"를 명시해서 앞에서 앞에서 지정한 수신 객체의 메소드를 호출
                        }
                        append("/nNow I know the alphabet!") // "this"를 생략하고 메소드를 호출
                        this.toString() // 람다에서 값을 반환
                    }
                }

            **2) apply 함수**

            거의 with와 같음. 유일한 차이란 apply는 항상 자신에게 전달된 객체를 반환한다는 점.

            - **apply를 사용해 알파벳 만들기**

                fun alphabet() = StringBuilder().apply {
                    for(letter in 'A'..'Z'){
                        append(letter)
                    }
                    append("\nNow I know the alphabet!")
                }.toString()

            → apply는 수신객체가 전달받은 람다의 수신 객체가 됨. 

            이 함수에서 apply를 실행한 결과는 StringBuilder객체 → 그 객체의 toString을 호출해서 String 객체를 얻을 수 있음.

            - **apply를 사용해 알파벳 만들기**

                fun createViewWithCustomAttributes(context: Context) =
                    TextView(context).apply{
                        text = "Sample Text"
                        textSize = 20.0
                        setPadding(10,0,0,0)
                    }

        ## 6장 코틀린 타입 시스템

        자바와 비교하면 코틀린의 타입 시스템은 코드의 가독성을 향상시키는데 도움이 되는 몇 가지 특성을 새로 제공 → **1. 널이될 수 있는 타입 2. 읽기 전용 컬렉션**

        [+](http://wiki.i-screamedu.com/pages/createpage.action?spaceKey=~yn.choi&title=%2B&linkCreation=true&fromPageId=9245483) 자바 타입 시스템에서 불필요하거나 문제가 되던 부분을 제거 (예: 배열 지원)

        - 널 가능성 → NullPointerException 오류 (간단히 NPE) 를 피할 수 있게 돕기 위한 코틀린 타입 시스템의 특성

            널이 될 수 있는지 여부를 타입 시스템에 추가함으로써 컴파일러가 여러 가지 오류를 컴파일 시 미리 감지해서 실행 시점에 발생할 수 있는 예외의 가능성을 줄일 수 있음. 

            1. 널이 될 수 있는 타입

            **코틀린 타입 시스템이 널이 될 수 있는 타입을 명시적으로 지원한다는 점** → 코틀린과 자바의 첫 번째이자 가장 중요한 차이 프로그램 안의 프로퍼티나 변수에 null을 허용하게 만드는 방법 

            - 자바

                int strLen(String s){
                    return s.length();
                }

            - 코틀린

                fun strLen(s: String) = s.length
                 
                 
                >>>strLen(null)
                ERROR : Null can not be a value of a non-null type String

            컴파일러는 널이 될 수 있는 값을 strLen에게 인자로 넘기지 못하게 막음. 

            2. 타입의 의미

            → 타입이란 무엇이고 왜 변수에 타입을 지정해야하는 걸까?

            (타입 : 분류로, 어떤 값들이 가능한지와 그 타입에 대해 수행할 수 있는 연산의 종류를 결정)

            3. 안전한 호출 연산자 **?.**

            null 검사와 메소드 호출을 한 번의 연산으로 수행 s?.toUpperCase() 와 if(s!=null) s.toUpperCase() else null과 같음.→ 호출하려는 값이 null이 아니라면 ?. 는 일반 메소드 호출처럼 작동하고, 호출하려는 값이 null이면 호출이 무시되고 null이 결과값으로 반환.

            4. 엘비스 연산자 **?:**

            null 대신 사용할 디폴트 값을 지정할 때 편리하게 사용할 수 있는 연산자

                //"s"가 null이면 결과는 빈 문자열 ""
                fun foo(s: String?){
                    val t: String = s ?: ""
                }

            - 코틀린에서는 return 이나 throw 등의 연산도 식 

            → 엘비스 연산자의 우항에 return, throw 등의 연산을 넣을 수 있음.

            5. 안전한 캐스트 : as? 

            자바 타입 캐스트와 마찬가지로 대상 값을 as로 지정한 타입으로 바꿀 수 없으면, ClassCastException이 발생 as? 연산자는 어떤 값을 지정한 타입으로 캐스트 함. 

            값을 대상으로 타입 → 어떤 값을 지정한 타입으로 캐스트하며, 값을 대상 타입으로 변환할 수 없으면 null을 반환

            - **안전한 연산자를 사용해 equals 구현하기**

                class Person(val firstName: String, val lastName: String){
                    override fun equals(o: Any?) : Boolean {
                        val otherPerson  = o as? Person ?: return false // 타입이 서로 일치하지 않으면 false를 반환
                        return otherPerson.firstName == firstName && otherPerson.lastName == lastName // 안전한 캐스트를 하고나면 otherPerson이 Person 타입으로 스마트 캐스트
                    }
                    override fun hashCode() : Int = firstName.hashCode() * 37 + lastName.hashCode()
                }
                 
                 
                >>> val p1 = Person("dmitry", "jemerov")
                >>> val p2 = Person("dmitry", "jemerov")
                >>> println(p1==p2) // == 연산자는 "equals" 메소드를 호출
                true
                >>>println(p1.equals(42))
                false

            6. 널 아님 단언 **!!**

            널이 될 수 있는 타입의 값을 다룰 때 사용할 수 있는 도구 중에서 가장 단순하면서도 무딘 도구 

            느낌표를 이중으로 사용하면 어떤 값이든 널이 될 수 없는 타입으로 바꿀 수 있음.

            → 실제 널에 대해 !! 를 적용하면 NPE가 발생

            ----- 널이 될 수 있는 값을 널이 아닌 값만 인자로 받는 함수에 넘기려면 어떻게 하는 지 --------

            7. let 함수

            널이 될 수 있는 식을 쉽게 다를 수 있음.

            let함수를 안전한 호출 연산자와 함께 사용하면 원하는 식을 평가해서 결과가 널인지 검사한 다음에 그 결과를 변수에 넣는 작업을 간단한 식을 사용해 한꺼번에 처리할 수 있음.

            → let 함수는 자신의 수신 객체를 인자로 전달받은 람다에게 넘김

            → 널이 될 수 있는 값에 대해 안전한 호출 구문을 사용해 let을 호출하되 널이 될 수 없는 타입을 인자로 받는 람다를 let에게 전달함.

            → 널이 될 수 있는 타입의 값을 널이 될 수 없는 타입의 값으로 바꿔서 람다에게 전달

            8. 나중에 초기화할 프로퍼티 

            → 사용하는 시점에 초기화한다는 것은 메모리를 절약할 수 있음.

            객체 인스턴스를 일단 생성한 다음에 나중에 초기화하는 프레임워크가 많다. 

            예) 안드로이드에서는 onCreate에서 액티비티를 초기화하고, 제이유닛에서는 @Before로 애노테이션된 메소드 안에서 초기화 로직을 수행해야만 함.

            코틀린에서는 클래스 안의 널이 될 수 없는 프로퍼티를 생성자 안에서 초기화하지 않고 특별한 메소드 안에서 초기화할 수는 없음.

            일반적으로 생성자에서 모든 프로퍼티를 초기화해야하고, 프로퍼티 타입이 널이 될 수 없는 타입이라면 반드시 널이 아닌 값으로 그 프로퍼티를 초기화해야 함.

            9. 널이 될 수 있는 타입 확장

            널이 될 수 있는 타입에 대한 **확장 함수를 정의**하면 null 값을 다루는 강력한 도구로 활용할 수 있음.

            어떤 메소드를 호출하기 전에 수신 객체 역할을 하는 변수가 널이 될 수 없다고 보장하는 대신, **직접 변수에 대해 메소드를 호출**해도 **확장 함수**인 메소드가 알아서 널을 처리해 줌.

            예) 코틀린 라이브러리에서 string을 확장해 정의된 isEmpty와 isBlank라는 함수가 있고, 전자는 빈 문자열인지 검사하고, 후자는 문자열이 모두 공백 문자로 이뤄졌는지 검사한다.

            * 디스패치

            객체지향언어에서 객체의 동적 타입에 따라 적절한 메소드를 호출해주는 방식

            **+ run() 함수  시점에 따라 다름**

            10. 타입 파라미터의 널 가능성

            코틀린에서 함수나 클래스의 모든 타입 파라미터는 기본적으로 널이 될 수 있다. 널이 될 수 있는 타입을 포함하는 어떤 타입이라도 타입 파라미터를 대신할 수 있다.→ 타입 파라미터 T를 클래스나 함수 안에서 타입 이름으로 사용하면 이름 끝에 물음표가 없더라도 T가 널이 될 수 있는 타입

            - **널이 될 수 있는 타입 파라미터 다루기**

                fun <T> printHashCode(t:T){
                    printIn(t?.hashCode()) // "t"가 null이 될 수 있으므로 안전한 호출을 써야 함.
                }
                 
                 
                >>> printHashCode(null) // "T" 의 타입은 "Any?"로 추론된다.
                null

            11. 널 가능성과 자바코틀린은 자바 상호운용성을 강조하는 언어 → 자바 타입 시스템은 널 가능성을 지원하지 않음.

            → 자바의 @Nullable String은 코틀린 쪽에서 볼 때 String? 과 같고,

            자바의 @NotNull String은 코틀린쪽에서 볼 때 String과 같음.

            - 플랫폼 타입코틀린이 널 관련 정보를 알 수 없는 타입 → 그 타입을 널이 될 수 있는 타입으로 처리해도 되고, 널이 될 수 없는 타입으로 처리해도 됨.

        - **코틀린의 원시 타입**

            코틀린은 원시 타입과 래퍼 타입을 구분하지 않음.

        1. 원시 타입 : Int, Boolean 등자바는 원시 타입과 참조 타입을 구분 **원시 타입** (int등의 변수) : 그 변수의 이 직접 들어감**참조 타입**(string 등) : 메모리 상의  위치가 들어감→ 코틀린은 원시 타입과 래퍼 타입을 구분하지 않으므로 항상 같은 타입을 사용

        2. 널이 될 수 있는 원시 타입 : Int?, Boolean? 등

            null 참조를 자바의 참조 타입의 변수에만 대입할 수 있기 때문에 널이 될 수 있는 코틀린 타입은 자바 원시 타입으로 표현할 수 없음. 

            **코틀린에서 널이 될 수 있는 원시 타입을 사용하면 그 타입은 자바의 래퍼 타입으로 컴파일 됨.**

        3. 숫자 변환코틀린과 자바의 가장 큰 차이점 중 하나는 숫자를 변환하는 방식코틀린은 **한 타입의 숫자를 다른 타입의 숫자로 자동 변환하지 않음.**

            결과 타입이 허용하는 숫자의 범위가 원래 타입의 범위보다 넓은 경우조차도 자동 변환은 불가능 → 코틀린은 모든 원시 타입에 대한 변환 함수를 제공 (toByte(), toShort(), toChar()등)문자열을 숫자로 변환하기

            코틀린 표준 라이브러리는 문자열을 원시 타입으로 변환하는 여러 함수를 제공한다. 

            (toInt, toByte, toBoolean 등)

            >>>println("42".toInt())

            42

            → 이런 함수는 문자열의 내용을 각 원시 타입을 표기하는 문자열로 파싱  

            파싱에 실패하면 NumberFormatException이 발생

        4. Any, Any? 최상위 타입
        5. 자바에서 Object가 클래스 계층의 최상위 타입이듯 코틀린에서는 Any 타입이 모든 널이 될 수 없는 타입의 조상 타입 하지만 자바에서는 참조 타입만 Object를 정점으로 하는 타입 계층에 포함되며, 원시 타입은 그런 계층에 들어있지 않음.

            → 자바에서 Object 타입의 객체가 필요할 경우 int와 같은 원시 타입을 java.lang.Integer 같은 래퍼 타입으로 감싸야만 한다는 뜻! 

            코틀린에서는 any 타입의 변수에 대입하면 **자동으로 값을 객체로 감싼다.**  

        6. Unit 타입 : 코틀린의 void코틀린의 Unit 타입은 자바 void와 같은 기능을 함 

            → 관심을 가질 만한 내용을 **전혀 반환하지 않는** 함수의 반환 타입으로 Unit을 쓸 수 있음. fun f() : Unit { .. } 코틀린의 Unit이 자바 void와 다른 점이 무엇일까?

            Unit은 모든 기능을 갖는 일반적인 타입. void와 달리 Unit을 타입 인자로 쓸 수 있음.Unit 타입에 속한 값은 단 하나 뿐이며, 그 이름도 Unit→ Unit 타입의 함수는 Unit 값을 묵시적으로 반환 함수형 프로그래밍에서 전통적으로 Unit은 단 하나의 인스턴스만 갖는 타입을 의미 

            → 코틀린에는 Nothing이라는 전혀 다른 기능을 하는 타입이 하나 존재

            **유일한 인스턴스의 유무가 자바 void와 코틀린 Unit을 구분하는 가장 큰 차이**

        7. Nothing 타입 : 

            이 함수는 결코 정상적으로 끝나지 않음 코틀린에는 결코 성공적으로 값을 돌려주는 일이 없으므로 '반환 값'이라는 개념 자체가 의미 없는 함수 일부 존재

            예) 테스트 라이브러리들은 fail이라는 함수를 제공하는 경우가 많음 

            → **fail**은 특별한 메시지가 들어있는 에외를 던져서 현재 테스트를 실패 시킴 

            → 함수가 정상적으로 끝나지 않는다는 경우를 표현하기 위해 Nothing이라는 특별한 반환 타입이 존재- nothing 타입은 아무 값도 포함하지 않음. 

            → 함수의 반환 타입이나 반환 타입으로 쓰일 타입 파라미터로만 쓸 수 있음. 확장 함수 코틀린의 최상위 객체는 Any이기 때문에, 여기에 추가하면 모든 객체에 확장 함수를 추가할 수 있다.확장 함수를 사용하면 좋은 경우 

            → 함수가 해당 클래스와 밀접한 관련을 가졌는데 여기서 말고는 이 클래스에서 이 함수를 호출할 일이 없어서 클래스에 포함시키기엔 껄끄러울때 → 클래스의 멤버 메서드처럼 호출되지만

        ## 컬렉션과 배열 (컬렉션 자료구조의 종류와 차이점들을 알아두는 것이 좋음 list, arraylist 어디에 쓰는 것이 좋을지 미리 알아두는 것이 좋음.)

        1. 널 가능성과 컬렉션
        2. 읽기 전용과 변경 가능한 컬렉션코틀린에서는 컬렉션안의 데이터에 접근하는 인터페이스와 컬렉션 안의 데이터를 변경하는 인터페이스를 분리했음.
        3. 코틀린 컬렉션과 자바

            [Untitled](https://www.notion.so/11c5b14b4c674b9da65d2a5c96539ca5)

        4. 컬렉션을 플랫폼 타입으로 다루기
        5. 객체의 배열과 원시 타입의 배열
        - 요약

            - 코틀린은 널이 될 수 있는 타입을 지원해 NullPointerException 오류를 컴파일 시점에 감지할 수 있음

            - 자바에서 가져온 타입은 코틀린에서 플랫폼 타입으로 취급 → 개발자는 플랫폼 타입을 널이 될 수 있는 타입으로도, 널이 될 수 없는 타입으로도 사용할 수 있음.

            - 코틀린에서는 수를 표현하는 타입이 일반 클래스와 똑같이 생겼고, 일반 클래스와 똑같이 동작한다. 하지만 대부분 컴파일러는 숫자 타입을 자바 원시타입으로 컴파일 함.

            - 널이 될 수 있는 원시 타입은 자바의 박싱한 원시타입에 대응

            - Any 타입은 다른 모든 타입의 조상 타입이며, 자바의 object에 해당 

            - 자바 클래스를 코틀린에서 확장하거나 자바 인터페이스를 코틀린에서 구현하는 경우, 메소드 파라미터의 널 가능성과 변경 가능성에 대해 깊이 생각해야 함.

        ## 7장 연산자 오버로딩과 기타 관례

        - 연산자 오버로딩
        - 관례 : 여러 연산을 지원하기 위해 특별한 이름이 붙은 메소드
        - 위임 프로퍼티

            코틀린에서는 언어 기능이 어떤 타입(클래스)과 연관되기보다는 특정 함수 이름과 연관된다.

            예) 어떤 클래스 안에 plus라는 이름의 특별한 메소드를 정의하면 그 클래스의 인스턴스에 대해 + 연산자를 사용할 수 있음.

            → 어떤 언어 기능과 미리 정해진 이름의 함수를 연결해주는 기법을 코틀린에서는 **관례**라고 부름.

            1. 이항 산술 연산 오버로딩

            Point에서 지원하고픈 첫 번째 연산은 두 점을 더하는 연산 X좌표와 Y좌표를 각각 더하는 + 연산자 구현은 다음과 같음. 

                //plus 연산자 구현하기 
                data class Point(val x : Int, val y: Int){
                    //plus 라는 이름의 연산자 함수를 정의함.
                    operator fun plus(other: Point) : Point{
                        // 좌표를 성분별로 더한 새로운 점을 반환
                        return Point(x+other.x, y+other.y)
                }
                }
                 
                 
                >>>val p1 = Point(10,20)
                >>>val p2 = Point(30,40)
                //+로 계산하면 "plus"함수가 호출됨.
                >>>println(p1+p2)
                 
                 
                Point(x=40, y=60)

            연산자를 오버로딩하는 함수 앞에는 꼭 **operator**가 붙어야 함. 

            → 어떤 함수가 관례를 따르는 함수임을 명확히 하기 위해

            - 연산자를 확장함수로 정의하기

                operator fun Point.plus(other: Point) : Point {
                    return Point( x+ other.x, y+ other.y)
                }

            - 코틀린에서 정의할 수 있는 이항 연산자와 그에 상응하는 연산자 함수 이름

                [Untitled](https://www.notion.so/93f18b83dd1e42c08ecc645958e243b7)

        - 복합 대입 연산자 오버로딩

            plus와 같은 연산자를 오버로딩하면 코틀린은 + 연산자뿐만 아니라 그와 관련있는 연산자인 **+=**도 자동으로 함께 지원+=, -= 등의 연산자는 복합 대입 연산자라 불린다.

                >>>var point = Point(1,2)
                >>>point += Point(3,4)
                >>>println(point)
                Point(x=4, y=6)
                
                >>> val list = arrayList(1,2)
                // += 는 list를 변경
                >>> list += 3
                //+는 두 리스트의 모든 원소를 포함하는 새로운 리스트를 반환
                >>> val newList = list + listOf(4,5)
                >>> println(list)
                [1,2,3]
                >>> println(newList)
                [1,2,3,4,5]

        - 단항 연산자 오버로딩

            → 미리 정해진 이름의 함수(멤버나 확장함수로) 선언하면서 operator로 표시하면 된다.단항 연산자를 오버로딩하기 위해 사용하는 함수는 인자를 취하지 않음.

            [Untitled](https://www.notion.so/9995791c759347ba8175050652d72f18)

                //단항 연산자 정의하기
                operator fun Point.unaryMinus() : Point { // 단항 minus함수는 파라미터가 없음
                    return Point(-x, -y) // 좌표에서 각 성분의 음수를 취한 새 점을 반환
                }
                 
                 
                >>>val p = Point(10,20)
                >>>println(-p)
                Point(x=-10, y=-20)

        - 동등성 연산자 : equals

            == 연산자 호출은 equals 메소드 호출로 컴파일 함.

            = 연산자도 equals 호출로 컴파일 됨.

            a == b 라면,→ 코틀린에서는 a가 널인지 판단해서 널이 아닌 경우에만 a.equals(b)를 호출

        - 순서 연산자 : compareTo

            자바에서는 정렬이나 최솟값, 최댓값 등 값을 비교해야 하는 알고리즘에서 사용할 클래스는 Comparable 인터페이스를 구현해야 함.

            → Comparable에 들어있는 compareTo 메소드는 한 객체와 다른 객체의 크기를 비교해 정수로 나타냄  

            코틀린도 똑같은 Comparable 인터페이스르 지원. 

            코틀린은 Comparable 인터페이스 안에 있는 compareTo 메소드를 호출하는 관례를 제공 

            → < > <= >= 는 compareTo 호출로 컴파일→ compareTo의 반환값은 Int 이다. 

            예) p1 < p2 = p1.compareTo(p2) < 0

        - 컬렉션과 범위에 대해 쓸 수 있는 관례

            컬렉션을 다룰 때 가장 많이 쓰이는 연산은 인덱스를 사용해 원소를 읽거나, 쓰는 연산과 어떤 값이 컬렉션에 속해있는지 검사하는 연산인덱스를 사용해 원소를 설정하거나 가져오고 싶을 때는 a[b]라는 식을 사용 (이와 같은것을 인덱스 연산자라고 함)

            in연산자 : 원소가 컬렉션이나 범위에 속하는지 검사하거나 컬렉션에 있는 원소를 이터레이션할 때 사용

        - 인덱스로 원소에 접근 : get과 set

                //get관례 구현하기
                operator fun Point.get(index : Int) : Int {
                    return when(index){
                        0 -> x
                        1 -> y
                        else ->
                            throw IndexOutOfBoundsException("invalid coordinate $index")
                 
                 
                    }
                }
                 
                 
                >>> val p = Point(10,20)
                >>> println(p[1])
                20

        - in 관례

            객체가 컬렉션에 들어있는지 검사 → 대응하는 함수 contains

                //in관례 구현하기
                data class Rectangle(val upperLeft: Point, val lowerRight:Point)
                operator fun Rectangle.contains(p:Point) : Boolean{
                    //범위를 만들고 x 좌표가 그 범위 안에 있는지 검사
                    return p.x in upperLeft.x until lowerRight.x &&
                        p.y in upperLeft.y until lowerRight.y //until 함수를 사용해 열린 범위를 만든다.
                }
                 
                 
                >>> println(Point(20,30) in rect)
                true
                >>> println(Point(5,5) in rect)
                false

        - rangeTo 관례

            범위를 만들려면 .. 구문을 사용해야 함... 연산자는 rangeTo함수를 간략하게 표현하는 방법

            → rangeTo 함수는 범위를 반환함.

            이 연산자는 아무 클래스에나 정의할 수 있음. 하지만 어떤 클래스가 Comparable 인터페이스를 구현하면 rangeTo를 정의할 필요가 없음. 

            → 코틀린 표준 라이브러리를 통해 비교 가능한 원소로 이뤄진 범위를 쉽게 만들 수 있음.

        - for루프를 위한 iterator 관례

            코틀린의 for루프는 범위 검사와 똑같이 in 연산자를 사용함. 

            하지만 이 경우의 in의 의미는 for( x in list) { ... } 와 같은 문장은 list.iterator()를 호출해서 이터레이터를 얻은 다음, 자바와 마찬가지로 그 이터레이터에 대해 hasNext와 next 호출을 반복하는 식으로 변환

        - 구조 분해 선언과 component 함수

            구조 분해를 선언하면 복합적인 값을 분해해서 여러 다른 변수를 한꺼번에 초기화할 수 있음.

                >>> val p = Point(10,20)
                //x, y 변수를 선언한 다음에 p의 여러 컴포넌트로 초기화 함
                >>> val (x,y) = p
                >>> println(x)
                10
                >>> println(y)
                20

            구조 분해 선언은 일반 변수 선언과 비슷하지만, 다만 = 의 좌변에 여러 변수를 괄호로 묶었다는 점이 다름내부에서 구조 분해 선언은 다시 관례를 사용한다. 

            구조 분해 선언의 각 변수를 초기화하기 위해 componentN이라는 함수를 호출→ N은 구조 분해 선언에 있는 변수의 위치에 따라 붙는 변호

            data 클래스의 주 생성자에 들어있는 프로퍼티에 대해서는 컴파일러가 자동으로 componentN함수를 만들어줌.

        - 프로퍼티 접근자 로직 재활용 : 위임 프로퍼티

            위임프로퍼티 : 코틀린이 제공하는 관례에 의존하는 특성 중에서 독특하면서 강력한 기능

            위임프로퍼티를 사용하면 그 값을 뒷받침하는 필드에 단순히 저장하는 것보다 더 복잡한 방식으로 작동하는 프로퍼치를 쉽게 구현할 수 있음

            그 과정에서 접근자 로진을 매번 재구현할 필요가 없고, 예를 들어 프로퍼티는 위임을 사용해 자신의 값을 필드가 아니라 데이터베이스 테이블이나 브라우져 세션, 맵 등에 저장할 수 있음.

            위임은 객체가 직접

        - 위임객체가 직접 작업을 수행하지 않고 다른 도우미 객체가 그 작업을 처리하게 맡기는 디자인 패턴을 말함.

            → 이때 작업을 처리하는 도우미 객체를 위임객체라고 부름. (그 패턴을 프로퍼티에 적용해서 접근자 기능을 도우미 객체가 수행하게 위임한다. 

            도우미 객체를 직접 작성할 수도 있지만 더 나은 방법은 코틀린 언어가 제공하는 기능을 활용하는 것.)

        - 위임 프로퍼티 소개

                class Foo{
                    var p : Type by Delegate()
                }

            → p프로퍼티는 접근자 로직을 다른 객체에 위임한다. 여기서는 Delegate 클래스의 인스턴스를 위임 객체로 사용한다. by 뒤에 있는 식을 계산해서 위임에 쓰일 객체를 얻음

            프로퍼티 위임 객체가 따라야 하는 관례를 따르는 모든 객체를 위임에 사용할 수 있음.

        - 위임 프로퍼티 사용 : by lazy()를 사용한 프로퍼티 초기화 선언

            지연 초기화는 객체의 일부분을 초기화하지 않고 남겨뒀다가 실제로 그 부분의 값이 필요한 경우 초기화할 때 흔히 쓰이는 패턴초기화 과정에 자원을 많이 사용하거나 객체를 사용할 때마다 꼭 초기화하지 않아도 되는 프로퍼티에 대해 지연 초기화 패턴을 사용할 수 있음.

            → 예를 들어, person 클래스가 자신이 작성한 이메일의 목록을 제공한다고 가정할 때, 이메일은 데이터베이스에 들어있고, 불러오려면 시간이 오래 걸린다. 

            그래서 이메일 프로퍼티의 값을 최초로 사용할 때 단 한번만 이메일을 데이터베이스에서 가져오고 싶다.이제 데이터베이스에서 이메일을 가져오는 loadEmails 함수가 있다고 하자.

                class Person(val name:String){
                    //데이터를 저장하고 emails의 위임 객체 역할을 하는 _emails의 프로퍼티
                    private var_emails: List<Email>? = null
                    val emails: List<Email>>
                        get(){
                            if(emails==null){
                                //최초 접근 시 이메일을 가져온다.
                                _emails = loadEmails(this)
                    }
                            return _emails!! //저장해둔 데이터가 있으면 그 데이터를 반환한다.
                }
                }
                 
                 
                >>> val p = Person("Alice")
                >>> p.emails // 최초로 emails를 읽을 때 단 한번만 이메일을 가져온다.
                Load emails for Alice
                >>> p.emails

            여기서는 **뒷밤침하는 프로퍼티**라는 기법을 사용함._emails 라는 프로퍼티는 값을 저장하고, 다른 프로퍼티인 emails는 _emails라는 프로퍼티에 대한 읽기 연산을 제공한다.

            _emails는 널이 될 수 있는 타입인 반면 emails는 널이 될 수 없는 타입이므로 프로퍼티를 두 개 사용해야 한다.

        - 위임 프로퍼티 구현

            어떤 객체의 프로퍼티가 바뀔 때마다 리스너에게 변경 통지를 보내고 싶다. 이런 기능이 유용할 때가 많은데, 예를 들어 어떤 객체를 UI에 표시하는 경우 객체가 바뀌면 자동으로 UI도 바뀌어야 한다. 자바에서는 propertychangesupport와 propertychangeevent클래스를 사용해 이런 통지를 처리하는 경우가 자주 있음.

            → 이제 코틀린에서 위임 프로퍼티 없이 이런 기능을 구현하고 나중에 그 코드를 위임 프로퍼티를 사용하게 리팩토링해보자.

            → propertychangesupport 클래스는 리스너의 목록을 관리하고 propertychangeevent 이벤트가 들어오면 목록의 모든 리스너에게 이벤트를 통지함.

            자바 빈 클래스의 필드에 propertychangesupport 인스턴스를 저장하고 프로퍼티 변경 시 그 인스턴스에게 처리를 위임하는 방식으로 이런 통지 기능을 주로 구현함.

        - 위임 프로퍼티 컴파일 규칙

                class C{
                    var prop : Type by MyDelegate()
                }
                 
                 
                var c = C()

            → 컴파일러는 mydelegate 클래스의 인스턴스를 감춰진 프로퍼티에 저장하며 그 감춰진 프로퍼티는 <delegate>라는 이름으로 부른다. 또한 컴파일러는 프로퍼티를 표현하기 위해 kproperty 타입의 객체를 사용 

            → 이러한 객체의 이름을 <property>부른다.

                //컴파일러는 다음 코드를 생성
                class C{
                    private val <delegate> = MyDelegate()
                    var prop : Type
                    get() = <delegate>.getValue(this, <property>)
                    set(value : Type) = <delegate>.setValue(this, <property>, value)
                    }
                // 컴파일러는 모든 프로퍼티 접근자 안에 다음과 같이 getvalue 와 setvalue 호출 코드를 생성해 줌.
                val x = c.prop -> val x = <delegate>.getvalue(c, <property>)
                c.prop = x -> <delegate>.setvalue(c, <property>, x)
                -> 프로퍼티 값이 저장될 장소를 바꿀 수 도 있고 프로퍼티를 읽거나 쓸 때 벌어질 일을 변경할 수도 있음. => 이러한 것들을 간결한 코드로 달성할 수 있음.

        - 프로퍼티 값을 맵에 저장

            자신의 프로퍼티를 동적으로 정의할 수 있는 객체를 만들 때 위임 프로퍼티를 활용하는 경우가 자주 있음.그런 객체를 **확장 가능한 객체**라고 부른다.

            예) 연락처 관리 시스템에서 연락처 별로 임의의 정보를 저장할 수 있게 허용하는 경우를 살펴보면, 시스템에 저장된 연락처에는 특별히 처리해야하는 일부 필수 정보(이름 등)이 있고, 사람마다 달라질 수 있는 추가정보가 있음(예를 들어 제일 어린 자식의 생일 등)

            → 이런 시스템을 구현하는 방법 중에는 정보를 모두 맵에 저장하되 그 맵을 통해 처리하는 프로퍼티를 통해 필수 정보를 제공하는 방법이 있음.

        - 프레임워크에서 위임 프로퍼티 활용

            객체 프로퍼티를 저장하거나 변경하는 방법을 바꿀 수 있으면 프레임워크를 개발할 때 유용

            → 데이터베이스의 내용을 위임 프로퍼티를 이용해서 쉽게 가져올 수 있음. 

                //객체는 데이터베이스 테이블에 해당 , 프로퍼티는 테이블 칼럼에 해당
                object User : IdTable(){
                    val name : varchar("name", length=50).index()
                    val age = integer("age")
                }
                // 각 user 인스턴스는 테이블에 들어있는 구체적인 엔티티에 해당
                class User(id : EntityID) : Entity(id){
                    //사용자 이름은 데이터베이스 "name" 칼럼에 들어있음.
                    var name : String by Users.name
                    var age : Int by Users.age
                }

            - 요약

            - 코틀린에서는 정해진 이름의 함수를 오버로딩함으로써 표준 수학 연산자를 오버로딩할 수 있음. → 하지만 새로운 연산자를 만들 수는 없음

            - 비교연산자는 equals와 compareTo 메소드로 변환된다.

            - 클래스에 get, set, contains 라는 함수를 정의하면 그 클래스의 인스턴스에 대해 []와 in 연산을 사용할 수 있고, 그 객체를 코틀린 컬렉션 객체와 비슷하게 다룰 수 있음.

            - 미리 정해진 관례를 따라 rangeTo, iterator 함수를 정의하면 범위를 만들거나 컬렉션과 배열의 원소를 이터레이션할 수있음.

            - 구조 분해 선언을 통해 한 객체의 상태를 분해해서 여러 변수에 대입할 수 있음. 함수가 여러 값을 한꺼번에 반환해야 하는 경우 구조 분해가 유용→ 데이터 클래스에 대한 구조 분해는 거저 사용할 수 있지만, 커스텀 클래스의 인스턴스에서 구조 분해를 사용하려면 componentN 함수를 정의해야 함.

            - 위임 프로퍼티를 통해 프로퍼티 값을 저장하거나 초기화하거나 읽거나 변경할 때 사용하는 로직을 재활용할 수 있음.

            - 위임 프로퍼티는 프레임워크를 만들 때 아주 유용

            - 표준 라이브러리 함수인 lazy를 통해 지연 초기화 프로퍼티를 쉽게 구현할 수 있음

            - Delegates.observable 함수를 사용하면 프로퍼티 변경을 관찰할 수 있는 관찰자를 쉽게 추가할 수 있음.

            - 맵을 위임 객체로 사용하는 위임 프로퍼티를 통해 다양한 속성을 제공하는 객체를 유연하게 다룰 수 있음.

        ## 9장 제네릭

        - 제네릭 함수와 클래스를 정의하는 방법
        - 타입 소거와 실체화한 타입 파라미터
        - 선언 지점과 사용지점 변성

        실체화한 타입 파라미터 / 선언 지점 변성

        실체화한 타입 파라미터를 사용하면 인라인 함수 호출에서 타입 인자로 쓰인 구체적인 타입을 실행 시점에 알 수 있음.

        → 일반 클래스나 함수의 경우 타입 인자 정보가 실행 시점에 사라지기 때문에 이런 일이 불가능함

        선언 지점 변성을 사용하면, 기저 타입은 같지만 타입 인자가 다른 두 제네릭 타입 Type<A> 와 Type<B>가 있을때 타입 인자 A와 B의 상위/하위 타입 관계에 따라 두 제네릭 타입의 상위/하위 타입 관계가 어떻게 되는지 지정할 수 있음

        예) List<Any> 를 인자로 받는 함수에게 List<Int> 타입의 값을 전달할 수 있을지 여부를 **선언 지점 변성**을 통해 지정할 수 있음.

        사용지점 변성 같은 목표를 제네릭 타입 값을 사용하는 위치에서 파라미터 타입에 대한 제약을 표시하는 방식으로 달성

        (자바 와일드카드는 사용 지점 변성에 속하며, 코틀린 선언 지점 변성과 같은 역할을 함.)

        - 제네릭 타입 파라미터

        제네릭스를 사용하면 타입 파라미터를 받는 타입을 정의할 수 있음.제네릭 타입의 인스턴스를 만들려면 타입 파라미터를 구체적인 **타입 인자**로 치환해야 함.예) List라는 타입이 있다면 그 안에 들어가는 원소의 타입을 안다면 쓸모가 있을 것. 타입 파라미터를 사용하면 "이 변수는 리스트다"라고 말하는 대신 정확하게 "이 변수는 문자열을 담는 리스트다."라고 말할 수 있음. 코틀린에서 문자열을 담는 리스트를 표현하는 구문은 자바와 마찬가지로 List<String>클래스에 타입 파라미터 여러개 있을 수도 있음.

        빈 리스트를 만들어야 한다면 타입인자를 추론할 근거가 없기 때문에 직접 타입인자를 명시해야 함.

            * 리스트를 만들 때 변수의 타입을 지정해도 되고 변수를 만드는 함수의 타입 인자를 지정해도 됨.
            //두 선언은 동일
            val readers: MutableList<String> = mutableListOf()
            val readers = mutableListOf<String>()

        자바와 달리 코틀린에서는 제너릭 타입의 타입 인자를 프로그래머가 명시하거나 컴파일러가 추론할 수 있어야 함.

        - 제네릭 함수와 프로퍼티

        제네릭 함수를 호출할 때 반드시 구체적 타입으로 타입 인자를 넘겨야 함.→ 컬렉션을 다루는 라이브러리 함수는 대부분 제네릭 함수

            * 제네릭 함수인 slice는 T를 타입 파라미터로 받음.
            fun <T> List<T>.slice(indices:IntRange) : List<T>
            // 타입 파라미터가 수신 객체와 반환 타입에 쓰임

        - 제네릭 클래스 선언

            자바와 마찬가지로 코틀린에서도 타입 파라미터를 넣은 꺾쇠 기호(<>)를 클래스 이름 뒤에 붙이면 클래스를 제네릭하게 만들 수있음.타입 파라미터를 이름 뒤에 붙이고 나면 클래스 본문 안에서 타입 파라미터를 다른 일반 타입처럼 사용할 수 있음.표준 자바 인터페이스인 List 를 코틀린으로 정의하면 다음과 같다.

        - 타입 파라미터 제약

            타입 파라미터 제약은 클래스나 함수에 사용할 수 있는 타입 인자를 제한하는 기능어떤 타입을 제네릭 타입의 타입 파라미터에 대한 상한으로 지정하면 그 제네릭 타입을 인스턴스화 할때 사용하는 타입 인자는 반드시 그 **상한** 타입이거나 그 상한타입의 하위 타입이여야 함. 

            T의 상한 타입은 comparable<T>. first > second 라는 식은 코틀린 연산자 관례에 따라 first.compareTo(second) > 0이라고 컴파일된다는 점을 기억

                //타입 파라미터 뒤에 상한을 지정함으로써 제약을 정의할 수 있음
                fun <T:Numbers> List<T>.sum() : T
                 
                >>>println(listOf(1,2,3).sum())
                6

            → 타입 파라미터 T에 대한 상한을 정하고 나면 T타입의 값을 그 상한 타입의 값으로 취급할 수 있음.

                //number를 타입 파라미터 상한으로 정함.
                fun <T : Number> oneHalf(value:T) : Double {
                    //Number 클래스에 정의된 메소드를 호출
                    return value.toDouble() / 2.0
                }
                >>> println(oneHalf(3))
                1.5

                //타입 파라미터를 제약하는 함수 선언하기
                fun <T:Comparable<T>> max(first : T, second:T) :T{
                    return if(first > seconde) first else second // 이 함수의 인자들은 비교가 가능해야 함.
                }
                 
                 
                >>>println(max("kotlin", "java")) // 문자열은 알파벳순으로 비교됨
                kotlin

            → max를 비교할 수 없는 값 사이에 호출하면 컴파일 오류가 남.

            >>> println(max("kotlin", 42))→ error 발생

            → 타입 인자가 charsequence와 appendable 인터페이스를 반드시 구현해야한다는 사실을 표현

                //타입 파라미터에 여러 제약을 가하기 
                fun <T> ensureTrailingPeriod(seq : T){
                    where T : CharSequence, T: Appendable { //타입 파라미터 제약 목록
                        if(!seq.endsWith('.')){ //charsequence 인터페이스의 확장 함수를 호출
                            seq.append('.') // appendable 인터페이스의 메소드를 호출
                        }
                }
                }
                 
                 
                >>> val helloWorld = StringBuilder("Hello World")
                >>> ensureTrailingPeriod(helloWorld)
                >>> println(helloWorld)
                Hello World

        - 타입 파라미터를 널이 될 수 없는 타입으로 한정

            제네릭 클래스나 함수를 정의하고 그 타입을 인스턴스화할 때는 널이 될 수 있는 타입을 포함하는 어떤 타입으로 타입 인자를 지정해도 타입 파라미터를 치환할 수 있음.→ 아무런 상한을 정하지 않은 타입 파라미터는 결과적으로 Any? 를 상한으로 정한 파라미터와 같음

                class Processor<T>{
                    fun process(value: T){
                        value?.hashCode() //"value"는 널이 될 수 있다. 따라서 안전한 호출을 사용해야함
                }
                }

            - <T : Any> 라는 제약은 T타입이 항상 널이 될 수 없는 타입이 되게 보장함.→ 타입 파라미터를 널이 될 수 없는 타입으로 제약하기만 하면 타입 인자로 널이 될 수 있는 타입이 들어오는 일을 막을 수 있음.

        - 실행 시 제네릭스의 동작 : 소거된 타입 파라미터와 실체화된 타입 파라미터

        JVM의 제네릭스는 보통 **타입 소거**를 사용해 구현 된다. → 실행 시점에 제네릭 클래스의 인스턴스에 타입 인자 정보가 들어있지 않다는 뜻

        - 실행 시점의 제네릭 : 타입 검사와 캐스트

            자바와 마찬가지로 코틀린 제네릭 타입 인자정보는 런타임에 지워진다. → 제네릭 인스턴스가 그 인스턴스를 생성할 떄 쓰인 타입 인자에 대한 정보를 유지하지 않는다는 뜻 

            예) List<String> 객체를 만들고 그 안에 문자열을 여럿 넣더라도 실행 시점에는 그 객체를 오직 list로만 볼 수 있음. 그 list객체가 어떤 타입의 원소를 저장하는지 실행 시점에는 알 수 없다. 

            - 타입 소거로 인해 생기는 한계

            타입 인자를 따로 저장하지 않기 때문에 실행 시점에 타입 인자를 검사할 수 없음.

                >>> if(value is List<String>){ ... }
                ERROR : Cannot check for for instance of erased type

            예) 어떤 리스트가 문자열로 이뤄진 리스트인지 다른 객체로 이뤄진 리스트인지 실행 시점에 검사할 수 없음

            다만 저장 해야 하는 타입 정보의 크기가 줄어들어서 전반적인 메모리 사용량이 줄어든다는 제네릭 타입 소거 나름의 장점이 있음.  

            스타 프로젝션 : 어떤 값이 집합이나 맵이 아니라 리스트라는 사실을 어떻게 확인할 수 있을까? 이때 사용하는 것이 스타 프로젝션

             (코틀린에서는 타입 인자를 명시하지 않고 제네릭 타입을 사용할 수 없음.)

            → 인자를 알 수 없는 제네릭 타입을 표현할 때 (자바의 List<?>와 비슷함) 스타 프로젝션을 씀타입파라미터가 2개 이상이라면 모든 타입 파라미터에 * 를 포함시켜야 함.

                //제네릭 타입으로 타입 캐스팅 하기 
                fun printSum(c: Collection<*>){
                    //아래에서 unchecked cast : List <*> to List<Int> 경고가 발생
                    val intList = c as? List<Int>
                        ?: throw IllegalArgumentException("List is expected")
                    println(intList.sum())
                }
                 
                 
                //예상대로 작동
                >>> printSum(listOf(1,2,3))
                6
                
                >>> printSum(setOf(1,2,3)) // 집합은 리스트가 아니므로 예외가 발생
                IllegalArgumentException : List is expected
                 
                 
                >>> printSum(listOf("a","b","c"))
                ClassCastException: String cannot be cast to Number // as? 캐스팅은 성공하지만 나중에 다른 예외가 발생

            → 실행 시점에 어떤 값이 List인지 여부는 확실히 알아낼 수 있지만, 그 리스트가 String의 리스트인지, Person의 리스트 인지 혹은 다른 어떤 타입의 리스트인지는 알 수가 없다. → 그러한 정보는 지워짐

        - 코틀린 컴파일러는 컴파일 시점에 타입 정보가 주어진 경우에는 is 검사를 수행하게 허용할 수 있을 정도로 똑똑하다.

                // 알려진 타입 인자를 사용해 타입 검사하기
                fun printSum(c: Collection<Int>){
                    if(c is List<Int>){ // 이런 검사는 올바르다.
                        println(c.sum())
                }
                }

            → 컴파일 시점에 c 컬렉션(리스트나 집합 등 종류는 문제가 안된다.)이 **Int 값을 저장한다는 사실이 알려져 있으므로** c가 List<Int> 인지 검사할 수 있음.

            (일반적으로 코틀린 컴파일러는 안전하지 못한 검사와 수행할 수 있는 검사를 알려주기 위해 최대한 노력한다. 안전하지 못한 is검사는 금지하고 위험한 as캐스팅은 경고를 출력)

        - **실체화한 타입 파라미터**를 사용한 함수 선언

            코틀린 제네릭 타입 인자 정보는 실행 시점에 지워짐. 따라서 제네릭 클래스의 인스턴스가 있어도 그 인스턴스를 만들 때 사용한 타입 인자를 알아낼 수 없음. 

                fun<T> isA(value: Any) = value is T
                ERROR : Cannot check for instance of erased type : T

            → 인라인 함수의 타입 파라미터는 실체화되므로 실행 시점에 인라인 함수의 타입 인자를 알 수 있음.

            inline 함수: 어떤 함수에 inline 키워드를 붙이면 컴파일러는 그 함수를 호출한 식을 모두 함수 본문으로 바꿔준다.

            → 방금 위의 함수 isA를 인라인 함수로 만들고 타입 파라미터를 reified로 지정하면 value 의 타입이 T의 인스턴스인지를 실행 시점에 검사할 수 있음.  

                //실체화한 타입 파라미터를 사용하는 함수 정의하기 
                inline fun<reified T> isA(value : Any) = value is T // 아까 위에서는 오류가 났지만 inline 키워드를 붙이고, reified를 붙임으로써 오류가 사라짐.
                >>> println(isA<String>("abc"))
                true
                >>>println(isA<String>(123))
                false

            reified 키워드는 이 타입 파라미터가 실행 시점에 지워지지 않음을 표시

        - 실체화한 타입 파라미터로 클래스 참조 대신

            java.lang.Class 타입 인자를 파라미터로 받는 API에 대한 **코틀린 어댑터**를 구축하는 경우 실체화한 타입 파라미터를 자주 사용

            java.lang.Class를 사용하는 API의 예로는 JDK의 ServiceLoader가 있음. 

            → 어떤 추상 클래스나 인터페이스를 표현하는 java.lang.Class를 받아서 그 클래스나 인스턴스를 구현한 인스턴스를 반환함.

            → 실체화한 타입 파라미터를 활용해 이런 API를 쉽게 호출할 수 있게 만드는 방법

        - 실체화한 타입 파라미터의 제약실체화한 타입 파라미터는 유용한 도구지만 몇 가지 제약이 있음.
        - 일부는 실체화의 개념으로 인해 생기는 제약이며, 나머지는 지금 코틀린이 실체화를 구현하는 방식에 의해 생기는 제약으로 향후 완화될 가능성이 있음.
        - 실체화한 타입 파라미터를 사용할 수 있는 경우

            1. 타입 검사와 캐스팅 (is, is, as, as?)

            2. 10장에서 설명할 코틀린 리플렉션 API(::class)

            3. 코틀린 타입에 대응하는 java.lang.Class를 얻기(::class.java)

            4. 다른 함수를 호출할 때 

        - 타입 인자로 사용 할 수 없는 일

            1. 타입 파라미터 클래스의 인스턴스 생성하기

            2. 타입 파라미터 클래스의 동반 객체 메소드 호출하기

            3. 실체화한 타입 파라미터를 요구하는 함수를 호출하면서 실체화하지 않은 타입 파라미터로 받은 타입을 타입 인자로 넘기기

            4. 클래스, 프로퍼티, 인라인 함수가 아닌 함수의 타입 파라미터를 reified로 지정하기

        - 변성 : 제네릭과 하위 타입변성 variance라는 개념은 List<String> 와 List<Any> 와 같이 기저 타입이 같고 타입 인자가 다른 여러 타입이 서로 어떤 관계가 있는지 설명하는 개념

        (직접 제네릭 클래스나 함수를 정의하는 경우 변성을 꼭 이해해야 함. 

        → 변성을 잘 활용하면 사용에 불편하지 않으면서 타입 안전성을 보장하는 API를 만들 수 있음.)

        - 변성이 있는 이유 : 인자를 함수에 넘기기List<Any>타입의 파라미터를 받는 함수에 List<String>을 넘기면 안전한가?

            → String클래스는 Any를 확장하므로 Any타입 값을 파라미터로 받는 함수에 String 값을 넘겨도 절대로 안전함.하지만, Any와 String이 List 인터페이스의 타입 인자로 들어가는 경우 그렇게 자신있게 안전성을 말할 수 없다.

                //리스트의 내용을 출력하는 함수
                fun printContents(list: List<Any>){
                    println(list.joinToString())
                }
                 
                 
                >>> printContents(listOf("abc","bac"))
                abc, bac
                -> 이 경우에 문자열 리스트도 잘 작동하고, 각 원소를 Any로 취급하며 모든 문자열은 Any 타입이기도 하므로 완전히 안전함.
                 
                 
                // 리스트를 변경하는 다른 함수
                fun addAnswer(list:MutableList<Any>){
                    list.add(42)
                }
                 
                 
                // 이 함수에 문자열 리스트를 넘기게 되면?
                >>> val strings = mutableListOf("abc", "bac")
                >>> addAnswer(strings) // 이 줄이 컴파일된다면
                >>> println(strings.maxBy { it.length}) // 실행 시점에 예외가 발생할 것
                ClassCastException: Integer cannot be cast to String

        - 클래스, 타입, 하위 타입변수의 타입이 그 변수에 담을 수 있는 값의 집합을 지정함.

            제네릭 타입에서 올바른 타입을 얻으려면 제네릭 타입의 타입 파라미터를 구체적인 타입 인자로 바꿔줘야 함.예) List는 타입이 아니다. (클래스이다.)

            하지만 타입 인자를 치환한 List<Int>, List<String?>, List<List<String>> 등은 모두 제대로 된 타입 → 각각의 제네릭 클래스는 무수히 많은 타입을 만들어낼 수 있음.

        - 타입사이의 관계를 논하기 위해 **하위 타입**이라는 개념을 알아야 함.
        - 하위타입 : 어떤 타입 A의 값이 필요한 모든 장소에 어떤 타입 B의 값을 넣어도 아무 문제가 없다면 타입 B는 타입 A의 하위 타입예) Int는 Number의 하위 타입이지만 String은 Number의 하위 타입은 아님
        - 상위타입 : 하위타입의 반대. A 타입이 B타입의 하위 타입이라면 B는 A의 상위 타입 한 타입이 다른 타입의 하위 타입인지 중요한 이유 컴파일러는 변수 대입이나 함수 인자 전달 시 하위 타입 검사를 매번 수행한다.

                //어떤 타입이 다른 타입의 하위 타입인지 검사하기
                fun test(i: Int){
                    val n : Number = i // Int가 Number의 하위 타입이어서 컴파일 됨.
                 
                 
                    fun f(s: String){/*..*/}
                    f(i) // Int가 String의 하위타입이 아니여서 컴파되지 않음
                }

            → 어떤 값의 타입이 변수 타입의 하위 타입인 경우에만 값을 변수에 대입하게 허용

            이 예제에서 변수를 초기화한 i의 Int로 변수의 타입인 Number의 하위 타입 → 따라서, 올바른 대입함수에 전달하는 식의 타입이 함수 파라미터 타입의 하위타입인 경우에만 함수 호출이 허용됨.

        - 간단한 경우, **하위 타입**은 **하위 클래스**와 근본적으로 같음.예) Int 클래스는 Number의 하위 클래스이므로 Int는 Number의 하위 타입널이 될 수없는 타입은 널이 될 수 있는 타입의 하위 타입이지만, 거꾸로는 성립하지 않음.

                val s : String = "abc"
                val t : String? = s // String이 String?의 하위타입이므로 이 대입은 합법적

            → 제네릭 타입을 인스턴스화할 때 타입 인자로 서로 다른 타입이 들어가면 인스턴스 타입 사이의 하위 타입 관계가 성립하지 않으면 그 제네릭 타입을 **무공변**이라고 말함.

            MutableList를 예로 들면 A와 B가 서로 다르기만 하면 MutableList<A>는 항상 Mutable<B>의 하위 타입이 아니다. 자바에서 모든 클래스가 무공변.→ A가 B의 하위 타입이면 List<A>는 List<B>의 하위 타입

            : 이런 클래스나 인터페이스를 **공변적**이라 말함.

        - **공변성** : 하위 타입 관계를 유지

             A가 B의 하위 타입일 때, Producer<A>가 Producer<B>의 하위 타입이면 Producer는 공변적. → 하위 타입 관계가 유지된다고 말함

            예) Cat이 Animal의 하위 타입이기 때문에 Producer<Cat>은 Producer<Animal> 의 하위 타입→ 코틀린에서 제네릭 클래스가 타입 파라미터에 대해 공변적임을 표시하려면 타입 파라미터 이름 앞에 out을 넣어야 함.

                //타입 파라미터 앞에 out을 넣어 공변적임을 표시
                interface Producer<out T>{ //클래스가 T에 대해 공변적이라고 선언함.
                    fun produce() : T
                }

             

            → 클래스의 타입 파라미터를 공변적으로 만들면 함수 정의에 사용한 파라미터 타입과 타입인자의 타입이 정확히 일치하지 않더라도 그 클래스의 인스턴스를 함수 이나나 반환 값으로 사용할 수 있음.

            예) Herd 클래스로 표현되는 동물 무리의 사육을 담당하는 함수가 있다고 할 때, Herd 클래스의 타입 파라미터는 그 떼가 어떤 동물 무리인지 알려줌.

                //무공변 컬렉션 역할을 하는 클래스 정의하기
                open class Animal {
                    fun feed(){...}
                }
                 
                 
                class Herd<T:Animal>{ // 이 타입 파라미터를 무공변성으로 지정
                    val size : Int get() =  ...
                    operator fun get(i:Int): T{...}
                }
                 
                 
                fun feedAll(animals : Herd<Animal>){
                    for(i in 0 unitl animals.size){
                        animals[i].feed()
                }
                }
                 
                 
                //사용자 코드가 고양이 무리를 만들어서 관리한다고 한다면,
                class Cat : Animal(){
                    fun cleanLitter(){...}
                }
                 
                 
                fun takeCareOfCats(cats : Herd<Cat>){
                    for(i in 0 until cats.size){
                    cats[i].cleanLitter()
                        //feedAll(cats) Error : inferred type is Herd<Cat>, but Herd<Animal> was expected라는 오류가 발생
                }
                }
                -> feedAll 함수에 고양이 무리를 넘기면 타입 불일치 오류가 나옴.
                Herd 클래스의 T타입 파라미터에 대해 아무 변성도 지정하지 않았기 때문에, 고양이 무리는 동물 무리의 하위 클래스가 아님
                명시적으로 타입 캐스팅을 사용하면 이 문제를 풀 수 있긴 하지만 그런 식으로 처리하면 코드가 장황해지고 실수를 하기 쉬움.

            → **Herd**를 **공변 클래스**로 만들고 호출 코드를 적절히 바꿀 수 있음.

                //공변적 컬렉션 역할을 하는 클래스 사용하기
                class Herd<out T: Animal> { //T는 이제 공변적
                    ...
                }
                 
                 
                fun takeCareOfCats(cats:Herd<Cat>){
                    for( i in 0 until cats.size){
                        cats[i].cleanLitter()
                    }
                    feedAll(cats) // 캐스팅을 할 필요가 없음.
                }

            → 모든 클래스를 공변적으로 만들 수는 없지만, 공변적으로 만들면 안전하지 못한 클래스도 있음.

            타입파라미터를 공변적으로 지정하면 클래스 내부에서 그 파라미터를 사용하는 방법을 제한함. → 타입 안전성을 보장하기 위해 **공변적 파라미터는 항상 아웃 위치에만 있어야함.**

            **→ 이는 클래스가 T타입의 값을 생산할 수 있지만 T타입의 값을 소비할수는 없다는 뜻**

            클래스 멤버를 선언할 때 타입 파라미터를 사용할 수 있는 지점은 모두 인과 아웃위치로 나뉜다.T라는 타입 파라미터를 선언하고 T를 사용하는 함수가 멤버로 있는 클래스에서- T가 함수의 반환 타입에 쓰인다면, T는 아웃 위치에 있음. → 그 함수는 T타입의 값을 생산함.- T가 함수의 파라미터 타입에 쓰인다면 T는 인 위치에 있음. → T타입의 값을 소비함.

                //함수 파라미터 타입은 인 위치, 함수 반환 타입은 아웃 위치에 있음.
                interface Transformer<T>{
                    fun transform(t: T) : T
                }
                 
                 
                인을 넣고 싶다면 ()안의 T의 위치에, 아웃은 : 옆의 T의 위치에
                // 클래스 타입 파라미터 T앞에 out 키워드를 붙이면 클래스 안에서 T를 사용하는 메소드가 아웃 위치에서만 T를 사용하게 허용하고 인 위치에서는 T를 사용하지 못하게 막음.
                out 키워드는 T의 사용법을 제한하며 T로 인해 생기는 하위 타입 관계의 타입 안정성을 보장

                class Herd<out T: Animal>{
                    val size : Int get() = ...
                    operator fun get(i: Int) : T {...} //T를 반환 타입으로 사용
                 
                 
                }

            → 이 위치(함수의 반환 타입)는 아웃 위치

            → 따라서 이 클래스를 공변적으로 선언해도 안전

            → Cat이 Animal의 하위 타입이기 때문에 Herd<Animal> 의 get을 호출하는 모든 코드는 get이 Cat을 반환해도 아무 문제없이 작동

        - List<T>의 인터페이스에서코틀린 List는 읽기 전용→ 그 안에는 T타입의 원소를 반환하는 get 메소드는 있지만 리스트에 T타입의 값을 추가하거나 리스트에 있는 기존 값을 변경하는 메소드는 없음. 따라서 List는 T에 대해 공변적

                // 읽기 전용 메소드로 T를 반환하는 메소드만 정의함 (따라서 T는 항상  "아웃" 위치에 쓰임)
                interface List<out T> : Collection<T> {
                    operator fun get(index : Int)
                    // ...
                }

            타입 파라미터를 함수의 파라미터 타입이나 반환 타입에만 쓸 수 있는 것은 아니다.타입 파라미터를 다른 타입의 타입 인자로 사용할 수도 있음. 예) List 인터페이스에는 List<T>를 반환하는 subList라는 메소드가 있음

                interface List<out: T> : Collection<T>{
                    fun subList(fromIndex : Int, toIndex: Int) : List<T> //여기서도 T는 아웃 위치에 있다.
                    // ...
                }

        - 변성은 코드에서 위험할 여지가 있는 메소드를 호출할 수 없게 만듦으로써 제네릭 타입의 인스턴스 역할을 하는 클래스 인스턴스를 잘못 사용하는 일이 없게 방지하는 역할을 함.

            (val이나 var 키워드를 생성자 파라미터에 적는다면 게터나 세터를 정의하는 것과 같음 → 따라서 읽기 전용 프로퍼티는 아웃 위치, 변경 가능 프로퍼티는 아웃과 인 위치 모두에 해당)

                class Herd<T:Animal>(var leadAnimal: T, vararg animals:T) {...}
                // 여기서는 T타입인 leadAnimal 프로퍼티가 인 위치에 있기 때문에 T를 out으로 표시할 수 없음.
                이런 위치 규칙은 오직 외부에서 볼 수 있는 (public, protected, internal) 클래스 API에만 적용할 수 있음
                변성규칙은 클래스 외부의 사용자가 클래스를 잘못 사용하는 일을 막기 위한 것이므로 클래스 내부 구현에는 적용되지 않음.

        - **반공변성** : 뒤집힌 하위 타입 관계

            공변성을 거울에 비친 상 → 반공변 클래스의 하위 타입관계는 공변 클래스의 경우와 반대

            예) Comparator 인터페이스를 살펴보면 이 인터페이스에는 compare라는 메소드가 있음.

            이 메소드는 주어진 두 객체를 비교함 

                interface Comparator<in T>{
                    fun compare(e1: T, e2:T):Int{...} // T를 "인"위치에 사용
                }

            → 이 인터페이스의 메소드는 T타입의 값을 소비하기만 함

            이는 T가 인 위치에서만 쓰인다는 뜻 → 따라서 T 앞에는 in 키워드를 붙여야만 함.물론 어떤 타입에 대해 comparator를 구현하면, 그 타입의 하위 타입에 속하는 모든 값을 비교할 수 있음.예를 들어 Comparator<Any>가 있다면, 이를 사용하여 모든 타입의 값을 비교할 수 있음

                >>> val anyComparator = Comparaotr<Any>{
                    e1, e2 -> e1.hashCode() - e2.hashCode()
                }
                >>> val strings : List<String> = ...
                >>> strings.sortedWith(anyComparator) // 문자열과 같은 구체적인 타입의 객체를 비교하기 위해 모든 객체를 비교하는 Comparator를 사용할 수 있음.
                }

            Comsumer<T>를 예로 들 때,타입 B가 타입 A의 하위 타입인 경우 Consumer<A>가 Consumer<B>의 하위 타입인 관계가 성립하면 제네릭 클래서 Consumer<T>는 타입 인자 T에 대해 반공변

        [Untitled](https://www.notion.so/9aa5b55f587a4e66b33f261cbb9ffb65)

        클래스나 인터페이스 어떤 타입 파라미터에 대해서는 공변적이면서 다른 타입 파라미터에 대해서는 반공변적일 수도 있음.

        Function 인터페이스가 고전적인 예

            //파라미터가 하나뿐인 function 인터페이스인 funtion1
            interface Function1<in P, out P>{
                operator fun invoke(p:P) : R
            }

        코틀린 표기에서 (P) → R 은 Function1<P,R>을 더 알아보기 쉽게 적은 것

        → P(함수 파라미터의 타입)는 오직 인 위치

        → R(함수 반환 타입)은 오직 아웃 위치에 사용된다는 사실

        - 사용 지점 변성 : 타입이 언급되는 지점에서 변성 지정클래스를 선언하면서 변성을 지정하면 그 클래스를 사용하는 모든 장소에 변성 지정자가 영향을 끼치므로 편리함.자바에서는 타입 파라미터가 있는 타입을 사용할 때마다 해당 타입 파라미터를 하위 타입이나 상위 타입 중 어떤 타입으로 대치할 수 있는지 명시해야 함.→ 사용 지점 변성

            클래스 안에서 어떤 타입 파라미터가 공변적이거나 반공변적인지 선언할 수 없는 경우에도 특정 타입 파라미터가 나타나는 지점에서 변성을 정할 수 있음.

                //무공변 파라미터 타입을 사용하는 데이터 복사 함수
                fun <T> copyData(source : MutableList<T>,
                                        destination:MutableList<T>){
                        for(item in source){
                            destination.add(item)
                        }
                }

            → 이 함수는 컬렉션의 원소를 다른 컬렉션으로 복사함. 두 컬렉션 모두 무공변 타입이지만 원본 컬렉션에서는 읽기만 가능하고 대상 컬렉션에서는 쓰기만 함. 이 경우 두 컬렉션의 원소 타입이 정확히 일치할 필요가 없음

            예) 문자열이 원소인 컬렉션에서 객체의 컬렉션으로 원소를 복사해도 아무 문제가 없음.→ 이 함수가 여러 다른 리스트 타입에 대해 작동하게 만들려면 두 번째 제네릭 타입 파라미터를 도입할 수 있음.

        - 스타프로젝션 : 타입인자 대신 * 사용제네릭 타입 인자 정보가 없음을 표현하기 위해 스타 프로젝션을 사용예) 는 **List<*>** 라는 구문으로 표현할 수 있음.

            원소 타입이 알려지지 않은 리스트

        - Mutablelist<*>는 mutablelist<any?> 와 같지 않다.
        - mutablelist<any?>는 모든 타입의 원소를 담을 수 있다는 사실을 알 수 있는 리스트 ↔ mutablelist<*>는 어떤 구체적인 타입의 원소만을 담는 리스트지만 그 원소의 타입을 정확히 모르는다는 사실을 표현 (리스트 타입이 mutablelist<*>라는 말은 그 리스트가 string과 같은 구체적인 타입의 원소를 저장하기 위해 만들어진 것이라는 뜻 → 타입이 mutablelist<*>인 리스트를 만들 수는 없음. )→ 리스트의 원소 타입이 어떤 타입인지 모른다고해서 그 안에 아무 원소나 담아도 된다는 뜻은 아님( 코틀린에서는 Any? 는 모든 타입의 상위 타입)
        - 스타 프로젝션을 사용할 때는 값을 만들어내는 메소드만 호출할 수 있고, 그 값의 타입에는 신경을 쓰지 말아야함.

- **SOLID**

  SOLID 원칙은 객체지향 프로그램에서 지키면 좋은 5가지 원칙을 의미한다

  해당 원칙을 지킨다면 새로운 요구사항이 나오더라도, 큰 문제 없이 이를 해결할 수 있다.

    1. S(SRP, 단일 책임 원칙)
        - 하나의 클래스가 하나의 책임만 가져야 한다
    2. O(OCP, 개방 폐쇄 원칙)
        - 확장에는 열려있고 수정에는 닫혀 있다
        - 이로 인해 기존의 코드를 고치지 않고도 새로운 기능을 추가하거나 변경사항을 반영할 수 있다
    3. L(LSP, 리스코프 치환 원칙)
        - 자식 타입은 언제나 부모 타입으로 교체할 수 있다
        - 다형성을 이용할 때 사용하는 개념이다
    4. I(ISP, 인터페이스 분리 원칙)
        - 인터페이스 역시 하나의 책임을 가지고 있어야 한다
        - 인터페이스는 클라이언트의 목적과 용도에 적합한 인터페이스만을 제공해야 한다
    5. D(DIP, 의존 역전 원칙)
        - 구체척인 것에 의존하는 것이 아니라 추상적인것(인터페이스)에 의존하자



- **DI**

  Dependency Injection 즉, 의존 관계 주입을 의미한다

  필요한 의존 관계를 직접 생성하는것이 아니라, 외부에서 주입을 받는것을 의미한다

  효과

    - 유지보수성 향상
        - 코드를 바꾸지 않고 주입하는 객체만 바꾸어서 다른 동작을 유도할 수 있다
    - 결합도를 낮출 수 있다
        - 실행 시점에 어떤 구현체를 사용할건지 선택이 된다

  의존관계

    - 정적 의존 관계
        - 코드에서 나타나는 클래스간 의존 관계
        - 컴파일 당시에 정해진다
        - 정확히 어떤 구현체를 사용하는지는 알 수 없다
    - 동적 의존 관계
        - 실행 시점에 나타나는 의존관계
        - 런타임에 정해진다

  → DI 를 하게 되면 정적인 의존 관계는 바꾸지 않으면서 동적인 의존관계는 외부에서 결정할 수 있도록 할 수 있다




- **IoC**

  스프링에서는 개발자가 스프링 프레임워크 안에서 코드를 작성하고 이를 실행하면 해당 코드의 흐름을 개발자가 아닌 스프링이 가져가게 된다

  → 이처럼 프로그램의 흐름을 개발자가 직접 하는것이 아닌 외부에서 나타나는 것을 제어의 역전(IOC) 라고 한다

  스프링에서 객체를 생성하고 DI 컨테이너를 관리하는 일을 개발자가 직접하기 보다 스프링이 알아서 한다

  → IOC의 예시



- **생성자 주입 vs 수정자, 필드 주입 차이**

    - 생성자 주입
        - 주로 롬복의 @RequiredArgsConstructor로 쓰인다
        - 객체가 생성되는 순간 딱 1번 이 생성자가 호출되기 때문에 불변이고 필수적인 의존관계에 사용이 된다
    - 수정자 주입
        - setter이라는 수정자 메소드를 활용한다
        - 생성자 주입과 다르게 변경이 될수 있는 의존성을 주입할 때 사용한다
    - 필드 주입
        - 가장 간단한 방식
        - 테스트 하기가 어렵다
            - 테스트에는 단위 테스트와 통합 테스트가 있다
                - 단위 테스트는 각 기능 별로 테스트를 하는것을 의미한다. 대부분 순수 자바 로직을 사용한다
                - 통합 테스트는 스프링, DB 등등이 같이 돌아가는 테스트를 의미한다
                - 필드 주입을 선택하게 되면 Mock 객체를 주입하기 어려워 단위 테스트에서 사용하기에 어렵다

  → 다양한 방식으로 의존성을 주입할 수 있다



  의존성을 주입할 때 대상 빈이 2개 이상일 경우 어떻게 해결할 수 있을까?

    1. @Autowired 필드명 매칭

       Autowired는 우선 타입 매칭을 시도한다. 이때 여러 빈이 조회가 된다면 필드 이름, 파라미터 이름으로 추가적인 매칭을 진행한다

    2. @Primary 사용

       Autowired를 할 때 @Primary 라고 적혀 있는 빈이 우선권을 가지는 방식이다

    3. @Qualifier 사용

       추가적으로 구분할 수 있는 조건을 붙여주는 방식이다



- **AOP**

  프로그램의 핵심 로직과 공통 관심사를 분리해서 관리하는 기법

  → 비즈니스 로직은 핵심 기능을 구현하고, 공통된 기능은 따로 분리하자

  효과

    - 중복 코드 제거/유지보수성 향상
        - 공통기능을 함께 관리한다
    - 관심사 분리
        - 핵심 기능과 공통기능을 나누어서 관리한다

  스프링 AOP 적용 방식

    - 보통 실제 존재하는 객체 앞에 가짜 객체를 두고 여러 기능을 만들어둔다

  주요 적용 예시

    - 트랜잭션 관리
    - 공통 로깅
    - 예외 처리
    - 보안 처리…




- **서블릿**

  클라이언트의 요청을 처리하는 서버측 프로그램

  브라우저→ http 요청 → 서블릿 → 처리 후 응답(HTML/JSON 등)

  HttpServletRequest

    - 서블릿은 HTTP 요청 메세지를 쉽게 사용할 수 있도록 이를 파싱해주고 그  결과를 HttpServletRequest를 통해 사용할 수 있다
    - HTTP 메시지에 나온 메서드, url, uri, 프로토콜, 헤더 정보 등등을 쉽게 가져올 수 있다

  클라이언트로 부터 데이터 받기

    - 쿼리 파라미터
        - url의 쿼리 파라미터를 활용하는 방식
        - `request.getParameter("username")` 과 같이 getParameter() 메소드로 조회할 수 있다
        - 만일 이름이 같은 파라미터가 여러개라면 getParameterValues()를 활용해 조회할 수 있다
    - HTML FORM
        - form을 사용하는 경우 메시지 바디에 쿼리 파라미터와 동일한 형식으로 데이터가 전달된다
        - 서버는 위에서 설명한 쿼리 파라미터와 동일한 형식으로 데이터를 사용하면된다
    - 메시지 바디
        - json
            - json 형식을 파싱하기 위해서 개발자가 직접 객체를 생성할 수 있다
            - 또는 Jackson 라이브러리를 활용할 수 있다

  HttpServletResponse

    - HTTP 응답 메시지를 생성할 때 사용한다
    - 이를 통해 content, 쿠키, 리다이렉팅 등등 여러 정보를 메시지에 쉽게 생성할 수 있다
- 자바의 Optional 클래스

  이는 자바8부터 나온 기능으로 null을 안전하게 다루기 위해(NPE를 줄이기 위해) 등장했다

  Optional은 값이 존재할수도 하지 않을수도 있다는것을 표현한다

  기본 사용법

    jsx
    //값 생성하기
    Optional<String> op1 = Optional.of("hello");
    
    //값 꺼내기 
    System.out.println(op1.get()); //값이 없으면 NoSuchElementException
    System.out.println(op1.orElse("default")); // 값이 없으면 "default"
    System.out.println(op1.orElseThrow(() -> new RuntimeException("없음!")));
    
    //자주 사용하는 메소드
    op1.isPresent() //값이 있으면 true
    op1.isEmpty()  // 값이 없으면 true
    



- Stream API

  컬렉션이나 배열 같은 데이터를 선언적 방식으로 다룰 수 있게 해준다

    - 이를 통해 데이터를 순차적으로 처리할 수 있고 원본데이터는 유지한채 새로운 결과를 만들어낼 수 있다

  자주 사용하는 연산

    - filter() : 데이터를 필터링한다
    - map() : 데이터의 형식을 변환
    - sorted() : 정렬
    - distinct() : 중복 제거
    - limit() : 앞에서 n개만 가져옴
    - forEach() : 요소들을 반복처리한다
    - collect() : 특정 자료형으로 모은다
    - count() : 개수 세기

    ```jsx
    public class StreamExample {
        public static void main(String[] args) {
            List<String> colors = Arrays.asList("red", "blue", "white", "blac");
    
            
            List<String> result = colors.stream()
                                       .map(String::toUpperCase)
                                       .collect(Collectors.toList());
                                       
    
            System.out.println(result); // [RED, BLUE, WHITE, BLACK]
        
        
    		    List<Integer> nums = List.of(1, 2, 3, 4, 5);
    
            nums.stream()
                    .filter(n -> n % 2 == 0)
                    .forEach(System.out::println); 
            // 출력: 2
            //      4
    
            nums.stream()
                    .sorted()
                    .forEach(System.out::println); 
            // 출력: 1 2 3 4 5 (오름차순)
    
            nums.stream()
                    .sorted((a, b) -> b.compareTo(a))
                    .forEach(System.out::println); 
            // 출력: 5 4 3 2 1 (내림차순)
        
        }
    }
    

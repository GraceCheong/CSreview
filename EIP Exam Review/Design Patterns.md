# Design Pattern 오답노트 

## GoF Design Pattern 
---

### Creational Pattern 
    객체 생성(인스턴스화) 패턴 
    특정 개체가 생성되거나 변경되어도 프로그램 구조에 영향을 크게 받지 않도록 유연성을 제공
    추상 팩토리, 빌더, 팩토리 메서드, 프로토타입, 싱글턴 등이 있다. 

1. 추상 팩토리 
: 다양한 구성 요소 별로 '객체의 집합을 생성해야 할 때 유용하다. 
    ex) Button Factory based on OS 

2. 빌더
: 인스턴스 생성 시 생성자만을 통해서 생성하는 것이 아닌 다양한 방법을 고안 

    - 점증적 생성자 패턴(telescoping construtor pattern) : 클래스 내에 오버로딩을 통해 생성자를 여러 개 작성하는 것

    - 자바 빈 패턴(java Bean pattern)

            Student student = new Student();
            student.setId(123);
            student.setName("hong");
            student.setAge(20);

- 빌더 패턴 :  
    - 점층적 생성자 패턴 + 빈 패턴 

    
            Student student = new Student.Builder(123, "hong")
                                    .major("CS")
                                    .age(20)
                                    .build()


3. 팩토리 메서드 Factory method pattern : 상위 클래스에서 객체를 생성하는 인터페이스를 정의하고, 하위클래스에서 인스턴스 생성하도록 하는 방식 
    장점 : 클래스간 결합도를 낮춰 보다 효율적인 코드 제어가 가능 

4. 프로토 타입 Prototype pattern : prototype 을 먼저 생성하고 인스턴스를 복제하여 사용하는 구조 

5. 싱글턴 : 인스턴스를 하나만 만들어 사용하기 위한 패턴, 생성자의 호출이 반복적으로 이뤄져도 실제로 생성되는 최초 생성된 객체 반환 

        public class ExampleClass {
            //Instance
            private static ExampleClass instance = new ExampleClass();
            // 스태틱으로 선언하는게 중요한 것 같음 

            //private construct
            private ExampleClass() {}

            public static ExampleClass getInstance() {
                return instance;
            }
        }



    - 추가 정리 패턴

    - bridge pattern : 구현부에서 추상층을 분리하여 각자 독립적으로 확장이 가능하게 하는 패턴 
        - structural patterns
    - mediator pattern : 객체간의 통제와 지시의 역할을 하는 중재자를 두어 객체 지향의 목표를 달성하게 해준다. 
        - behavioral patterns 

    - adapter pattern : 호환성이 없는 인터페이스 때문에 함께 동작할 수 없는 클래스들이 함께 작동하도록 해주는 패턴 
        - 특징 : 
            1. 관계가 없는 인터페이스 간 같이 사용 가능 
            2. 프로그램 검사 용이 
            3. 클래스 재활용성 
        - 샘플 코드: 
            public interface Plugin {
                public void connect();
                public void disconnect();
            }

            public class Plugin110V implements Plugin {
                @Override
                public void connect() {
                    System.out.println("110V connect");
                }
                @Override
                public void disconnect() {
                    System.out.println("110V disconnect");
                }
            }
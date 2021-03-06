## JVM에 대해서 설명해주세요

Java Virtual Machine, JVM의 역할은 가상의 운영체제로서 바이트 코드를 해석하고 실행하는 것입니다.  
JVM의 가장 핵심적인 개념은 Java와 OS 사이에서 중개자 역할을 수행하여, Java가 OS에 구애받지 않고 코드를 재사용할 수 있게 해줍니다.  
그리고 또 한 가지, 절대 빼놓을 수 없는 중요한 역할이 있는데, 바로 Garbage Collection입니다.  
JVM은 메모리를 효율적으로 관리하기 위해서 GC를 통해, 사용하지 않는 객체를 메모리에서 자동으로 해제시켜줍니다.

Java 프로그램의 실행 과정을 간단하게 살펴보자면, 우선 개발자가 확장자 명이 `.java`인 Java 소스 코드를 작성하면, Java 컴파일러인 javac가 해당 소스 코드를 읽어들여서, 확장자 명이 `.class`인 바이트 코드로 변환시킵니다.  
이렇게 생성된 바이트 코드 파일은 JVM 구동 명령어인 `java.exe`에 의해 해석되며, 해당 운영체제에 맞는 기계어로 번역되고, 실행되는 것입니다.

그런데 사실, "Write once, run anywhere", 즉, 코드를 한 번 작성하면 어디에서든 구동이 가능하다는 메시지 자체는 참 매력적이지만, 한 번의 컴파일로 실행 가능한 기계어가 바로 만들어지는 것이 아니고 반드시 JVM을 거쳐야만 하기 때문에 C나 C++에 비해서 느립니다.  
하지만 이 또한 기계어로 빠르게 변환해주는 JVM 내부의 최적화된 JIT 컴파일러를 통해서 속도의 격차는 현저하게 줄어들고 있습니다.

※ Code States 기술 면접 문제 리스트에도 있는 질문이지만, 너무나도 중요하여 다시 한 번 정리하였음

- Reference 1 : [자바가상머신, JVM이란 무엇인가?](https://asfirstalways.tistory.com/158)
- Reference 2 : ["JVM이란 무엇인가" 자바 가상 머신 이해하기](https://www.itworld.co.kr/news/110837)

<br>

## OOP에 대해서 설명해주세요

객체 지향 프로그래밍은 현실 세계에서 어떤 제품을 만들 때, 부품을 먼저 개발하고 이 부품들을 하나씩 조립해서 완성된 하나의 제품을 만들어 내듯이, 소프트웨어를 개발할 때에도 부품에 해당하는 객체들을 먼저 만들고, 이것들을 하나씩 조립해서 완성해 나가는 프로그래밍 기법입니다.  
OOP의 대표적인 특징으로는 객체의 필드와 메소드를 하나로 묶고 실제 구현 내용은 감추어주는 **캡슐화** ,  
상위 객체가 자신이 갖고 있는 필드와 메소드를 하위 객체에게 물려주어, 하위 객체가 사용할 수 있도록 해주는 **상속** ,  
하나의 타입에 여러 객체를 대입할 수 있게 함으로써 다양한 기능을 이용할 수 있게 해주는 **다형성** 이 있습니다.

<br>

## SOLID 원칙에 대해서 설명해주세요

'클린 코드'로 유명하신 로버트 마틴이 정의한 좋은 객체지향 설계의 5가지 원칙은 SRP, OCP, LSP, ISP, DIP로 이루어져 있습니다.

우선 맨 앞의 SRP, Single Responsibility Principle은 한 클래스에 하나의 책임만 따른다는 원칙입니다.

그리고 OCP, Open/Closed Principle은 소프트웨어 요소가 확장에는 열려 있지만 변경에는 닫혀 있어야 한다는 원칙입니다.  
이는 요구사항의 변경이나 추가사항이 발생하더라도 기존 구성요소를 수정하기보다는 확장해서 재사용 가능하도록 설계해야 한다는 뜻입니다.

그 다음으로 LSP, Liskov Substitution Principle은 프로그램의 객체는 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바뀔 수 있어야 한다는 원칙입니다.  
좀 더 쉽게 표현하자면 인터페이스의 이름에 맞도록 기능을 넣어야 한다는 뜻입니다.

그리고 ISP, Interface Segregation Principle은 클래스 내에 사용하지 않는 인터페이스를 구현하지 말아야 한다는 원칙입니다.  
이는 '하나의 일반적이고 통합적인 인터페이스보다는 여러 개의 구체적인 인터페이스가 더 낫다'는 말과도 일맥상통합니다.

마지막으로 DIP, Dependency Inversion Principle은 "추상화에 의존해야지 구체화에 의존하면 안된다"는 의미를 내포하고 있습니다.  
쉽게 말해서 구현 클래스에 의존하지 말고, 인터페이스, 즉, 역할에 의존하라는 뜻입니다.

<br>

## Object Pooling이 뭔가요?

Object Pooling은 많은 수의 오브젝트가 생성되는 것을 방지하기 위해서 Pool에 Object들을 담아두고 사용 및 반납하는 방식입니다.  
만약 이런 시스템을 사용하지 않는다면 필요할 때마다 새로운 인스턴스를 만들어야 하기 때문에 자칫 사용하지 않는 인스턴스들이 지나치게 많아질 수 있다는 우려가 있습니다.  
Object Pooling은 이러한 것들을 방지해주고, 객체를 효율적으로 사용 및 반납할 수 있도록 해줍니다.

<br>

## static의 위험성에 대해 아시나요?

static은 클래스 로딩 시에 메모리 공간이 할당되고 이것이 프로그램 종료까지 이어집니다.  
이러한 static은 여러 동작에서 공통적으로 사용되는 경우 사용하게 되는데,  
객체 생성을 따로 할 필요 없이 바로바로 사용한다는 이점은 있지만  
자칫 메모리를 지나치게 낭비할 수 있게 되는 위험 요소가 있으며, 객체 지향의 캡슐화 원칙에도 위배됩니다.

<br>

## 오버라이드와 오버로딩에 대해 설명해주세요

우선 오버라이드는, 어떤 클래스가 부모 클래스를 상속받았다고 했을 때,  
이 부모 클래스의 메소드가 자식 메소드에서 사용하기에 적합하지 않을 수 있기 때문에,  
상속된 메소드 중 이렇게 적합하지 않는 메소드들을 재정의하기 위한 용도로 사용됩니다.  
오버라이드를 사용할 때는 부모 클래스의 메소드와 동일한 이름과 리턴 타입, 매개 변수들을 사용해야 하며,  
@Override 어노테이션을 달아서 사용할 수 있습니다.  
사실, @Override 어노테이션은 생략이 가능하지만 이 어노테이션을 명시해줄 경우  
컴파일러가 정확히 오버라이딩 된 것인지를 체크해주기 때문에 실수를 줄여줄 수 있습니다.

그리고 오버로딩은 같은 클래스 안에서 동일한 메소드 이름을 사용했을 때에도,  
매개 변수의 갯수나 타입에 따라 메소드를 달리 사용할 수 있도록 해주는 기능입니다.  
단, 리턴 타입만 다르다면 오버로딩을 할 수 없습니다.  
보통의 경우 함수 한 개가 한 가지의 기능을 담당하는 것이 보통이지만,  
Java에서는 이렇게 매개 변수의 차이에 따라 하나의 함수를 다양하게 활용할 수 있기 때문에  
'과적한다'는 의미의 오버로딩이라는 용어가 붙게 되었습니다.

<br>

## 어노테이션의 작동 방식에 대해서 설명해주세요

자바에서 어노테이션은 코드 사이 주석처럼 쓰이면서 특별한 의미를 갖고,  
특정 기능을 수행하도록 하는 기술입니다.  
즉 프로그램에 추가적인 정보를 제공해주는 메타 데이터라고 볼 수 있습니다.  
그리고 크게 3가지 역할을 해줍니다.  
우선 코드 작성 시 컴파일러에게 문법 에러를 체크할 수 있도록 정보를 제공해주고,  
개발툴이 빌드나 배치할 때 어노테이션의 코드를 자동으로 적용시킬 수 있도록 정보를 제공해주며,  
코드 실행 중 Reflection을 이용해서 추가 정보를 획득하여 기능을 실행하도록 해줍니다.

<br>

## Generic 타입을 사용하는 이유가 뭔가요?

제네릭 타입을 사용하면 잘못된 타입이 사용될 경우, 컴파일 과정에서 해결할 수 있기 때문입니다.  
자바 컴파일러는 타입의 잘못된 사용을 방지하기 위해 제네릭 타입에 대해 강한 타입 체크를 하기 때문에  
에러를 컴파일 단계에서 잡아낼 수 있어집니다.  
이러한 제네릭 타입은 컬렉션, 람다식, 스트림, NIO 등에서 널리 사용되고 있습니다.

<br>

## 추상 클래스와 인터페이스의 차이가 뭔가요?

일단 둘의 공통점은 상속 받는 클래스가 자신의 추상 메소드들을 구현하도록 강제한다는 것입니다.  
하지만 추상 클래스의 목적은 상속해서 기능을 이용하고 확장시키는 데에 있으며,  
인터페이스는 함수의 껍데기만 있기 때문에 구현을 강제하도록 하는 데에 의의가 있습니다.  
그리고 또 한 가지 중요하게 살펴봐야 할 개념은, 자바가 다중 상속을 지원하지 않는다는 점입니다.  
만약 자식 클래스가 2개 이상의 부모 클래스를 상속 받는데,  
부모 클래스들이 이름이 똑같은 메소드를 가지고 있다고 한다면 구현이 모호해지기 때문에,  
자바에서는 다중 상속을 하지 못하도록 해두었습니다.  
반면에 인터페이스는 구현을 강제하기 때문에 오히려 한 클래스에서 여러 인터페이스를 상속받을 수 있습니다.  
따라서 인터페이스는 메소드의 명세만 가지고 다양하게 활용할 수 있다는 점에서  
다형성을 충실히 따르는 기능을 한다고 생각합니다.

※ Reference : [자바의 추상 클래스와 인터페이스](https://brunch.co.kr/@kd4/6)

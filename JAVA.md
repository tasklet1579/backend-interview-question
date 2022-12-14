Java

<details>
<summary>✍️ 1. 객체지향 프로그래밍의 5가지 설계 원칙이 무엇인지 설명해주세요.</summary>
<br>

***단일 책임의 원칙 (SRP, Single Responsibility Principle)***

- 하나의 클래스는 한가지 책임을 가져야 하고 같은 이유로 변경될 코드는 모으지만 다른 이유로 변경될 코드는 배제합니다.
- 하나의 액터(역할)에 대해서만 책임을 갖는다면 변경을 특정할 수 있으므로 변경해야 하는 이유와 시점이 명확해집니다.
- 단일 책임의 원칙을 적용하면 응집도는 높이고 결합도는 낮출 수 있습니다.
- 뿐만 아니라 책임을 적절하게 분배함으로써 코드의 가독성 향상, 유지보수 용이라는 이점까지 얻을 수 있습니다.

***개방 폐쇄 원칙 (OCP, Open-Closed Principle)***

- 요구사항의 변경이나 추가사항이 발생하더라도 기존의 구성요소는 수정이 일어나지 않아야하며 쉽게 확장이 가능하여 재사용할 수 있어야 합니다.
- 개방 폐쇄 원칙을 지키기 위해서는 추상화에 의존해야 하는데 추상화란 핵심적인 부분만 남기고 불필요한 부분을 제거함으로써 복잡한 것을 간단히 하는 것입니다.
- 추상화를 통해 변하지 않는 부분만 남김으로써 기능을 구체화하고 확장할 수 있으며 변경이 필요한 경우에는 생략된 부분을 수정하여 원칙을 지킬 수 있습니다.
    - ex) 변하지 않는 것은 사용자를 추가할 때 암호화가 필요하다는 것이고 변하는 것은 사용되는 구체적인 암호화 정책입니다.

***인터페이스 분리 원칙 (ISP, Interface Segregation Principle)***

- 클라이언트가 필요하지 않는 것들을 의존하지 않도록 인터페이스를 작게 유지해야 합니다.
- 충분히 높은 응집도를 가진 클래스라도 목적과 관심이 다른 클라이언트가 있다면 인터페이스를 통해 적절히 분리할 필요가 있습니다.
- 인터페이스 분리 원칙을 적용하면 클라이언트는 자신이 사용하지 않는 메서드에 생긴 변화에 영향을 받지 않게 됩니다.

***리스코프 치환 원칙 (LSP, Liskov Substitution Principle)***

- 하위 클래스는 상위 클래스를 대체할 수 있어야 하며 하위 클래스가 변경되어도 상위 클래스에서 정의한 기능이 정상적으로 동작해야 합니다.
- 리스코프 치환 원칙을 지키기 위해서는 상위 클래스의 메서드를 의도와 다르게 오버라이딩 하지 않는 것이 중요합니다.

***의존 역전 원칙 (DIP, Dependency Inversion Principle)***

- 상위 모듈은 하위 모듈의 구현에 의존해서는 안 되며 하위 모듈은 상위 모듈에서 정의한 추상 타입에 의존해야 합니다.
- 상위 모듈은 변경이 없는 추상화된 클래스 또는 인터페이스를 의미하며 하위 모듈은 변화기 쉬운 구현 클래스를 의미합니다.
- 상위 모듈에 인터페이스가 위치하게 되고 하위 모듈이 그것을 구현하는 형태가 되는데 상위 모듈은 어떤 변경에도 영향을 받지 않게 됩니다.
- 결국 의존 역전 원칙의 핵심은 추상화에 의존하자이며 모든 관계를 구현 클래스가 아닌 추상 클래스나 인터페이스와 맺도록 하는 것입니다.

</details>

<details>
<summary>✍️ 2. 객체, 클래스, 인스턴스가 무엇인지 설명해주세요.</summary>
<br>

객체는 소프트웨어 세계에 구현할 대상이고 이를 구현하기 위한 설계도가 클래스이며 이 설계도에 따라 소프트웨어 세계에 구현된 실체가 인스턴스입니다.

객체는 현실의 대상과 비슷하며 상태나 행동 등을 가지지만 소프트웨어 관점에서는 개념일 뿐입니다.

소프트웨어에서 객체를 구현하기 위해서는 개념 이상으로 많은 것들을 생각하고 구현해야 하므로 이를 위한 설계도로 클래스를 작성합니다.

클래스를 바탕으로 객체를 소프트웨어에 실체화하면 그것이 인스턴스가 되고 이 과정을 인스턴스화라고 합니다. 실체화된 인스턴스는 메모리에 할당됩니다.

</details>

<details>
<summary>✍️ 3. Boxing과 Unboxing이 무엇인지 설명해주세요.</summary>
<br>

자바는 기본 타입 (byte, char, short, int, long, float, double, boolean)의 값을 갖는 객체를 생성할 수 있다.

이러한 객체를 Wrapper 객체라고 하는데, 기본 타입의 값을 내부에 두고 포장하기 때문이다.

기본 타입의 값은 변경할 수 없고 변경하고 싶다면 새로운 Wrapper 객체를 생성해야 한다.

Wrapper 클래스는 java.lang 패키지에 포함되어 있는데, 다음과 같이 기본 타입에 대응되는 클래스들이 있다.

|기본 타입|Wrapper 클래스|
|---|---|
|byte|Byte|
|char|Character|
|short|Short|
|int|Integer|
|long|Long|
|float|Float|
|double|Double|
|boolean|Boolean|

기본 타입의 값을 Wrapper 객체로 만드는 과정을 Boxing이라고 하고, Wrapper 객체에서 기본 타입의 값을 얻어내는 과정을 Unboxing이라고 한다.

기본 타입의 값을 직접 Boxing, Unboxing하지 않아도 자동으로 일어나는 경우가 있는데 자동 Boxing은 기본 값이 대입될 경우에 발생하고 힙 영역에 Wrapper 객체가 생성된다.

자동 Unboxing은 기본 타입에 Wrapper 객체가 대입될 경우에 발생하고 Java 1.5부터 추가된 기능이기 때문에 1.4 이전 버전에서는 직접 Boxing과 Unboxing을 해주어야 한다.

Wrapper 객체는 내부의 값을 비교하기 위해 ==와 != 연산자를 사용할 수 없다. 이 연산자는 내부의 값을 비교하는 것이 아니라 Wrapper 객체의 참조를 비교하기 때문이다.

내부의 값만 비교하려면 Unboxing한 값을 얻어 비교해야는데 ==와 != 연산자로 내부의 값을 비교할 수 있는 값이 있다.

|타입|값의 범위|
|---|---|
|boolean|true, false|
|char|\u0000 ~ \u007f|
|byte, short, int|-128 ~ 127|

</details>

<details>
<summary>✍️ 4. IntegerCache 클래스가 무엇인지 설명해주세요.</summary>
<br>

```
package java.lang;

public final class Integer extends Number implements Comparable<Integer> {
    ...
  
    private static class IntegerCache {
        static final int low = -128;
        static final int high;
        static final Integer cache[];
  
        static {
            // high value may be configured by property
            int h = 127;
            String integerCacheHighPropValue =
                sun.misc.VM.getSavedProperty("java.lang.Integer.IntegerCache.high");
            if (integerCacheHighPropValue != null) {
                try {
                    int i = parseInt(integerCacheHighPropValue);
                    i = Math.max(i, 127);
                    // Maximum array size is Integer.MAX_VALUE
                    h = Math.min(i, Integer.MAX_VALUE - (-low) -1);
                } catch( NumberFormatException nfe) {
                    // If the property cannot be parsed into an int, ignore it.
                }
            }
            high = h;
  
            cache = new Integer[(high - low) + 1];
            int j = low;
            for(int k = 0; k < cache.length; k++)
                cache[k] = new Integer(j++);
  
            // range [-128, 127] must be interned (JLS7 5.1.7)
            assert IntegerCache.high >= 127;
        }
  
        private IntegerCache() {}
    }
    
    public static Integer valueOf(int i) {
        if (i >= IntegerCache.low && i <= IntegerCache.high)
            return IntegerCache.cache[i + (-IntegerCache.low)];
        return new Integer(i);
    }
    
    private final int value;
    
    public Integer(int value) {
        this.value = value;
    }
    
    ...
}
```

Integer 클래스 내부에는 primitive type인 int 변수와 IntegerCache 클래스가 존재한다.

IntegerCache에는 -128에서 127 사이의 값이 캐싱되어 있기 때문에 Integer 변수에 해당 범위의 값이 Auto Boxing되면 기존에 생성해둔 값을 반환한다.

그렇기 때문에 ==와 != 연산자로 내부의 값을 비교할 수 있고 128 이상의 값을 저장하기 위해서선 -XX:AutoBoxCacheMax=size 옵션을 사용하면 된다.

</details>

<details>
<summary>✍️ 5. JVM에 대해서 설명해주세요.</summary>
<br>

JVM은 자바 바이트코드를 실행할 수 있는 독립적인 런타임 환경을 제공한다.

OS로부터 메모리 공간을 할당받아 자체적으로 관리하며 스택 기반의 네트워크 전송 시에 사용하는 바이트 오더인 네트워크 바이트 오더를 사용한다. (네트워크 바이트 오더는 빅 엔디안)

JVM이 자바 애플리케이션을 실행하는 흐름은 다음과 같다.

1. 클래스 로더가 컴파일된 자바 바이트코드를 런타임 데이터 영역에 로드한다.
2. 바이트코드를 실행 엔진이 실행한다.
3. 실행 도중 더 이상 힙 영역에서 참조되지 않는 인스턴스들은 가비지 컬렉터가 정리한다.

***클래스 로더***

클래스 로더는 컴파일된 자바 바이트코드를 런타임 데이터 영역에 로드하는데 기본 클래스 로딩 방식은 지연 로딩이다.

main 메서드가 위치한 클래스를 로드하고 실행 엔진으로 바이트코드를 해석하며 필요할 때마다 각 클래스를 메모리에 로드하고 읽어들인다.

- 클래스 로더 종류
    - 부트스트랩 클래스 로더 : JVM을 기동할 때 생성되며, Object 클래스들을 비롯하여 자바 API들을 로드한다.
    - 익스텐션 클래스 로더 : 기본 자바 API를 제외한 확장 클래스들을 로드한다. 다양한 보안 확장 기능 등을 여기에서 로드한다.
    - 시스템 클래스 로더 : 기본 자바 API를 제외한 확장 클래스들을 로드한다. 사용자가 지정한 $CLASSPATH 내의 클래스들을 로드한다.
    - 사용자 정의 클래스 로더 : 애플리케이션 사용자가 직접 코드 상에서 생성해서 사용하는 클래스 로더이다.

클래스 로더가 로드되지 않은 클래스를 찾으면, 다음과 같은 과정을 거쳐 클래스를 로드하고 링크하고 초기화한다.

1. 로드 : 클래스를 파일에서 가져와서 JVM의 메모리에 로드한다.
2. 검증 : 읽어 들인 클래스가 자바 언어 명세 및 JVM 명세대로 잘 구성되어 있는지 검사한다.
3. 준비 : 클래스가 필요로 하는 메모리를 할당하고 필드, 메서드, 인터페이스들을 나타내는 데이터 구조를 준비한다.
4. 분석 : 클래스의 상수 풀 내 모든 심볼릭 레퍼런스를 다이렉트 레퍼런스로 변경한다.
5. 초기화 : 클래스 변수들을 적절한 값으로 초기화한다. static initializer들을 수행하고, static 필드들을 설정된 값으로 초기화한다.

***런타임 데이터 영역***

런타임 데이터 영역은 JVM이 OS 위에서 실행되면서 할당받은 메모리 영역이다.

런타임 데이터 영역은 6개의 영역으로 나눌 수 있고 PC 레지스터, JVM 스택, 네이티브 메서드 스택은 스레드마다 하나씩 생성되며 힙 영역, 메서드 영역, 런타임 상수 풀은 모든 스레드가 공유해서 사용한다.

- PC 레지스터 : 현재 실행되고 있는 명령어의 주소 값이 저장되는 공간이다. 현재 실행하고 있는 명령어의 실행이 끝나면 다음 명령어의 주소 값을 갱신한다.
- JVM 스택 : 메서드가 호출되고 실행되면서 사용되는 지역 변수, 중간 연산 결과값이 갱신되며 저장되는 영역이다. 메서드 호출 시점마다 스택 프레임이라는 하나의 단위가 생성되고, 해당 메서드가 종료되는 시점에
  파괴된다.
- 네이티브 메서드 스택 : 자바 외의 언어로 작성된 네이티브 코드 실행을 지원하기 위한 영역이다.
- 메서드 영역 : 실행 시점에 사용되는 런타임 상수 풀, 필드, 메서드, 생성자와 같은 데이터들이 위치하는 영역이다. 메모리 공간이 부족하면 OutOfMemoryError가 발생한다.
- 런타임 상수 풀 : 각 클래스와 인터페이스의 상수뿐만 아니라, 메서드와 필드에 대한 모든 레퍼런스까지 담고 있는 테이블이다. JVM은 런타임 상수 풀을 통해 해당 메서드나 필드의 실제 메모리상 주소를 찾아서
  참조한다.
- 힙 영역 : 인스턴스 또는 객체를 저장하는 공간으로 가비지 컬렉션 대상이다.

***실행 엔진***

클래스 로더를 통해 런타임 데이터 영역에 로드된 바이트코드는 실행 엔진에 의해 실행된다.

실행 엔진은 자바 바이트코드를 명령어 단위로 읽어서 실행한다. 바이트코드의 각 명령어는 1바이트짜리 OpCode와 추가 피연산자로 이루어져 있으며, 실행 엔진은 하나의 OpCode를 가져와서 피연산자와 함께 작업을
수행한다.

이 과정에서 실행 엔진은 바이트코드를 기계어로 변경하는데 두 가지 방식이 존재한다.

- 인터프리터 : 바이트코드 명령어를 하나씩 읽어서 해석하고 실행한다.
- JIT (Just-In-Time) : 바이트코드를 컴파일하여 이후에는 해당 메서드를 더 이상 인터프리팅하지 않는다. 코드는 캐시에 보관하기 때문에 한 번 컴파일된 코드는 계속 빠르게 수행되고 JVM은 내부적으로
  해당 메서드가 얼마나 자주 수행되는지 체크하고, 일정 정도를 넘을 때에만 컴파일을 수행한다.
    - 오라클은 내부적으로 프로파일링을 통해 가장 컴파일이 필요한 부분, 즉 핫스팟을 찾아낸 다음, 이 핫스팟을 네이티브 코드로 컴파일하고 한번 컴파일된 바이트코드라도 해당 메서드가 더 이상 자주 불리지 않는다면
      캐시에서 제거한다.
    - IBM은 한번 컴파일된 네이티브 코드를 공유 캐시를 통해 JVM이 사용하도록 한다. 이미 컴파일된 코드는 다른 JVM에서도 컴파일하지 않고 사용할 수 있게 하는 것이다.

</details>

<details>
<summary>✍️ 6. Garbage Collector에 대해서 설명해주세요.</summary>
<br>

가비지 컬렉터는 힙 영역에 있지만 현재는 참조되고 있지 않는 인스턴스들을 찾아서 제거하고 사용되지 않는 메모리 공간을 회수한다.

이는 다음의 두 과정을 거친다.

1. Mark : GC가 참조되지 않는 인스턴스들을 찾아서 mark한다.
2. Sweep : GC가 mark된 인스턴스들을 힙 영역으로부터 정리한다.

GC는 JVM에 의해 간격을 두고 자동으로 동작하는데 System.gc()를 통해 명시적으로 호출하는 방법도 있지만 이는 즉시 동작을 보장하진 않는다.

또한 JVM은 GC를 수행할 때, 이를 실행하는 쓰레드 이외에는 작업을 중단하게 되므로 명시적인 호출은 지양해야 한다.

**메모리 구성**

Metaspace

- 자바 8에서 PermGen이 사라지고 Metaspace가 이를 대체하게 되었는데 PermGen은 자바 7까지 클래스의 메타데이터를 저장하던 영역이었고 Heap의 일부였다.
    - Permanent Generation은 힙 영역 중에 하나로 자바 애플리케이션을 실행할때 클래스의 메타데이터를 저장하는 영역이다. (자바 7기준)
    - 아래와 같은 것들이 Java Heap이나 native heap 영역으로 이동했다.
        - Symbols -> native heap
        - Interned String -> Java Heap
        - Class statics -> Java Heap
    - OutOfMemoryError: PermGen Space error는 더이상 볼 수 없고 PermSize 와 MaxPermSize는 더이상 사용할 필요가 없다. 이 대신에 MetaspaceSize 및
      MaxMetaspaceSize가 새롭게 사용되게 되었다.

Heap - Old & Young (Eden, Survivor)

- Heap은 Young Generation, Old Generation으로 크게 두개의 영역으로 나뉘고 Young Generation은 Eden, Survivor Space 0, 1로 세분화 된다.

**가비지 컬렉션 프로세스**

1. 새로운 인스턴스는 Eden 영역에 할당된다.
2. Eden 영역이 가득차면, MinorGC가 발생한다.
3. MinorGC가 발생하면, Reachable 인스턴스들은 S0으로 옮겨지고 Unreachable 인스턴스들은 Eden 영역에서 제거된다.
4. 다음 MinorGC가 발생할때, Eden 영역에는 3번과 같은 과정이 발생한다. 기존에 S0에 있었던 인스턴스들은 S1으로 옮겨지는데 이때 age 값이 증가된다.
5. 다음 MinorGC가 발생하면, 4번 과정이 반복되는데, S1이 가득차 있으므로 인스턴스들은 S0으로 옮겨지면서 age 값이 증가된다.
6. Young Generation에서 계속해서 살아남으며 age 값이 특정값 이상이 되면 Old Generation으로 옮겨진다.
7. 6번 과정이 계속해서 반복되면서 Old Generation이 가득차게 되면 MajorGC 가 발생한다.

**가비지 컬렉터 종류**

Serial GC

- 자바 5, 6에서 사용되는 GC
    - MinorGC, MajorGC 모두 순차적으로 실행된다.
    - Mark-Compact collection method를 사용한다.
        - 새로운 메모리 할당을 빠르게 하기 위해서 기존의 메모리에 있던 인스턴스들을 힙의 시작위치로 옮겨 놓는 방법이다.

Parallel GC

- 자바 8에서 사용되는 GC
- Young Generation에 대한 GC 수행시 멀티스레드를 사용한다.
- 스레드 개수는 디폴트로 CPU 개수만큼이 할당되는데 옵션을 사용한다면 Old Generation의 GC에서도 멀티스레딩을 활용할 수 있다.

Concurrent Mark Sweep (CMS) Collector

- GC 작업을 애플리케이션 스레드와 동시에 수행함으로써 GC로 인한 stop-the-world 시간을 최소화 한다.
- Young Generation에 GC 수행시 Parallel GC와 같은 알고리즘을 사용하지만 압축 작업을 하지 않는다.
- 일반적으로 CMS 컬렉터는 살아있는 인스턴스들에 대한 압축작업을 수행하지 않으므로, 메모리의 파편화가 문제가 된다면 더 큰 힙 사이즈를 할당해야 한다.

G1 Garbage Collector

- 자바 7부터 사용 가능하며 자바 9에서 사용되는 GC
- 대용량 메모리 공간이 있는 멀티 프로세서 시스템에서 실행되는 응용 프로그램을 위해 만들어졌다.

</details>

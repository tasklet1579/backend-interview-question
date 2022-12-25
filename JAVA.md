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

Spring

<details>
<summary>✍️ 1. 데이터베이스 커넥션 풀에 대해서 설명해주세요.</summary>
<br>

데이터베이스 연결을 열고 닫는데 들어가는 비용과 시간을 줄이는 방법입니다.

데이터베이스에 연결하기 위해서는 드라이버를 로드하고 커넥션 객체를 생성해야는데 이때 많은 시스템 자원 소모와 시간이 발생합니다.

데이터베이스 사용을 완료하면 자원을 반납해야 하고 매번 요청할 때마다 이러한 작업을 반복하는 것은 매우 비효율적이기 때문에 커넥션 풀을 사용합니다.

커넥션 풀의 커넥션 개수가 적으면 쓰레드의 대기시간이 길어져 성능 저하가 발생하고 커넥션 개수가 증가하더라도 Disk 병목이나 컨텍스트 스위칭으로 인한 오버헤드가 발생하기 때문에 성능적인 한계가 존재합니다.

***커넥션 풀 설정***

|설정|설명|
|---|---|
|initialSize|초기 커넥션 개수 (default 10)|
|minIdle|최소한으로 유지할 커넥션 개수 (default 10)|
|maxIdle|최대한 유지할 수 있는 커넥션 개수 (default 100)|
|maxActive|동시에 사용할 수 있는 최대 커넥션 개수 (default 100)|
|maxWait|커넥션을 얻기 전 최대 대기 시간 (default 30s)|

maxActive는 initialSize 보다 크거나 같아야 합니다.

- 초기 커넥션 개수가 최대 커넥션 개수 보다 커서 논리적인 오류가 있는 설정입니다.

maxIdle과 maxActive는 동일하게 설정하는 것을 권장합니다.

- maxIdle = 5, maxActive = 10인 경우 커넥션을 5개 사용하고 있다고 가정합니다.
- 1개의 커넥션이 추가로 요청된다면 10개까지 사용 가능하므로 커넥션을 생성하고 사용이 완료되면 풀에 반환합니다.
- 이때 maxIdle이 5이므로 해당 커넥션은 close되는데 이러한 상황이 반복되면 불필요한 비용과 시간이 발생할 수 있습니다.

</details>

<details>
<summary>✍️ 2. Spring Container, IoC, DI는 무엇이고 어떠한 장점이 있을까요?</summary>
<br>

스프링 컨테이너는 설정 파일에 정의된 객체로부터 인스턴스를 생성하고 이들의 생명 주기를 관리합니다.

BeanDefinition에 의존하도록 설계되어 있기 때문에 애너테이션이나 자바 코드, XML을 선택적으로 사용할 수 있습니다.

스프링 컨테이너의 종류에는 BeanFactory와 ApplicationContext가 있습니다.

BeanFactory는 기본적인 컨테이너 기능만을 제공하며 클라이언트의 요청이 있을 때 인스턴스를 생성하는 지연 로딩 방식을 사용합니다.

ApplicationContext는 AOP와 같은 추가 기능을 제공하고 컨테이너가 구동될 때 모든 인스턴스를 생성하는 사전 로딩 방식을 사용합니다.

제어의 역전은 개발자가 직접 객체를 제어하는 것이 아닌 스프링 컨테이너에게 결정권이 넘어가는 것을 의미합니다.

스프링 컨테이너가 객체의 생성과 관계 설정, 사용, 소멸 등의 작업을 대신하기 때문에 개발자는 비즈니스 로직에 집중할 수 있습니다.

제어의 역전을 구현하는 방법으로는 의존성 검색과 의존성 주입이 있는데 의존성 검색은 컨테이너 종속성이 증가하므로 의존성 주입을 사용합니다.

의존성 주입은 두 객체 간의 관계를 결정하는 디자인 패턴으로 런타임에 동적으로 인스턴스를 주입하여 클래스 간의 결합도를 낮추고 직접 객체를 생성하는 것 보다 유지보수가 수월합니다.

</details>

<details>
<summary>✍️ 3. Bean 라이프 사이클에 대해 아는 만큼 설명해주세요.</summary>
<br>

두 가지 방식을 이용해서 Bean의 라이프 사이클을 관리할 수 있습니다.

- 스프링이 제공하는 특정 인터페이스를 상속받아 빈을 구현합니다.
- 스프링 설정에서 특정 메서드를 호출하라고 지정합니다.

***Bean 라이프 사이클 개요***

```
빈 객체 생성
↓
빈 프로퍼티 설정
↓
BeanNameAware.setBeanName()
↓
ApplicationContextAware.setApplicationContext()
↓
BeanPostProcess의 초기화 전 처리
↓ 
@PostConstruct 메서드
↓
InitializingBean.afterPropertiesSet()
↓
커스텀 init 메서드
↓
BeanPostProcessor의 초기화 후 처리
↓
빈 객체 사용
↓
@PreDestroy 메서드
↓
DisposableBean.destroy()
↓
커스텀 destroy 메서드
```

전체 흐름은 객체 생성/프로퍼티 설정 → 초기화 → 사용 → 소멸의 네 단계를 거치게 됩니다.

Bean의 초기화와 소멸 방법은 각각 세 가지가 존재하며 각 방식이 쌍을 이루어 함께 사용되곤 합니다. @PostConstruct 애너테이션을 사용해서 초기화 메서드를 지정했다면 @PreDestroy 애너테이션을
사용해서 소멸 메서드를 지정하고 커스텀 init 메서드를 사용했다면 커스텀 destroy 메서드를 사용하는 식입니다.

***InitializingBean 인터페이스와 DisposableBean 인터페이스***

- InitializingBean : Bean의 초기화 과정에서 실행될 메서들을 정의
- DisposableBean : Bean의 소멸 과정에서 실행될 메서들을 정의

```
public interface InitializingBean {
    void afterPropertiesSet() throws Exception;
}

public interface DisposableBean {
    void destroy throws Exception;
}
```

객체 생성 이외의 추가적인 초기화 과정이 필요하다면 InitializingBean 인터페이스를 상속받고 afterPropertiesSet() 메서드에서 초기화 작업을 수행하면 됩니다.

컨테이너가 종료될 때 객체에 알맞은 처리가 필요하다면 DisposableBean 인터페이스를 상속받아 destroy() 메서드에서 소멸 작업을 수행하면 됩니다.

초기화와 소멸 과정이 필요한 예가 데이터베이스 커넥션 풀 기능입니다. 커넥션 풀은 미리 커넥션을 생성해 두었다가 커넥션이 필요할 때 제공하는 기능이므로 초기화 과정을 필요로 합니다.

더 이상 커넥션이 필요 없으면 생성한 커넥션을 모두 닫기 위한 소멸 과정을 필요로 하고 이런 커넥션 풀 기능을 스프링 Bean으로 사용하고 싶은 경우 InitializingBean 인터페이스와
DisposableBean 인터페이스를 상속받아 초기화와 소멸 과정을 처리할 수 있습니다.

***@PostConstruct 애너테이션과 @PreDestroy 애너테이션***

모두 자바 표준 패키지의 애너테이션입니다.

InitializingBean 인터페이스와 DisposableBean 인터페이스는 스프링에 종속적이고 메서드의 이름을 변경할 수 없습니다.

외부 라이브러리에도 적용할 수 없기 때문에 @PostConstruct 애너테이션과 @PreDestroy 애너테이션 사용을 권장하고 있습니다.

하지만 외부 라이브러리에 적용하는 경우 코드 수정이 불가능해서 다른 방법을 찾아야 합니다.

***커스텀 init 메서드와 커스텀 destroy 메서드***

```
import org.springframework.context.annotation.Bean;

@SpringBootApplication
public class Application {
    @Bean(initMethod = "init", destroyMethod = "destroy")
    public ConnectionPool connectionPool() {
        return new ConnectionPool();
    }
    
    ...
}
```

@Bean 애너테이션에 initMethod와 destroyMethod를 설정하여 초기화와 소멸 과정을 처리할 수 있습니다.

메소드의 이름을 자유롭게 변경할 수 있으며 코드에 접근할 수 없는 외부 라이브러리에도 초기화와 종료 메서드를 적용할 수 있습니다.

또한 destroyMethod에는 inferred라는 추론 기능이 있는데 일반적으로 종료 메서드의 이름으로 close 또는 shutdown을 많이 이용하기 때문에 close 또는 shutdown 함수가 존재하면 이를
소멸 메서드로 인식하여 호출합니다. 이러한 추론 기능을 사용하고 싶지 않으면 destroyMethod="" 처럼 공백으로 지정하면 됩니다.

</details>

<details>
<summary>✍️ 4. Bean Scope와 종류에 대해 아는 만큼 설명해주세요.</summary>
<br>

스프링 Bean은 Scope를 갖는데 주요 범위에는 다음의 두 가지가 있습니다.

- 싱글톤
- 프로토타입

스프링은 별다른 설정이 없으면 싱글톤으로 생성되는데 특정 타입의 Bean을 하나만 만들어 두고 공유해서 사용하기 위함입니다.

그래서 Bean에 상태를 저장하는 코드를 작성하는 것은 동시성 문제를 유발하여 위험한 상황을 초래할 수 있고 필요에 따라서 프로토타입이 필요할 수도 있습니다.

프로토타입을 이용해서 일종의 팩토리(객체 생성 기능을 제공하는 객체)처럼 만들 수 있지만 그러한 경우에는 명시적으로 팩토리 클래스를 만들어서 사용하는 편이 더 좋습니다.

***싱글톤***

- 스프링에서 기본이 되는 Scope
- 스프링 컨테이너의 시작과 종료까지 1개의 객체만 유지
- 싱글톤이라는 것을 명시적으로 표현하고 싶다면 @Scope("singleton") 애너테이션 추가

***프로토타입***

- Bean의 초기화까지만 관리하고 컨테이너가 종료한다고 해서 소멸 과정이 실행되지 않음
- 클라이언트의 요청이 오면 항상 새로운 인스턴스를 생성하고 반환하고 이후에 관리하지 않음
- 프로토타입이라는 것을 명시적으로 표현하고 싶다면 @Scope("prototype") 애너테이션 추가

</details>

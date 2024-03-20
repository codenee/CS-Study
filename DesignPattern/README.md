# Design Pattern
- [Singleton](#singleton)

</br>

디자인 패턴은 용도에 따라 3가지로 나눌 수 있다. </br>
1. 생성 패턴 </br>
    : 싱글톤 패턴, 추상 팩토리, 팩토리 메소드 </br>
2. 행동 패턴 </br>
    : 옵저버, 전략, 템플릿 메소드, 반복자 </br>
3. 구조 패턴 </br>
    : 컴포지트, 프록시, 어댑터,  </br>

## Singleton
생성자가 여러차례 호출되어도 실제로 생성되는 객체는 하나이다. </br>
최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴한다.  </br>
클래스의 인스턴스가 딱 1개만 생성되는 것을 보장하는 디자인 패턴이다.  </br>
프로그램 시작부터 종료시까지 어떤 클래스의 인스턴스가 메모리 상에 단 하나만 존재할 수 있게 하고, 이 인스턴스에 대해 어디에서나 접근할 수 있도록 하는 패턴이다. </br>

- 사용하는 이유? 
우리가 만들었던 DI컨테이너에 요청을 할 때마다 새로운 객체를 생성한다.   </br>
요청이 많은 트래픽 사이트에서는 계속 객체를 생성하게 되면 메모리 낭비가 심해지기 때문이다.   </br>
- 스프링에서 사용하는 패턴
스프링 컨테이너는 싱글톤 패턴을 적용하지 않아도 객체 인스턴스를 싱글톤으로 관리한다.   </br>
이러한 기능 덕분에 싱글톤 패턴의 모든 단점을 해결하고 객체를 싱글톤으로 유지할 수 있다.   </br>
스프링에서 싱글톤 관련 코드를 작성하지 않아도 스프링 빈에서 객체를 1개 설정한다.   </br>
스프링 빈이 싱글톤 패턴으로 관리되는 빈이다.   </br>

### 구현
> 다양한 방법이 있는데 공통적으로 가지는 특징이 있다.   </br>

private생성자만을 정의해 외부 클래스로부터 인스턴스 생성을 차단한다.  </br>
싱글톤을 구현하고자 하는 클래스 내부에 멤버 변수로써 private static객체 변수를 만든다.   </br>
public static메소드를 통해 외부에서 싱글톤 인스턴스에 접근할 수 있도록 접점을 제공한다.   </br>

- Bill Pugh Singleton Implementation </br>
Inner Static Helper Class를 사용하는 방식으로 현재 가장 널리 사용되고 있는 싱글톤 패턴 구현 방법이다. </br>
```
public class Singleton {
    private Singleton(){}
    private static class SingletonHelper{
        private static final Singleton SINGLETON = new Singleton();
    }
    public static Singleton getInstance(){
        return SingletonHelper.SINGLETON;
    }
}
```
SingletonHelper클래스는 Inner Class로 선언되어 있기 때문에 Singleton클래스가 Class Loader에 의해 로딩될 때 로딩되지 않다가 getInstance()가 호출될 때 JVM메모리에 로드되고 객체를 생성하게 된다. </br>
또한 클래스가 로드될 때 객체가 생성되기 때문에 multi-thread환경에서도 안전하게 사용이 가능하다. </br>
하지만 이 방법도 Java의 Reflection을 사용하면 private 생성자, 메서드에 접근 가능해지면 단 하나의 객체라는 조건을 깨뜨린다. </br>

> 자세한 설명 </br> https://code-space.tistory.com/399








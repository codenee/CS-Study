# Part 2-2 JAVA
- [Part 2-2 JAVA](#part-2-2-JAVA)
    - [01. 자바의 신](https://github.com/codenee/CS-Study/tree/main/Language/Java/GodOfJava3rd)
    - [02. JVM](#JVM)
    - [03. Garbage Collection](#Garbage-Collection)
    - [04. String Class](#String-Class)

</br>

 [back](https://github.com/codenee/CS-Study)

</br>


# 언어
## Java
* Sun Microsystems에서 개발하여 1996년 1월에 공식적으로 발표한 객체지향 프로그래밍 언어입니다.
* 자바는 운영체제에 독립적이라는 특징이 있어 운영체제의 종류에 관계없이 실행이 가능합니다.
* 이는 JDK(Java Development Kit)라는 개발 도구가 있기에 가능합니다.

### 특징
#### 1. 운영체제에 독립적
* 자바가 운영체제에 독립적으로 사용할 수 있는 이유는 일종의 애뮬레이터인 JVM(Java Virtual Machine)을 통해서 가능합니다. 자바 응용 프로그램은 운영체제나 하드웨어가 아닌 JVM하고만 통신하고 JVM이 자바 응용프로그램으로부터 전달받은 명령을 해당 운영체제가 이해할 수 있도록 변환하여 전달합니다.
* 자바로 작성된 프로그램은 운영체제에 독립적이지만 JVM은 운영체제에 종속적이어서 Sun에서는 여러 운영체제에서 설치할 수 있는 JVM을 제공합니다.
* 자바 소스는 컴파일 후 바이트코드가 생성되며 JVM은 바이트코드를 해석해 운영체제에서 실행할 수 있도록 변역해 주는 역할을 담당합니다.
* Hello.java 작성 -> 컴파일(javac.exe) -> Byte Code(.class) -> 실행(java.exe) -> "Hello World" 출력
#### 2. 객체지향언어
* 객체지향개념의 특징인 상속, 캡슐화, 다형성이 잘 적용된 객체지향언어입니다.
* 숫자(int, float, long 등), 논리 값(true, false)를 제외한 모든 것이 객체로 구성되어 있습니다. 자바는 Object클래스에서 모든 클래스를 파생합니다.
* int, float, long, true, false등을 원시 자료형(Primitive type)이라고 합니다.
#### 3. 자동 메모리 관리(Garbage Collection)
* 자바로 작성된 프로그램이 실행되면, Garbage Collector가 자동으로 메모리를 관리해주기 때문에 프로그래머가 메모리를 따로 관리하지 않아도 됩니다.
* 이는 포인터 연산을 지원하지 않기 때문에 잘못된 주소를 가르킬 가능성이 없습니다. 모든 메모리 접근을 자바 시스템이 관리하고 제한하며 예외 핸들링을 하여 시스템 붕괴의 우려가 없습니다. 
#### 4. 네트워크와 분산처리 지원
* 다양한 네트워크 프로그래밍 라이브러리(JAVA API)를 통해 비교적 짧은 시간에 네트워크 관련 프로그램을 개발할 수 있도록 지원합니다.
#### 5. 멀티쓰레드 지원
* 자바에서 개발되는 멀티쓰레드 프로그램은 시스템과는 관계없이 구현이 가능하고, 관련된 JAVA API 라이브러리가 제공되어 구현이 쉽습니다. 여러 쓰레드에 대한 스케줄링을 자바 인터프리터가 담당하게 됩니다.
#### 6. 동적 로딩(Dynamic Loading)지원
* 자바로 작성된 애플리케이션은 여러 개의 클래스로 구성되어 있습니다.
* 자바는 동적 로딩을 지원하기 때문에 실행 시에 모든 클래스가 로딩되지 않고 필요한 시점에 클래스를 로딩하여 사용할 수 있다는 장점이 있습니다.
* 그 외에도 일부 클래스가 변경되어도 전체 애플리케이션을 다시 컴파일하지 않아도 되며, 애플리케이션의 변경사항이 발생해도 비교적 적은 작업만으로 처리할 수 있는 유연하게 애플리케이션을 작성할 수 있습니다.

### JAVA의 핵심 기술 패키지
#### JVM
* Java Virtual Machine으로, 자바 프로그램을 실행하는 자바 플랫폼 구성요소입니다.
* 자바로 작성된 애플리케이션은 모두 JVM에서만 실행되기 때문에, 자바 애플리케이션이 실행되기 위해서는 반드시 JVM이 필요합니다.
* Java 애플리케이션은 OS사이에 JVM이 있어, JVM을 한 번 더 거치게 됩니다.
* 하드웨어에 맞게 컴파일된 상태가 아닌 실행 시에 해석(interpret)되기 때문에 속도가 느리다는 단점을 가지고 있습니다.
* 하지만 바이트코드(컴파일된 자바코드)를 하드웨어의 기계어로 바로 변환해주는 JIT컴파일러와 향상된 최적화 기술이 적용되어 속도의 격차가 줄어졌습니다.
* Java 애플리케이션은 JVM하고만 상호작용하기 때문에 OS와 하드웨어에 독립적이라는 특징이 있지만, JVM은 OS에 종속적이기 때문에 OS에 맞는 JVM을 설치해야합니다.
#### JRE
* Java Runtime Environment로, 자바로 만들어진 프로그램을 실행시키는데 필요한 라이브러리들과 각종 API, JVM이 포함되어 있습니다.
* JVM을 생성하는 디스크 상의 부분입니다.
* JDK는 자바 기반 소프트웨어를 개발하기 위한 도구들로 이루어진 패키지인 반면, JRE는 자바 코드를 실행하기 위한 도구들로 구성된 패키지입니다. JRE는 자바로 개발(쓰기)은 안되고 실행(읽기)만 된다고 이해하면 됩니다.
#### JDK
* Java Development Kit로, 자바 애플리케이션을 구축하기 위한 핵심 플랫폼으로 자바를 개발하는데 필요한 프로그램들이 있습니다.
* 개발자들이 JVM과 JRE에 의해 실행되고 구동될 수 있는 자바 프로그램을 생성할 수 있게 해줍니다.
* 즉, 자바 기반 소프트웨어를 개발하기 위한 도구들로 이루어진 패키지입니다.
* 개발을 하려면 실행도 시켜줘야 하기 때문에 JRE도 함께 포함되어 있습니다.
#### JDK의 bin디렉토리에 있는 주요 실행 파일

|실행 파일|설명|
|---|---|
|javac.exe|자바 컴파일러, 자바소스 코드를 바이트코드로 컴파일한다.|
|java.exe|자바 인터프리터, 컴파일러가 생성한 바이트코드를 해석하고 실행한다|
|javap.exe|역어셈블러, 컴파일된 클래스 파일을 원래의 소스로 변환한다.|
|javadoc.exe|자동문서 생성기, 소스파일에 있는 주석을 이용하여 java api문서와 같은 형식의 문서를 자동으로 생성한다.|
|jar.exe|압축프로그램, 클래스파일과 프로그램의 실행에 관련된 파일을 하나의 jar로 압축하거나 압축해제한다.|

#### JVM 동작 방식
1. 자바 프로그램을 실행하면 JVM은 OS로 부터 메모리를 할당합니다.
2. 자바 컴파일러(Javac)가 자바 소스 코드(.java)를 자바 바이트 코드(.class)로 컴파일합니다.
3. Class Loader를 통해 JVM Runtime Data Area로 로딩합니다.
4. Runtime Data Area에 로딩 된 .class들은 Execution Engine을 통해 해석합니다.
5. 해석된 바이트 코드는 Runtime Data Area의 각 영역에 배치되어 수행하며 이 과정에서 Execution Engine에 의해 GC의 작동과 스레드 동기화가 이루어집니다.

#### JVM 구조
* Class Loader
   * 자바는 동적으로 클래스를 읽어옵니다. 프로그램이 실행 중인 런타임에서 모든 코드가 자바 가상 머신과 연결됩니다. 이렇게 동적으로 클래스를 로딩해주는 역할이 "클래스 로더"입니다.
   * 자바에서 소스를 작성하면 .java파일이 생성되고, .java소스를 컴파일러가 컴파일하면 .class파일이 생성되는데 클래스 로더는 .class파일을 묶어서 JVM이 운영체제로부터 할당받은 메모리 영역이 Runtime Data Area로 적재합니다.
* Execution Engine
  * 클래스 로더에 의해 JVM으로 로드된 .class파일(바이트 코드)들은 Runtime Data Area의 Method Area에 배치되는데, 배치된 이후에 JVM은 Method Area의 바이트 코드를 실행 엔진에 제공하여, 정의된 내용대로 바이트 코드를 실행시킵니다.
  * 이때, 로드된 바이트 코드를 실행하는 런타임 모듈이 실행 엔진입니다. 실행 엔진은 바이트 코드를 명령어 단위로 읽어서 실행합니다.
* Garbage Collector
  * 자바 가상 머신은 가비지 컬렉터를 이용하여 사용하지 않는 메모리를 자동으로 회수해줍니다. 개발자가 따로 메모리 관리를 하지 않아도록 자동으로 관리해줍니다. Heap 메모리 영역에 생성(적재)된 객체들 중 참조되지 않은 객체들을 탐색 후 제거하는 역할을 하며 해당 역할을 하는 시간은 정확이 언제인지는 알 수 없습니다. GC역할을 수행하는 스레드를 제외한 나머지 모든 스레드들은 일시정지 상태가 됩니다.
* Runtime Data Area
  * 런타임 데이터 영역은 JVM의 메모리 영역으로 자바 애플리케이션을 실행할 때 사용되는 데이터들을 적재하는 영역입니다.
  * 모든 스레드가 공유해서 사용 (GC의 대상)
    * Heap Area
    * Method Area
  * 스레드마다 하나씩 생성
    * Stack Area
    * PC Register
    * Native Method Stack
   
> 블로그 정리
>> https://code-space.tistory.com/338

</br>

[Up](#part-2-1-Language) / [back](https://github.com/codenee/CS-Study)


</br>


# Garbage Collection
* JVM내에서 메모리 관리를 해주는 것. </br>
쓰지 않는 객체(힙 메모리 객체가 null)인 경우 가비지 컬렉터의 대상이 된다. </br>
사용자가 동적으로 생성한 객체가 있는 영역인 Heap메모리에서 동작한다.
* C++에서는 Heap영역의 메모리를 사용하기 위해 동적 메모리 영역을 할당 받고 해제하는 과정을 개발자가 직접 해야한다 </br>
  (메모리를 수동으로 직접 관리) </br>
→ 메모리 영역을 할당 받고 해제하지 않으면 메모리 누수가 발생할 수 있고, 이미 해제한 메모리 영역을 또 해제하면 에러가 발생할 수 있다. </br>
→ Java에서는 동적 메모리 영역(힙 메모리)를 GC가 관리하여 에러 발생 요인을 방지할 수 있다. </br>
GC를 수행하게 되면 GC를 수행하는 스레드를 제외한 모든 스레드가 중지된다.</br>
→ 이것을 stop-the-world라고 한다. </br>

GC 튜닝은 stop-the-world시간을 줄이는 것을 의미한다. </br>
GC가 자주 호출되면 그 만큼 stop the world가 자주 발생하여 사용자 입장에서 느껴질 정도로 애플리케이션 동작이 지연될 수 있다.

Java플랫폼에서는 4가지의 가비지 컬렌션이 지원되는데, Serial GC( 직렬 GC)를 제외하고는 병렬화하여 성능을 향상시킨다.

가비지 컬렉션을 수행하는 오버헤드를 가능한 낮게 유지하는 것이 매우 중요한다.</br>
→ 소규모 시스템에서는 문제가 되지 않을 수 있지만, 대규모 시스템에서는 병목 현상이 발생할 수 있다.

## JVM Generations
모든 객체가 쓰레기인지 검사하는 방식의 가비지 컬렉션은 규모가 큰 프로그램에서 심각한 문제가 생길 수 있다. </br>
→ 따라서 매번 전체를 검사하지 않고 일부만 검사할 수 있도록 Generational한 구조를 고안해 냈다.</br>
* young generation </br>
객체가 생성되면 이 영역에 위치한다. </br>
이곳이 가득차면 minor gc가 발생한다. </br>
minor gc가 발생하면 살아있는 객체들만 체크하고 나머지는 다 없애버린다. </br>
null객체는 매우 빠르게 수거 된다. → 살아남은 객체들 중 더 오래 쓸 것 같은 일부 객체는 Old Generation(Tenured)으로 이동합니다. </br>
* Old Generation(tenured) </br>
이곳이 가득 차면 major gc가 발생한다. </br>
major gc는 minor gc보다 더 오래 걸린다. </br>
Young Generation는 임계값이 설정되어 있으며, 해당 임계값에 도달하면 오브젝트(객체)는 Old Generation으로 이동한다. </br>
major gc는 모든 라이브러리 객체를 포함하기 때문에 속도가 훨씬 느려진다.major gc를 위한 stop the world event 기간(수행 시간)은 Old Generation에 사용되는 GC종류에 영향을 받는다. </br>
따라서 major gc를 최소화해야 한다. </br>
* Permanet Generation </br>
애플리케이션에서 사용되는 클래스 및 메서드를 설명하는데 필요한 메타데이터가 포함되어 있다. </br>
애플리케이션에서 사용 중인 클래스를 기반으로 런타임에 JVM에 의해 채워진다. Java SE라이브러리 클래스 및 메서드가 여기 저장된다. </br>
perm영역이 현재 meta space로 변경되었다. </br>
* Metaspace </br>
Java8이 나오면서 JVM영역이 변경되었다. </br>
Permanent Generation메모리 영역이 없어지고 Metaspace영역이 생김. </br>

* Stop the World Event </br>
모든 minor gc, major gc는 stop the world 이벤트를 가진다. </br>
GC를 수행하게 되면 GC를 수행하는 스레드를 제외한 모든 스레드가 중지된다 </br>
→ 이것을 stop-the-world라고 한다. </br>

### PermGen vs Metaspace

Java 7 HotSpot JVM
```
<----- Java Heap ----->             <--- Native Memory --->
+------+----+----+-----+-----------+--------+--------------+
| Eden | S0 | S1 | Old | Permanent | C Heap | Thread Stack |
+------+----+----+-----+-----------+--------+--------------+
                        <--------->
                       Permanent Heap
S0: Survivor 0
S1: Survivor 1
```

Java 8
```
<----- Java Heap -----> <--------- Native Memory --------->
+------+----+----+-----+-----------+--------+--------------+
| Eden | S0 | S1 | Old | Metaspace | C Heap | Thread Stack |
+------+----+----+-----+-----------+--------+--------------+
```

* Permanent Generation </br>
 Class혹은 Method Code가 저장되는 영역 </br>
 Heap영역에 속함 </br>
 Default로 제한된 크기를 가짐 </br>
 
| JVM| Default Permgen size(MB) | Default maximum Mataspace size|
|---|---|---|
|32-bit client JVM	|64	|unlimited|
|32-bit server JVM	|64	|unlimited|
|64-bit JVM	|82	|unlimited|

JVM Argument </br>
-XX:permSize=N (PermGen Default size설정)    
-XX:MaxPermSize=N (PermGen Max Size설정)

- Metaspace </br>
java의 ClassLoader가 현재까지 로드한 Class들의 Metadata가 저장되는 공간 </br>
Native메모리 영역(Heap아님!!, 시스템의 기본 메모리) </br>
Default로 제한된 크기를 가지고 있지 않기에 필요한 만큼 계속 늘어난다! </br>
Java8부터는 PermGen관련 JVM옵션 무시 </br>
JVM Argument  </br>
 -XX:MetaspaceSize=N (Metaspace Default size설정)  </br>
 -XX:MaxMetaspaceSize=N (Metaspace Max Size설정)  </br>
> Native Memory
> = Off-Heap, Non-Heap, Direct Memory

- 왜 Perm이 사라지고 Metaspace가 추가됬을까? </br>
Metaspace영역은 JVM에 의해 관리되는 Heap이 아닌 OS레벨에서 관리되는 Native메모리 영역이다. </br>
그러므로 Metaspace가 Native메모리를 이용함으로써 개발자는 영역 확보의 상한을 크게 신경쓸 필요가 없어짐 </br>
    - OOME </br>
Java애플리케이션은 크게 Heap과 Off-Heap 두 공간을 활용하여 동작한다.  </br>   
따라서, 애플리케이션을 배포할 때 메모리 몇GB를 할당해야 하는지 결정하기 위해서 Xmx값만 생각하면 OOME에 빠지기 쉽다. </br>
Xmx에 MaxMetaspace값을 더하고, 추가로 프로그램에서 NIO를 사용해 Native Memory를 직접 할당 받는 로직을 고려해서 Heap+Native Memory사용 총량으로 할당해야 비교적 정확하다. </br>    
특히 컨테이너의 경우 계산을 좀 더 정확하게 해야 시스템에서 OOM Killed되는 상활을 면할 수 있다.  </br>
최근에는 이 Off-Heap을 이용해 성능 향상을 하고 있는 애플리케이션들이 많다. </br>
> Netty, Spark, Cassandra, lgnite 등 이름만 들으면 알만한 여러 애플리케이션들과 이를 사용하는 파생된 수많은 프로젝트가 여기에 포함된다.

> 참고
>> https://m.post.naver.com/viewer/postView.nhn?volumeNo=23726161&memberNo=36733075
>> https://code-space.tistory.com/389


[Up](#part-2-1-Language) / [back](https://github.com/codenee/CS-Study)


</br>

# String Class
```
public final class String extends Object implements Serializable, Comparable<String>, CharSequence
```
String 클래스는 final로 선언되어 있다. </br>
String 클래스는 자식 클래스를 양산할 수 없다.  </br>
모든 클래스는 자식 클래스를 양산할 수 없다.  </br>
- Serializable 인터페이스
  구현해야 하는 메소드가 하나도 없는 특이한 인터페이스
- Comparable 인터페이스
  compareTo()메소드 하나만 선언되어 있다.
- CharSequence 인터페이스
  문자열을 다루기 위한 클래스
  - StringBuilder, StringBuffer 클래스도 CharSequence인터페이스를 구현해 놓았다.
## 1.불변한 객체
String은 immutable한 객체이다. 한 번 만들어지면 그 값을 변경할 수 없다(불변)
```
String str = "Hello";
str += "World"
```
위의 코드로 보면 불변이 아닌 변하는 객체같다. </br>
하지만 아니다. 불변한 객체이다. </br>
String문자열을 더하면 새로운 String객체가 생성되고, 기존 객체는 버려진다. </br>
하나는 String을 만들어 계속 더하기 작업을 하면 계속 쓰레기를 만들게 된다. </br>
쓰레기는 널 객체이고, 널 객체는 GC의 대상이다. </br>
 </br>
이러한 String의 단점을 보완하기 위해서 StringBuffer와 StringBuilder가 나왔다.  </br>
문자열을 더하더라도 새로운 객체를 생성하지 않는다.  </br>
이 클래스 타입은 append() 메소드로 더하기 작업을 한다.  </br>
  </br>
StringBuffer, StringBuilder는 CharSequence인터페이스를 구현했다. </br>
그래서 하나의 클래스를 사용하여 매개 변수로 받는 작업을 할 때는 String, StringBuilder타입보다 `CharSequence`타입으로 받는 것이 좋다.
- StringBuffer
  Thread safe하다. </br>
  클래스에 문자열 처리를 위한 인스턴스 변수가 선언되었고, 여러 쓰레드에서 이 변수를 동시에 접근하는 일이 있을 경우에는 반드시 String Buffer를 사용해야 만 한다.
- StringBuilder
  Thread safe하지 않다. </br>
  하나의 메소드 내에서 문자열을 생성하여 더할 경우에는 StringBuilder를 사용해도 상관없다.

> Thread safe </br> 해당 객체를 사용할 때 다른 스레드에 의해 값이 변경되지 않는 것을 보장하는 상태

## 2. + , concat()
JDK 7,8 버전부터 동작하는 방식이 달라진다. </br>
+ 연산을 하게 되면 StringBuilder로 바꿔주는 역할이 생겼다.</br>
String으로 연산하게 되면 객체를 계속 생성하고 버려지게 되어 GC가 많이 발생하게 된다. </br>
하지만 StringBuilder로 바뀌게 되면서 GC의 영향을 덜 받게 된다.</br>
Git컴파일러가 + 연산이 반복되는 것을 최적화하여 StringBuilder로 바꾼다. </br>

## 3.String literal
String클래스는 다른 클래스들과 다른 특성이 있다. </br>
```
String str1 = new String("heap");
String str2 = "heap";
String str3 = "heap";
```
str1은 new를 이용해 문자열을 생성하면 heap영역의 새로운 주소를 할당된다. </br>
str2는 문자열 리터럴로 생성하는 방식으로 `heap`영역안에 있는 `String Constant Pool`이라는 영역에 할당된다.  </br>
str1과 str2는 같은 값을 가지고 있지만 다른 주소 값을 가진다. </br>
str2와 str3는 같은 값을 가지고 있어, 같은 주소 값을 참조하게 된다. </br>
( 문자열이 담기는 상수풀의 위치는 자바8부터 HEAP영역으로 옮겨졌다. )</br>

str1도 상수풀에 있는 같은 값을 가지는 주소로 참조하게 할 수 있다.   </br>
intern()메소드가 있다. String Constant pool은 해당 문자열이 있는지 검증하고 없으면 상수 풀에 저장한 후 레퍼런스를 전달하고, 값이 있으면 기존 상수풀에 있는 참조 값을 넘겨준다. </br>
하지만 이 메소드는 사용하지 않아야 한다. </br>
Why? </br>
intern()메소드를 계속 사용하게 되면 상수풀 메모리가 꽉 차게 된다. 


## 4. ==, equals()
String클래스도 == 비교가 아닌 equals()메소드를 사용해서 해야만 한다. </br>
 == 은 주소 값을 비교하고, equals()메소드는 저장한 값을 비교한다. </br>
equals()를 제대로 사용하려면 오버라이딩해야 한다. </br>




[Up](#part-2-1-Language) / [back](https://github.com/codenee/CS-Study)


</br>
